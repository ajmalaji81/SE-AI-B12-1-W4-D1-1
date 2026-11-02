# Gmail AI Assistant (n8n LangChain Workflow)

An autonomous AI agent built in **n8n** using **LangChain** and **OpenAI (GPT-4.1-mini)** that parses conversational chat requests and automatically drafts or sends emails via the **Gmail API**.

---

## 🚀 Features

- **Conversational Chat Trigger**: Interact with your workflow in real time through n8n's native chat interface.
- **Agentic Decision Making**: Uses an n8n LangChain AI Agent (`Perception`) powered by OpenAI's `gpt-4.1-mini` (`Brain`) to understand intent, draft content, and identify recipients.
- **Short-Term Memory**: Integrates a `Buffer Window Memory` module so the assistant remembers context across multi-turn chat sessions.
- **Automated Gmail Tool Execution**: Auto-maps dynamically extracted recipient (`To`), `Subject`, and `Message` content to automatically dispatch or manage emails.

---

## 🛠️ Architecture

```
[ Chat Trigger ] 
       │
       ▼
 [ AI Agent ("Perception") ]
       ├── Language Model: OpenAI ("Brain", gpt-4.1-mini)
       ├── Memory: Window Buffer Memory
       └── Tool: Gmail Action Tool ($fromAI parameters)
```

---

## 📋 Prerequisites

Before importing this workflow into your n8n instance, ensure you have:

1. **n8n** (v1.0.0+ recommended with LangChain nodes enabled).
2. **OpenAI API Key**: With access to chat completion models (e.g., `gpt-4.1-mini`).
3. **Google Workspace / Gmail OAuth2 Credentials**: Configured in n8n with Gmail scopes enabled (`send`, `read/write`).

---

## ⚙️ Installation & Setup

1. **Import Workflow**:
   - In your n8n dashboard, go to **Workflows** > **Add Workflow**.
   - Click the three dots `...` in the top-right corner and select **Import from File** (or **Import from URL** / paste the JSON).
   - Select your workflow JSON file (`gmail-email-ai.json`).

2. **Configure Credentials**:
   - **OpenAI Node ("Brain")**:
     - Open the `Brain` node.
     - Attach or create your OpenAI API credentials.
   - **Gmail Node ("gmail action")**:
     - Open the `gmail action` node.
     - Connect your Google OAuth2 account credentials.

3. **Activate & Test**:
   - Toggle the workflow switch to **Active**.
   - Click **Chat** at the bottom-right of the n8n canvas to test your agent.
   - *Example prompt*:  
     > *"Send an email to contact@example.com with the subject 'Meeting Notes' summarizing our discussion about the launch."*

---

## 🔒 Security & Best Practices

- **Test Before Production**: Always test recipient routing and message formatting in a sandbox before connecting personal or enterprise email accounts.
- **Environment Variables**: Avoid hardcoding sensitive API keys or OAuth secrets directly into workflow JSON exports.

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).