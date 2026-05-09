
# 🤖 AI-Powered Virtual Tour Guide (RAG Architecture)

A proof-of-concept AI agent utilizing a **Retrieval-Augmented Generation (RAG)** pipeline to provide grounded, hallucination-free answers. While this V1 mock-up is currently configured as a Kuala Lumpur Virtual Tour Guide, the underlying architecture is modular and can be adapted to enterprise use cases like IT helpdesks, legal summarization, or e-commerce assistants.

## 🏗️ Architecture Overview

This project leverages a cloud-native architecture connecting a custom web client to Google Cloud's conversational AI and search infrastructure. 

### Tech Stack
* **Frontend Client:** HTML5, CSS3, Dialogflow Messenger (`df-messenger`)
* **Conversational Agent:** Google Cloud Dialogflow CX (Generative Playbooks)
* **LLM Orchestration:** Vertex AI Agent Builder
* **Data Storage (RAG):** Google Cloud Storage (Buckets)

---

## 🧠 Core System Components

### 1. The Generative Agent (Dialogflow CX)
Unlike traditional rigid, intent-based chatbots, this system utilizes **Generative AI Playbooks**. The agent operates autonomously based on natural language instructions, dynamically determining when to answer a user directly and when to invoke external tools (like searching the knowledge base). It handles conversational state, memory, and routing inference natively.

### 2. Knowledge Grounding & RAG (Cloud Storage Bucket)
To eliminate LLM hallucinations regarding factual data (e.g., operating hours, exact locations), the agent's responses are strictly grounded in an unstructured Data Store.
* **The Bucket:** Raw text files containing verified domain knowledge are uploaded to a secure Google Cloud Storage Bucket.
* **Vertex AI Integration:** Vertex AI Search ingests this bucket, embedding and indexing the unstructured text.
* **Retrieval:** When a user asks a factual question, the agent queries the Data Store, retrieves the exact context, and synthesizes a natural language response based *only* on that retrieved data.

### 3. Frontend Integration
The frontend is a lightweight web client utilizing the `df-messenger` component. To ensure seamless communication between the client browser and the Google Cloud backend, the webhook configuration includes unauthenticated API access for public deployment.

---

## 🚀 Getting Started (Local Development)

If you clone this repository, you must run the HTML file through a local web server. Opening the file directly via the `file:///` protocol will result in strict **CORS (Cross-Origin Resource Sharing) policy errors** from modern web browsers, preventing the widget from communicating with the Dialogflow API.

### Installation & Execution
1. Clone the repository:
   ```bash
   git clone [https://github.com/YOUR-USERNAME/YOUR-REPO-NAME.git](https://github.com/YOUR-USERNAME/YOUR-REPO-NAME.git)
   
```
2. Open the cloned folder in **Visual Studio Code**.
3. Ensure you have the **Live Server** extension (by Ritwick Dey) installed in VS Code.
4. Open the `main.html` file.
5. Click **Go Live** in the bottom right corner of the VS Code window to launch the local development environment and bypass browser CORS restrictions.

---

## 🔮 Phase 2 Roadmap

This repository represents a V1 UI mock-up and architectural proof-of-concept. Future iterations will deprecate the low-code console in favor of a fully custom, code-first backend:

* **Framework Migration:** Rebuilding the orchestration layer using **LangChain** and **LangGraph** for granular multi-agent control.
* **Inference Optimization:** Routing LLM calls through the **Groq API** to achieve ultra-low latency generation.
* **Database Normalization:** Migrating the static text files from the GCS Bucket into a highly structured, relational **SQL database** (optimized to 3NF) for scalable data integrity.
```

```
   
