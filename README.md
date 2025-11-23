# 🛡️ Elderly People Support Based on AI Agents
Author: Eduardo Seiti Ito

Track: Agents for Good

Goal: A multi-agents system for elderly care support.

Course: 5-Day AI Intensive Course with Google/Kaggle

### Introduction

This project demonstrates a robust, hierarchical multi-agents system designed for personalized senior care, built using the Google Agent Development Kit (ADK) and the Gemini 2.5 Flash Lite model. The system integrates advanced techniques in agent autonomy, external knowledge retrieval (RAG via SQLite), and complex tool-chaining to create a reliable safety and support network.

### 🤔 The Problem

Many elderly individuals wish to live independently but face significant challenges in managing the complex logistics of modern life. This includes remembering medications, scheduling doctor appointments, coordinating proper nutrition, and combating social isolation. Furthermore, a reactive system isn't enough; families need peace of mind that proactive monitoring is in place to handle unexpected health events, which are often full of uncertainty.

### ✅ The Solution: The Guardian Agent System

Herein is proposed the "Guardian Agent System", a proactive, multi-agents AI assistant. The system operates in two parts:

- ✨ **Conversational Assistant** - A friendly "Guardian" orchestrator agent that understands a senior's natural language requests (e.g., "I'm hungry," "When is my doctor's visit?") and delegates tasks to a team of specialists (HealthMinder, NutritionPal, JoyConnect).

- ✨ **Proactive Monitor** - A "ProactiveHealth" loop agent that runs 24/7, simulating sensor data (like blood pressure). When it detects an anomaly, it uses a RAG-based tool to semantically query a health protocol database, understand the uncertainty, and decide on the safest course of action—from a simple "drink water" alert to "call family."

This project intends to demonstrate a robust, personalized system that moves beyond simple task-completion to provide a true safety and support net.

### 🏗️ Agent System Architecture 

The architecture employs a Hierarchical Delegation Pattern, ensuring reliability by separating the user interface from the specialized execution units and the autonomous monitoring loop.

1. Multi-Agents Components

| Agent | Primary Role | Execution Model | Operational Mode |
| :--- | :--- | :--- | :--- |
| Guardian Orchestrator | Conversational Router. Interprets intent, handles complex reasoning, and delegates multi-step requests. | Gemini 2.5 Flash Lite | Reactive (User Input) |
| Proactive Agent | Autonomous Safety Monitor. Runs the scheduled vital-check loop. | Gemini 2.5 Flash Lite | Autonomous (System Trigger) |
| Specialist Agents | Tool Executor. Executes domain-specific tasks (Health, Nutrition, Joy) using simple tools. | Gemini 2.5 Flash Lite | Programmatic |

2. Autonomous Loop and RAG Implementation
The system's most critical feature is its reliance on RAG (Retrieval-Augmented Generation) combined with the Model-Controller-Program (MCP) pattern for autonomous safety:

* **RAG Source**: SQLite Database (health_protocols.db) stores granular clinical protocol text (Mild, Urgent, Crisis actions). This prevents configuration drift and ensures a single source of truth.
* **Retrieval**: The search_health_protocols tool executes a SQL query against the database based on sensor data (vitals).
* **MCP Flow**: The Proactive Agent executes the loop: Sensor Data $\rightarrow$ RAG Tool Call $\rightarrow$ LLM Reasoning $\rightarrow$ Final Action (call_family_contact).

### 🚀 Key Technical Features

* **Verified RAG**: Demonstrates integration of a persistent, external knowledge layer (SQLite) into the agent's decision-making process.
* **Tool Chaining**: The Guardian successfully executes multiple sequential steps in a single user query (e.g., checking the calendar THEN booking an appointment).
* **Personalization**: The USER_PROFILE is actively used by all agents to tailor responses based on preferences (e.g., low-sodium diet, music genre).

### ✅ Evaluation Summary
The system was verified against a comprehensive test set, validating all core Capstone concepts:
| Scenario | Core Agent Action | Project Value Demonstrated |
| :--- | :--- | :--- | 
| Safety Protocol | Health Agent enforces Crisis Protocol based on SQLite RAG retrieval. | Critical Safety & Reliability |
| Proactive Autonomy | Proactive Agent executes the full MCP Loop autonomously upon a system trigger. | Autonomy & Efficiency |
| Tool Chaining | Guardian successfully executes sequential scheduling and booking. | Complex Reasoning & Planning |
| Personalization | Nutrition/Joy Agents use USER_PROFILE data for specialized tool-calls. | Specialization & Empathy |

4. Multi-Agents System architecture
   
The Multi-Agents System architecture is displayed below:

https://github.com/edbkei/KaggleCapstoneProject/blob/main/image_projectv_final.jpg

And, the following concepts are introduced.

1. **Multi-Agents System**: The architecture cleanly separates concerns between a Guardian orchestrator (for user-facing tasks) and a ProactiveHealth agent (for background monitoring), which talk to specialists.

2. **Tools**: The system uses a wide array of the following tools: set_medication_reminder, check_sensor_data, send_user_alert.

   **Custom tools**: set_medication_reminder, check_sensor_data, send_user_alert.

   **OpenAPI-style**: Calendar mock (for production is recommended: Google Calendar).

   **RAG Tool**: The search_health_protocols tool is a perfect example of providing context for an LLM to "semantically search" and reason over.

3. **Loop Agents (and MCP)**: The ProactiveHealth agent is a loop agent that runs 24/7. It uses the Model-Controller-Program pattern to handle complex, uncertain health data, moving from sensor reading -> to protocol retrieval -> to reasoned action.

### 🎯 Project Value Proposition
The Multi-Agents System moves beyond simple reactive assistance to provide a true safety net for independent elderly living. It reduces cognitive load, automates complex logistics (scheduling, medication adherence), and provides verifiable safety actions based on clinical protocols.

### 🛠️ Technology Stack
| Component | Function | Status |
| :--- | :--- | :--- |
| **Framework** | Google ADK (Agent Development Kit) | Core Architecture |
| **LLM** | Gemini 2.5 Flash Lite for {Orchestrator} and {Specialists} | Reasoning Engine |
| **Architecture** | Hierarchical Delegation (Orchestrator -> Sub-Agents) | Final Design |
| **Execution Pattern** | Local Sub-Agents (In-Process) | Stable Solution |

### ⚙️ Getting Started (How to Run)

The Project is designed to run sequentially with a Kaggle or Colab Notebook environment.

**installation**

**# Required environment setup**

pip install -q google-adk[a2a]

pip install -q nest-asyncio

**execution**

Run all notebook cells from top to bottom. The final cell executes the full set of conversational and proactive scenarios, creating the necessary SQLite database and validating the complete system output.



