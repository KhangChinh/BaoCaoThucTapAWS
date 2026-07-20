---
title: "Workshop"
date: 2026-07-17
weight: 5
chapter: true
pre: " <b> 5. </b> "
---

# Uchimi StudyGamification - Learning Application Combining AI and Gamification


Welcome to the technical documentation of the **Uchimi StudyGamification** project. Built with a **ReactJS + Electron** architecture on the Client side and **AWS Serverless** on the Server side, the project aims to optimize operational costs while delivering an exceptional learning experience, transforming self-study from a forced obligation into an engaging journey.

## Overview

In the rapidly advancing digital era, the greatest challenge of self-study is no longer accessing knowledge. The true difficulty lies in **maintaining long-term focus and discipline** to prevent learning interruptions. Learners are easily distracted by countless temptations when using computers, making it extremely difficult to form a sustainable learning habit.

**Uchimi StudyGamification** was created to comprehensively solve this problem. The core objective of the project is to turn the act of "turning on the computer to study every day" into a natural, sustainable, and exciting habit.

The system provides a holistic solution, representing the perfect intersection between **strict discipline** and **healthy entertainment**:
*   **Disciplined Learning with AI:** Utilizing AI Scan technology to track and immediately block distracting behaviors while users operate their computers, helping to maintain intense focus.
*   **Entertainment Ecosystem (Minigames):** After intense study sessions, users can enter a relaxing space with engaging minigames. This combination turns academic pressure into well-deserved rewards, effectively regenerating energy.

By applying the **Discipline → Action → Feedback → Reward** loop, the project not only retains users but also gradually builds a completely new learning lifestyle.

## Architecture Index

This document will delve into analyzing and providing detailed guidance on the technical aspects of the project, including:

1. **[Project Context](5.1-Overview/)**
   * Analysis of the background, core objectives, and target audience.
   * Details of the technical problems that need to be solved to meet practical needs.
2. **[Project Architecture](5.2-Architecture/)**
   * Reasons for choosing the AWS Serverless architecture and identifying technical barriers.
   * How to set up authorization, security barriers, and integrate third-party services.
   * Details of the AWS services used, implementation strategies, and the overall Architecture Diagram [drawio].
3. **[Learning with AI](5.3-Study_with_AI/)**
   * Detailed description of the AI assistant's workflow and AI Scan technology.
   * How AI processes data, the benefits of the models/extensions used, and why this method is highly effective.
   * Setup instructions for each type of AI, learning modes, and the quest system.
4. **[Gamification Ecosystem](5.4-Gamification/)**
   * Analysis of the seamless transition flow from the Learning module to Minigames.
   * General description of the minigames' operational mechanics and core functions.
   * The Leaderboard system to increase competitiveness and user retention.
5. **[Deployment and Operations](5.5-Deployment/)**
   * Detailed instructions on the deployment process (packaging the build, downloading, and installing).
   * Description of the actual workflow and how users interact with the system.
6. **[Future Directions](5.6-Direction/)**
   * Acknowledging and evaluating current limitations that need improvement.
   * Development roadmap and upcoming features planned for future integration.

---

## Source Code

- **Frontend (ReactJS + Electron):** https://github.com/KhangChinh/AWSStudy-Play
- **Backend (AWS Serverless):** https://github.com/KhangChinh/AWSServerless