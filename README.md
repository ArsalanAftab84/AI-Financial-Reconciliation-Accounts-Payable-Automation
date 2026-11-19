# AI Financial System (n8n)

An automated AI-powered financial management and tracking system built in **n8n**. It processes incoming financial inputs (expenses, income, receipts, or natural-language queries), extracts and categorizes transaction data using an LLM, and syncs structured records directly with **Google Sheets** for real-time tracking and reporting.

## Key Features
- **AI Transaction Parsing:** Automatically extracts amounts, categories, dates, descriptions, and transaction types from natural-language prompts or incoming messages.
- **Automated Google Sheets Sync:** Logs and updates structured financial entries in Google Sheets without manual data entry.
- **Conversational Financial Insights:** Answers questions about spending patterns, balances, or summaries directly from live sheet data.
- **Modular n8n Architecture:** Easily extensible to connect additional channels (Chat, Telegram, WhatsApp, Gmail, or Webhooks) and swap LLM providers.

## Architecture & Core Components
| Component | Role |
|---|---|
| **Trigger Node** | Captures incoming financial inputs, commands, or scheduled reporting runs |
| **AI Agent / LLM Node** | Parses unstructured inputs, classifies transactions, and generates financial summaries |
| **Memory Node** | Maintains conversational context across follow-up queries |
| **Google Sheets Integration** | Stores, reads, and updates structured transaction records and budgets |

## Quick Setup
1. Download [`workflow.json`](./workflow.json) from this repository.
2. Open your **n8n** workspace, create a new workflow, open the top-right menu (`...`), and select **Import from File**.
3. Configure your credentials in n8n:
   - **LLM Provider:** Connect your preferred chat model API key (e.g., Google Gemini, OpenAI, Groq, or OpenRouter).
   - **Google Sheets OAuth2:** Connect your Google account and grant access to Sheets.
4. Create a new Google Sheet and replace the placeholder Google Sheet URL/ID in the Google Sheets node(s) with your own sheet.
5. Activate the workflow and test with a sample input (e.g., *"Log an expense of $25 for groceries today"* or *"Summarize my spending this week"*).
