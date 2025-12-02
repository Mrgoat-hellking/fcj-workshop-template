---
title: "Blog 2"
date: 2025-01-01
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---
# Optimize Multimodal Search Using the TwelveLabs Embed API and Amazon OpenSearch Service

*by James Le, Gitika Vijh, and Kruthi Jayasimha Rao on 04 APR 2025 in Advanced (300), Amazon OpenSearch Service, Partner Solutions*

The exponential growth of video content has created both opportunities and challenges. Content creators, marketers, and researchers are now faced with the daunting task of efficiently searching, analyzing, and extracting valuable insights from vast video libraries.
Traditional keyword-based search methods often fall short when analyzing visual, audio, or contextual elements within videos—making it difficult for organizations to unlock the full potential of their multimedia assets.
By integrating TwelveLabs’ Embed API with Amazon OpenSearch Service, we can now interact with and derive insights directly from video content. TwelveLabs’ advanced AI-powered video understanding technology, combined with OpenSearch’s vector database and analytics capabilities, enables multimodal video discovery with deep contextual understanding.
This post demonstrates how to integrate the TwelveLabs Embed API with OpenSearch Service to build a multimodal search solution. You’ll learn how to:
* Generate rich, contextual embeddings from video content.


* Store and index these embeddings in OpenSearch.


* Enable search capabilities across text, image, and audio modalities.


By the end, you’ll understand how to implement a system that can transform how your organization handles and extracts value from video content.

---

###  TwelveLabs is an AWS Advanced Partner and AWS Marketplace Seller specializing in video understanding solutions.
 Its Embed API transforms raw video content into meaningful, searchable data using state-of-the-art machine learning models.
Each video is converted into a 1024-dimensional dense vector embedding, representing the core semantic features across multiple modalities—image, text, and audio.


---

## Key Features of TwelveLabs Embed API
* Multimodal understanding – Generates embeddings that capture visual expressions, body language, spoken words, and overall context.

* Temporal coherence – Models the relationships between modalities over time for accurate contextual representation.

* Flexibility – Processes all modalities (video, text, audio) natively without separate models.

* High performance – Uses a video-native approach for superior temporal and contextual coherence.

## Benefits and Use Cases
The Embed API provides several advantages for businesses and developers working with video content:
Enhanced Search Capabilities – Perform multimodal search across video libraries using text, audio, or images.


Content Recommendation – Improve recommendation accuracy through contextual similarity between videos.


Scene Detection and Segmentation – Automatically detect and segment scenes for easier analysis.


Content Moderation – Efficiently identify inappropriate content across large datasets.


**Common use cases include**:
Anomaly detection

Sentiment analysis

Diversity sorting


Smart content recommendations




## Architecture Overview
The architecture integrates TwelveLabs Embed API and Amazon OpenSearch Service to enable advanced multimodal search. It consists of:

* 1. TwelveLabs Embed API – Generates 1024-dimensional vector embeddings from video content, capturing multimodal relationships.

* 2. Amazon OpenSearch Service (Vector Database) – Stores and indexes embeddings for vector-based search.

* 3. AWS Secrets Manager – Stores API keys, OpenSearch credentials, and access secrets securely.

* 4. Integration Components – TwelveLabs SDK and OpenSearch Client for processing videos, generating embeddings, and indexing data.


---

## he Use Case
In the demo, two example videos are used:
* Robin bird forest video by Federico Maderno

* Island video by Bellergy RC

However, this same architecture applies to other use cases such as:
* Searching thousands of hours of archival news footage.

* Automating metadata tagging for complex visual and audio context.

* Performing cross-modal queries (text, image, or audio to video).

* Rapid retrieval of relevant clips for breaking news or highlights.

By integrating TwelveLabs Embed API with OpenSearch Service, organizations can:
* Generate 1024-dimensional embeddings that capture video content, audio cues, and on-screen text.

* Enable text-to-video, image-to-video, and audio-to-video search.

* Reduce retrieval time from hours to seconds.

---



## Solution Walkthrough
**Step 1 – Set Up the TwelveLabs SDK**
Obtain your TwelveLabs API Key.


Store it in AWS Secrets Manager (e.g., under TL_API_KEY).


Use the AWS SDK to retrieve and use it in your Python environment.

---

**Step 2 – Generate Video Embeddings**
Use the Embed API to create multimodal embeddings.
 The model (Marengo-retrieval-2.7) processes video, capturing interrelations between image, text, and audio.
 Embeddings are asynchronous to generate and represent rich, time-aware features.

---
**Step 3 – Configure Amazon OpenSearch**
Install opensearch-py, botocore, and requests-aws4auth.


Authenticate with your OpenSearch domain using stored credentials.


Verify the connection and retrieve cluster information.

---

**Step 4 – Create a Vector Index**
Define an index with a 1024-dimensional knn_vector field for similarity search.
 This enables fast k-nearest neighbor (kNN) queries against video embeddings.

---
**Step 5 – Ingest Embeddings into OpenSearch**
Once embeddings are generated, ingest them into the index using the bulk API.
 Each document stores:
The video title


Segment start and end times


The embedding vector


---
**Step 6 – Perform Vector Search**
Run vector-based search queries to find the most similar embeddings using:
def search_similar_segments(query_vector, k=5):
```yaml
    query = {
        "size": k,
        "query": {
            "knn": {
                "embedding_field": {
                    "vector": query_vector,
                    "k": k
                }
            }
        }
    }
   

```
This function retrieves the top k video segments most similar to a given query vector.

---
**Step 7 – Text-to-Video Search**
Convert a text query (e.g., “Bird eating food”) into a vector embedding using TwelveLabs’ text embedding model, then perform a kNN search in OpenSearch.
Results return:
Video name


Time range


Similarity score

---

**Step 8 – Audio-to-Video Search**
Use TwelveLabs’ audio embedding capabilities to convert an audio clip (e.g., “Rock 808 beat.mp3”) into a vector.
 Perform vector search to retrieve video clips with matching audio characteristics.

---
**Step 9 – Image-to-Video Search**
Use an image (e.g., Ocean Image by shotbyjagar) to generate embeddings and perform image-to-video matching.
 Visually similar scenes are retrieved based on shape, color, and composition features encoded in the embedding.

## Results and Insights
Each search returns a ranked list of relevant video segments, including similarity scores and timestamps.
 Examples:
Text query: “Bird eating food” retrieves segments from the robin-bird.mp4 video.


Image query: An ocean image retrieves high-scoring segments from the island.mp4 video.


Audio query: A rhythmic track retrieves visually synchronized video clips.


This enables cross-modal video retrieval with human-like semantic understanding.

---
## Cleanup
To avoid incurring costs, delete:
The OpenSearch Service domain.


Any S3 buckets, Secrets, and Lambda functions created.

---

## Conclusion
The integration of TwelveLabs Embed API with Amazon OpenSearch Service delivers a powerful, scalable solution for multimodal video search and analysis.
By combining TwelveLabs’ video-native embeddings with OpenSearch’s vector search capabilities, you can perform text-to-video, image-to-video, and audio-to-video searches—unlocking contextual insights that traditional methods can’t match.
This approach empowers developers and organizations to:
Enhance video search and discovery.


Improve user engagement with intelligent content retrieval.


Enable advanced analytics across massive multimedia datasets.


As industries increasingly rely on video for communication, learning, and marketing, multimodal AI search will be a key differentiator in managing and understanding large video archives.
