# langgraph-agentic-sidekick
Agentic AI with LangGraph SideKick
# LangGraph Agentic Sidekick

An experimental **autonomous AI assistant** built with [LangGraph](https://github.com/langchain-ai/langgraph) and [LangChain](https://www.langchain.com/).  
This project demonstrates **multi-node agent orchestration**, **tool integration**, and **structured success evaluation** for building intelligent, production-ready AI operators.


## ✨ Key Features
- **Multi-node orchestration** using LangGraph’s state machine approach
- **Structured evaluation** to check if an AI response meets user-defined success criteria
- **Tool orchestration**: Web scraping, search, file operations, notifications, and code execution
- **Persistent state management** for long-running tasks
- **Configurable environment** via `.env`
---

## 🖼️ System Architecture

<img width="1430" height="956" alt="sidekick_architecture_pro" src="https://github.com/user-attachments/assets/ae5ebd1c-76be-4810-ae44-222e4967484f" />


### **How It Works**
The architecture is divided into **five key layers**:

1. **Presentation Layer**
   - **Gradio UI (`app.py`)**  
     Handles the chat interface where the user inputs:
     - **Message**
     - **Success criteria**
     - **Conversation history**  
     Passes these to the orchestration engine and displays the AI's response alongside evaluator feedback.

2. **Orchestration Layer**
   - **Sidekick Orchestrator (`side_kick.py`)**  
     Acts as the central coordinator between:
     - The LangGraph execution graph
     - The tools and integrations
     - The evaluator
   - **LangGraph Checkpointer (MemorySaver)**  
     Supports **state persistence** so agents can **resume mid-task** after interruptions.

3. **LangGraph StateGraph (Core Execution)**
   - **Worker Node**  
     The LLM bound to available tools. Generates **answer candidates**.
   - **Evaluator Node**  
     Performs **structured success checks** against the success criteria.
   - **Tool Node**  
     Executes tool calls and returns results to the worker node.

4. **Tools & Integrations**
   - **Python REPL** – Safe Python code execution (dev mode)
   - **Pushover API** – Push notifications
   - **Playwright** – Headless Chromium automation
   - **Google Serper** – Search queries
   - **Wikipedia API** – Knowledge lookups
   - **File Toolkit** – Sandboxed file operations

5. **Model Layer**
   - **ChatOpenAI (gpt-4o-mini)** for:
     - Evaluator Node (gpt-5-nano)
     - Worker Node 

6. **Config & Observability**
   - `.env` for API keys and feature toggles
   - Logs & metrics for:
     - Tool call timings
     - Step execution performance

---



