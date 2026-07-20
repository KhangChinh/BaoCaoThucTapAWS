---
title: "Proposal"
date: 2026-07-20
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# Uchimi StudyGamification
## Learning Application Combining AI and Gamification

### 1. Project Overview
**Uchimi StudyGamification** is a desktop learning application (Desktop App) that combines AI technology with a Gamification ecosystem. The project is designed to transform the act of "turning on the computer to study every day" into a natural, voluntary, and sustainable habit. By applying the behavioral loop: **Discipline → Action → Feedback → Reward**, the system helps learners maintain high concentration while enjoying healthy entertainment after stressful study hours.

### 2. Problem Statement
The current self-study process faces significant psychological and motivational barriers:
* **Lack of immediate feedback:** Learning outcomes appear slowly, whereas social networks or games provide instant dopamine feedback, making learners easily distracted and prone to giving up.
* **Dry traditional tools:** Current learning software primarily focuses on task management and fails to solve the problem of maintaining long-term motivation.
* **Superficial gamification:** If focusing solely on pure entertainment rewards, users easily get caught up in games, neglecting actual learning outcomes.
* **Digital cheating:** Desktop applications are easily manipulated (editing study time, hacking minigame scores, duplicating items), destroying the fairness of the environment.

### 3. Project Objectives
The project aims to build a learning ecosystem that balances **strict discipline** and **healthy entertainment**:
* **Breaking down macro goals:** Divide long-term learning roadmaps into manageable focus sessions (Focus mode) and daily quests.
* **Visualizing progress:** Provide timely feedback through a scoring system (Knowledge Points), learning streaks, pet items, and leaderboards.
* **AI application for personalization:** Assist in generating learning roadmaps, creating quizzes from documents, and monitoring distractions via AI Scan technology.
* **Ensuring fairness and transparency:** Build an anti-cheat backend system to protect the integrity of currency, item, and ranking data.

### 4. Solution Architecture
The project utilizes a **distributed Client-Server** model, combining the convenience of a Desktop App with the flexible scalability of the Cloud.

*   **Client (Frontend - Offline First):** Built with ReactJS and packaged with Electron into a standalone Desktop App. State management is handled by Redux and Electron-store.
*   **AI & Tracking:** Utilizes a Browser Extension (AIGuard) communicating via WebSocket with the Desktop App. Integrates Google Gemini (Cloud AI) or Ollama (Local AI) for learning support features.
*   **Backend (AWS Serverless):** All Business Logic (Gacha, Shop, Quest, Social) is processed via AWS Lambda and API Gateway in the `ap-southeast-1` region. 
*   **Storage & Data:** Amazon DynamoDB stores system data (using `TransactWriteItems` to ensure integrity). Amazon S3 stores static resources (assets, avatars) with CloudFront acting as the CDN.
*   **Ancillary Services:** Amazon Cognito (Authentication/JWT), EventBridge (Cronjobs for leaderboards/shops), DynamoDB Streams, and Algolia (User Search).

### 5. Implementation Roadmap (Timeline)
*   **Phase 1 (Infrastructure Setup):** Initialize AWS resources (Cognito, DynamoDB, S3), configure API Gateway, and deploy the basic Lambda framework using the Serverless Framework.
*   **Phase 2 (Client Development):** Build the ReactJS/Electron interface, integrate Focus Mode, the Daily Quest system, and the Offline-first caching mechanism.
*   **Phase 3 (AI Integration):** Develop the AIGuard Extension, set up WebSockets, and connect the Gemini API/Ollama to generate learning roadmaps and quizzes.
*   **Phase 4 (Gamification Ecosystem):** Finalize the logic for Minigames, Gacha, Shop, and Leaderboards on the Cloud. Apply Anti-cheat mechanisms.
*   **Phase 5 (Packaging & Operations):** Build the `.exe` file using `electron-builder` and distribute it via Google Drive. Conduct end-to-end testing and monitoring via CloudWatch.

### 6. Budget and Cost Optimization
The architecture is designed around a **cloud cost-optimization** mindset:
*   **Scale-to-Zero:** Using AWS Lambda and API Gateway means the system incurs virtually no fixed server costs when there is no user traffic.
*   **Flexible AI Options:** Users can configure their own API Key (Gemini) or run a Local LLM (Ollama) for free, relieving the platform of centralized LLM costs.
*   **Database Operation Optimization:** Apply internal caching on the Client and a batch synchronization mechanism (`POST /sync-all`) to reduce the number of API calls and read/write operations on DynamoDB.

### 7. Risk Assessment and Mitigation

| Risk Type | Issue Description | Mitigation Strategy |
| :--- | :--- | :--- |
| **System Latency** | AWS Lambda Cold Starts slowing down the initial request. | Maintain Lambda RAM configuration at an optimal level (512MB) to balance speed and cost. |
| **Data Integrity** | Client caching can easily cause data conflicts or user-side cheating. | The backend always acts as the Server Authority; use `TransactWriteItems` for critical transactions. |
| **Resource Consumption** | Electron and Local AI can consume a significant amount of computer RAM. | Optimize Vite Build (tree-shaking) and allow users the flexibility to choose between Cloud AI and Local AI. |
| **Vendor Lock-in** | Deep dependency on the AWS ecosystem (Cognito, DynamoDB, Streams). | Encapsulate business logic into independent Lambda modules and standardize connection protocols. |