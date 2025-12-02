---
title: "Blog 3"
date: 2025-01-01
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---


# Optimizing Network Footprint in Serverless Applications
*by Chris McPeek on 21 MAR 2025 in Amazon API Gateway, Amazon Elastic Kubernetes Service, Amazon EventBridge, Amazon Simple Queue Service (SQS), Amazon Simple Storage Service (S3), AWS Lambda, Serverless*

*Authored by Anton Aleksandrov, Principal Solutions Architect, AWS Serverless and Daniel Abib, Senior Specialist Solutions Architect, AWS.*


Serverless application developers frequently encounter scenarios where they must transport large payloads, particularly in modern cloud applications that require rich data. Examples include analytics platforms generating detailed reports, e-commerce systems managing large product catalogs, healthcare applications transmitting patient records, or financial services aggregating extensive transactional data.
However, many serverless services have strict payload size limits — for example:
AWS Lambda: 6 MB per request/response


Amazon SQS and Amazon EventBridge: 256 KB per message


This post explains how to use data compression techniques to reduce network footprint and transport larger payloads within existing constraints.


---

## Overview
As cloud applications evolve to meet new features and Service Level Objectives (SLOs), payload sizes often grow. Eventually, you may hit service-imposed limits such as:
Lambda synchronous invoke: 6 MB


API Gateway: 10 MB


SQS/EventBridge: 256 KB


If payloads reach tens of MBs or include large binary objects, you can store data on Amazon S3 and use pre-signed URLs for direct upload/download.

Figure 1 – Sample architecture for handling large payloads.
When handling large messages via SQS or EventBridge, you can store message content in S3 and send only a reference. The consumer then retrieves the full message directly from S3.
However, while these techniques work, they introduce architectural complexity and require modifying existing workflows.
Additionally, as payload sizes increase, data transfer costs rise—especially through NAT Gateways, VPC Endpoints, or cross-Region transfers. For example, Lambda functions inside a VPC may invoke public endpoints or external services.

Figure 2 – Examples of using virtual network appliances with serverless applications.
Both NAT Gateway and VPC Endpoint are billed per GB of data processed, making data compression a valuable optimization technique.

---
**What Is Data Compression?
Data compression reduces data size to improve performance and cost-efficiency for storage and transmission. Tools such as gzip and zstd are widely used, standardized under IANA and IETF RFC 9110.
Modern browsers (Chrome, Firefox), HTTP tools (curl, Postman), and runtimes (Node.js, Python) support compression natively.
When clients send compressed data, they specify it using the Content-Type header. To receive compressed responses, clients specify supported compression methods in the Accept-Encoding request header.

Figure 3 – Accept-Encoding request header specifying supported compression methods.
The server then compresses responses using a supported method and includes a Content-Encoding header to indicate the compression type.

Figure 4 – Content-Encoding response header specifying compression method.
This reduces bytes transmitted over the network, improving latency. Text-based formats like JSON, XML, HTML, and YAML compress well, whereas binary files (PDF, JPEG) compress less effectively.


---

## Data Compression with API Gateway
Amazon API Gateway offers built-in compression via the minimumCompressionSize configuration, which automatically compresses responses above a certain size (0 bytes–10 MB).

Figure 5 – Handling data compression in API Gateway.
How It Works
API Gateway automatically decompresses incoming requests and compresses outgoing responses.


Compression is bi-directional and works seamlessly with JSON payloads.


Clients specify compression in the Content-Encoding header; API Gateway decompresses before forwarding to integrations.


API Gateway compresses integration responses when clients include a matching Accept-Encoding header.


Test results:
Compression disabled: Response size = 1 MB, latency = 660 ms


Compression enabled: Response size = 220 KB, latency = 550 ms


→ 78% network footprint reduction and 110 ms faster response.
To preserve compression end-to-end (so Lambda can handle decompression), configure binaryMediaTypes to allow binary passthrough.

---

## Handling Compressed Data in AWS Lambda
AWS Lambda Invoke API supports text-based payloads (e.g., JSON) up to 6 MB (sync) or 256 KB (async).
 You can, however, compress payloads within Lambda code to overcome limits and reduce transfer costs.

Figure 7 – Transporting compressed payloads in serverless applications.
The code below shows how to compress response payloads in Node.js using the built-in zlib module:

Figure 8 – Sample code implementing response payload compression in a Lambda function.
Key details:
Line 1 imports gzip from the zlib module.


Lines 11 compress and Base64-encode data (since Lambda expects text-based output).


Lines 13–21 create the response object with isBase64Encoded=true and proper headers.


Result:
 A 20 MB uncompressed JSON returns as a 2.5 MB compressed payload — 80% network footprint reduction.

Figure 9 – Screenshot from Postman showing original vs. compressed payload size.
This method allows transferring payloads several times larger than Lambda’s default limits

---

## Using Function URLs with Compressed Payloads
Transporting compressed payloads via Lambda Function URLs requires no extra configuration.
 The handler simply compresses and Base64-encodes the response.
 Incoming requests marked as binary are automatically passed to your function as Base64 strings.

Figure 10 – Sample code implementing request payload decompression in a Lambda function.

Trade-Offs and Testing Results
Compression is CPU-intensive, increasing invocation duration and potentially cost. However, it reduces data transfer and latency—often yielding net savings.
Tests using Node.js on ARM architecture with random JSON payloads showed:
Compressing a 1 MB JSON object added ~124 ms compute time for 1 GB memory.


10 million invocations → +$16 compute cost.


But 70% payload size reduction saved ~$300 (NAT Gateway) or ~$70 (VPC Endpoint).


Savings depend on payload type and compression ratio. For low-compressibility data, results may vary.

---
## Sample Application
You can test this in your own AWS account using the sample project in the provided GitHub repository.
 The sample provisions two Lambda functions to demonstrate gzip compression for GET and POST operations via Function URLs and API Gateway.
Results show >80% reduction in network footprint using JSON payloads.

Figure 11 – Screenshot from Postman showing the original and compressed payload size.

---
## Conclusion
Data compression allows larger payload transfers and significantly reduces network footprint. It improves latency and helps control transfer costs, especially for data flowing through NAT Gateways or VPC Endpoints.
However, compression adds CPU overhead — you should balance the compute cost against the network savings.
Compression is most effective for large text-based payloads, where small increases in compute time are offset by faster, cheaper data transfer.
By applying these techniques in AWS Lambda and API Gateway, you can make your serverless applications more efficient, scalable, and cost-optimized.


