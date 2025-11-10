---
title: "Proposal"
date: 2025-10-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---



# Online Shopping Website: Furious Five Fashion (FFF)
## E-commerce Website Solution with AWS and AI

### 1. Executive Summary
Furious Five Fashion (FFF) is an e-commerce platform focusing on the fashion sector, aiming to deliver the best online shopping experience for customers in Vietnam. The solution leverages AWS serverless services and AI technology to build a low-cost, scalable, secure online sales system that personalizes the shopping journey.

The website will provide product management, shopping cart, payment, order management, and customer support via an AI chatbot.

### 2. Problem Statement
### What’s the Problem?
Many clothing websites in Vietnam face problems such as slow loading speed, poor scalability, high operating costs, lack of personalization in the shopping experience, and no AI tools to assist customers.

### The Solution
The platform uses AWS IoT Core to receive MQTT data, AWS Lambda and API Gateway for processing, Amazon S3 for storage (including a data lake), and AWS Glue Crawlers with ETL tasks to extract, transform, and load data from the S3 data lake into another S3 bucket for analysis. AWS Amplify with Next.js provides the web interface, and Amazon Cognito ensures secure access. Similar to Thingsboard and CoreIoT, users can register new devices and manage connections, but this platform operates on a smaller scale and for internal use. Key features include a real-time dashboard, trend analysis, and low operating costs.

### Benefits and Return on Investment
- Reduce infrastructure costs by using AWS serverless.

- Optimize revenue with AI-driven product recommendations.

- Easily scale from MVP to production.

- Expected ROI within 6–12 months through increased online sales and reduced operating costs.

### 3. Solution Architecture
The e-commerce system is built on an AWS serverless architecture, leveraging cloud services to minimize operational costs and ensure scalability. The user interface is deployed with a modern frontend, while the backend is handled flexibly through API Gateway and Lambda. Data is securely managed with DynamoDB and S3. Security layers, authentication, and an AI chatbot are integrated to enhance customer experience and ensure system safety.

![E-commerce Website Solution ](/images/2-Proposal/proposal.jpg)


### AWS Services Used
- **AWS Amplify**: Deploy and host frontend website (React/Next.js).

- **Amazon API Gateway + AWS Lambda**: Backend API handling for cart, orders, products.

- **Amazon DynamoDB**: Store product and order data (NoSQL, serverless).

- **Amazon S3**: Store product images and static assets.

- **Amazon Cognito**: Manage users (customers, admin).

- **Amazon CloudFront**: CDN for faster website and image loading.

- **Amazon SES (Simple Email Service)**: Send order confirmations and promotional emails

### Component Design
- **Frontend**: Next.js website deployed via AWS Amplify.

- **Backend**: API Gateway + Lambda handling business logic (CRUD for products, cart, orders).

- **Database**: DynamoDB (products, users, orders).

- **AI Layer**: Amazon Lex/Bedrock chatbot, personalized product recommendations based on shopping data.

- **User Management**: Cognito (login/registration, role-based access for customers and admin).

### 4. Technical Implementation
**Implementation Phases**
1. Architecture Design & Research (Month 1): Build AWS serverless architecture and design database.

2. MVP Development (Month 2): Develop frontend (Next.js), backend (Lambda), integrate DynamoDB and Cognito.

3. AI Integration & Cost Optimization (Month 3): Connect AI chatbot, personalize shopping experience.

4. Testing & Production Deployment (Month 4): System testing, performance optimization, official launch.

**Technical Requirements**
- Frontend: Next.js + Tailwind CSS.

- Backend: Node.js (Lambda functions).

- Database: DynamoDB.

- CI/CD Deployment: AWS Amplify + GitHub Actions.

### 5. Timeline & Milestones
**Project Timeline**
- Pre-Internship (Month 0): 1 month for planning and old station review.
- Internship (Months 1-3): 3 months.
    - Month 1: Study AWS and upgrade hardware.
    - Month 2: Design database, research AWS services, build MVP.
    - Month 3: Integrate AI chatbot, optimize infrastructure cost, deploy, test, and launch.
- Post-Launch: Up to 1 year for research.

### 6. Budget Estimation

### Infrastructure Cost
- AWS Services:
   - AWS Amplify: ~9 USD
   - API Gateway + Lambda: ~5 USD
   - DynamoDB: ~10 USD
   -  S3 + CloudFront: ~4 USD
   - Cognito: ~1 USD
   - AI Chatbot (Lex/Bedrock): ~10 USD
   - SES Email: ~1 USD
   - Contingency cost incurred: 70 USD/the first month
Total: ~45 USD/month (~300 USD/year).


### 7. Risk Assessment
#### Risk Matrix
- Performance bottlenecks during traffic spikes: High impact, medium likelihood.

- Exceeding AWS budget due to storage/infrastructure growth: Medium impact, medium likelihood.

- AI chatbot providing incorrect or unsuitable responses: Medium impact, high likelihood.
#### Mitigation Strategies
- Use CloudFront CDN and serverless auto-scaling.

- Set AWS budget alerts.

- Test and train AI chatbot with fashion-specific data.
#### Contingency Plans
- If AWS experiences downtime: switch to S3 backup and temporarily process orders manually.

- If AI chatbot is ineffective: fallback to live chat with customer service staff.
### 8. Expected Outcomes
#### Technical Improvements: 
Technical Improvements: Build a high-speed, low-cost, scalable e-commerce website.
Customer Experience: Integrate AI chatbot and personalized product recommendations.
Long-term Value: Easily expand into mobile apps, integrate marketing automation, and customer data analytics.
#### Conclusion

Furious Five Fashion (FFF) will become an intelligent e-commerce platform that optimizes costs and applies AI to enhance customer experience, while remaining suitable for deployment by a small team.