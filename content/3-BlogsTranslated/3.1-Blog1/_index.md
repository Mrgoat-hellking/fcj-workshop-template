---
title: "Blog 1"
date: 2025-01-01
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---


# Nomalab Automates Ad Break Detection in Media Workflows with AWS


*by Thomas Buatois, Iryna Oliinykova, and Ken Shek on 04 APR 2025 in Amazon Bedrock, Amazon Machine Learning, Amazon OpenSearch Service, Amazon Rekognition, Amazon Transcribe, Analytics, Artificial Intelligence, AWS Elemental MediaConvert, Data Science & Analytics for Media, Generative AI, Media & Entertainment, Media Services, Media Supply Chain & Archive, Monetization*

**The Media and Entertainment (M&E)** industry is undergoing an unprecedented transformation, with the volume and complexity of content continuing to grow at a rapid pace.
 To stay competitive, broadcasters and publishers must find innovative solutions to optimize their media workflows from ingest to delivery.
Recognizing this challenge, Nomalab, a leading cloud-based media management platform available on the AWS Marketplace, has leveraged the power of AI and Generative AI through the Guidance for Media2Cloud on AWS (Media2Cloud).
Media2Cloud is an open-source, serverless framework that exemplifies how embracing the latest cloud and AI technologies can drive efficiency and position media organizations for long-term success.
This post explores how Nomalab’s innovative use of AWS services and generative AI is transforming media workflows and setting a new standard for content processing efficiency.

---

## Nomalab Use Case


Nomalab’s customers—including major media groups—face increasing demand to deliver more content to linear TV and OTT platforms than ever before. Automation has become essential for maintaining a competitive edge in viewer experience and operational efficiency.
A key pain point in the content delivery pipeline is the generation of segmentation metadata for long-form content, particularly identifying title sequences, end credits, and ad insertion points that respect narrative flow.
The goal was to create a system that accurately generates metadata without human intervention, dramatically accelerating content preparation and reducing costs.
“Our clients need to be able to insert ads seamlessly into their programming, but manually reviewing hours of footage to identify suitable ad breaks is extremely time-consuming,”
 explains Romane Lafon, Digital Media CTO at Nomalab.
 “We knew AI could be the answer, but we wanted a solution that was highly accurate and cost-effective to run at scale.”
To meet stringent quality standards, Nomalab targeted over 90% accuracy in identifying segmentation points—matching or exceeding human-level performance. This gave clients the confidence to fully adopt automated workflows.

---

## Integrating Media2Cloud and Generative AI

When faced with automating ad break detection, Nomalab turned to Media2Cloud. The framework not only simplifies the migration of video assets and metadata to AWS but also unlocks deeper content insights by leveraging AI-powered metadata extraction.
“By integrating Media2Cloud and advanced AI capabilities, we’ve been able to develop a uniquely powerful solution that automates key tasks and delivers measurable results for our clients,” says Lafon.

---

## How It Works
Media2Cloud uses a combination of traditional AI/ML and generative AI to detect natural content breaks—known as chapter points—where visual and narrative contexts shift.
**Step 1: Visual Shot Detection**
The process starts with the Amazon Rekognition Segment API, which provides frame-accurate camera shot detection and technical cue identification (e.g., color bars, black frames, end credits).


---

## Step 2: Grouping Shots into Scenes
Detected shots are regrouped into logical scenes using the Amazon Titan Multimodal Embedding model via Amazon Bedrock.
 Frames are converted into vector embeddings capturing semantic meaning, stored in Amazon OpenSearch Service using K-NN indexing to cluster similar frames together.

---

## Step 3: Analyzing Conversation Flow
Next, Amazon Transcribe converts speech to text with timestamps, and Amazon Bedrock analyzes conversation flow to identify topic transitions, helping create natural chapter breaks aligned with visual cues.


---

## Step 4: Aligning Audio and Visual Cues
By aligning detected scenes with dialogue transitions, the workflow identifies natural, unobtrusive ad break opportunities—points where commercial interruptions are least disruptive to the viewer experience.

---

## Placing Ad Breaks
Building on this foundation, Media2Cloud’s ad break detection feature pinpoints frame-accurate opportunities for ad placement while generating contextual metadata using IAB Content Taxonomy V3 and GARM Taxonomy.

This contextual layer enables ad decision servers to make intelligent placement choices based on the surrounding content.


---

## Integration
Nomalab extends Media2Cloud with a proprietary post-evaluation phase that mirrors human decision-making.
 Custom business rules refine and prioritize ad break opportunities, ensuring only the most relevant and strategic breaks are selected.
This transforms raw detection data into production-grade insights, delivering optimal ad placement while maintaining the integrity of the viewing experience.

Figure 6 – Nomalab’s analysis workflow integrating AWS services and proprietary post-evaluation logic.
“The integration with Media2Cloud was critical,” says Lafon.
 “It provided a scalable, cloud-native foundation so we could focus on AI-powered features that deliver real value.
 The generative AI capabilities of Amazon Bedrock were a game-changer—combining computer vision, speech-to-text, natural language understanding, and business rules to reach near-human accuracy.”


## Benefits and Results
By automating ad break detection, Nomalab has drastically improved workflow efficiency.
 A manual operator could handle about 25 programs per day; now, with AWS automation, entire libraries can be analyzed in hours—at scale and with consistent accuracy.
“Our overall target is a 90 percent or higher accuracy rate, and we are nearly there or higher depending on content type,” says Lafon.
 “The best part is, our clients don’t have to worry about the complexity—they simply receive fully enriched media assets ready for ingest and distribution.”
Scalability is another key benefit:
“We handle tens of thousands of content pieces per year while keeping costs under control,” adds Lafon. “It’s a win-win for us and our clients.”

## Looking to the Future
As the media industry evolves, Nomalab’s workflow highlights how AWS and generative AI are transforming media operations.
“This is just the beginning,” Lafon says.
 “We’re already exploring automation for content classification, metadata enrichment, and even media quality control. The potential is limitless.”
By combining Amazon Bedrock, Amazon Rekognition, and Amazon Transcribe, Nomalab demonstrates the power of uniting AI and cloud technologies to achieve human-level accuracy in automated workflows.
This synergy between foundational AI/ML services and generative AI unlocks new insights from media assets—setting a new benchmark for automation in the media industry.
Looking ahead, as cloud-based AI continues to evolve, these technologies will drive increasingly intelligent, automated content-processing pipelines—becoming a key differentiator for competitive media organizations.
For media companies seeking to future-proof operations, Nomalab’s success on AWS demonstrates what’s possible by embracing the latest innovations in AI, cloud computing, and generative AI—transforming media workflows for the digital era.
