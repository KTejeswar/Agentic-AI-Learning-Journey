# Agentic-AI-Learning-Journey

Welcome to the **Agentic AI Study**. This repository is a learning space dedicated to mastering the building blocks of Agentic AI using **LangChain**. It covers agent creation, multi-provider model integration, tool calling, manual tool-execution loops, and message state management.


---

## 📓 Notebook Walkthroughs

### [1. LangChain Agent Intro]
* **Objective:** Introduce the fundamentals of agent creation using LangChain.
* **Topics Covered:**
  * Initializing basic configurations with `dotenv`.
  * Using the LangChain `create_agent` factory function.
  * Setting up system prompts and binding empty tool lists.

### [2. Models Integration]
* **Objective:** Dynamically interface with different LLM providers through a unified API.
* **Topics Covered:**
  * Setting up keys for **OpenAI** (`ChatOpenAI`), **Google Gemini** (`ChatGoogleGenAI`), and **Groq** (`ChatGroq`).
  * Utilizing LangChain's generic `init_chat_model` helper to load models dynamically (e.g., `gemini-1.5-flash`, `llama-3.1-8b-instant`).
  * Invoking models and processing text completions vs. raw `AIMessage` objects.

### [3. Custom Tools & Bindings]
* **Objective:** Teach models how to interact with custom Python functions.
* **Topics Covered:**
  * Creating custom tools using the `@tool` decorator with detailed type hints and docstrings.
  * Binding tools to models using `model.bind_tools()`.
  * Implementing a **manual tool execution loop**:
    1. Send a query to the model.
    2. Extract `tool_calls` from the response.
    3. Programmatically execute the Python tool with model-provided arguments.
    4. Format the result as a `ToolMessage` and return it to the model for a final, synthesized answer.

### [4. Messages & State]
* **Objective:** Understand how conversations are structured and maintained in memory.
* **Topics Covered:**
  * Core LangChain message components:
    * `SystemMessage`: Sets behavior directives for the model.
    * `HumanMessage`: User-generated inputs.
    * `AIMessage`: Assistant responses containing text outputs and tool call intents.
    * `ToolMessage`: Outputs returned back to the model after tool execution.
  * Managing multi-turn conversation lists.
  * Extracting usage metadata (e.g., input/output token counts).

### [5. Structured Output](file:///d:/TEJAA/Agentic%20AI/langchain/5-structured_output.ipynb)
* **Objective:** Direct LLMs and Agents to return structured data instead of unstructured text.
* **Topics Covered:**
  * Using Pydantic models with `.with_structured_output()`.
  * Returning raw messages alongside parsed objects (`include_raw=True`).
  * Creating nested data schemas for complex outputs.
  * Leveraging `TypedDict` and Python `dataclasses` for structure.
  * Forcing structured outputs in LangChain Agents using `response_format`.

---

## 🛠️ Setup & Installation

### 1. Prerequisites
Make sure you have Python (version `3.11` or higher recommended, configured for `>=3.14` in `pyproject.toml`) and virtual environment packages installed.

### 2. Install Dependencies
You can install dependencies using either `uv` (recommended) or standard `pip`:

Using `uv`:
```bash
uv pip install -r requirements.txt
```

Using standard `pip`:
```bash
pip install -r requirements.txt
```

### 3. Environment Setup
Create a `.env` file in the root directory (based on [.env](file:///d:/TEJAA/Agentic%20AI/.env)) and specify your API credentials:

```env
OPENAI_API_KEY="your-openai-api-key"
GOOGLE_API_KEY="your-google-api-key"
GROQ_API_KEY="your-groq-api-key"
```

> [!TIP]
> If you run into `RateLimitError / Insufficient Quota (429)` errors with OpenAI, switch your model initialization to Google Gemini (`gemini-1.5-flash`) or Groq (`llama-3.1-8b-instant`) to continue learning with your other free/active API keys!
