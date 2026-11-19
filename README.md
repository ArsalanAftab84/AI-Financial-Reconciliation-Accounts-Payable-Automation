# Autonomous GitHub Triage Agent (n8n)

An AI-powered GitHub triage and code-review agent built in **n8n**. It inspects live repository files, identifies bugs and security risks from actual source code, and drafts GitHub issues behind a Human-in-the-Loop (HITL) approval step.

**[Interactive Workflow Preview](https://ArsalanAftab84.github.io/AI-Financial-Reconciliation-Accounts-Payable-Automation/)** | **[Download `workflow.json`](./workflow.json)**

## What It Does
- **Repository Exploration:** Dynamically lists repository contents and reads target source files on demand rather than guessing code contents.
- **Automated Bug & Security Triage:** Analyzes source files and cites exact file paths, functions, and issues found.
- **Human-in-the-Loop (HITL) Guardrail:** Requires explicit approval before performing write actions such as creating GitHub issues.
- **Session Memory:** Maintains conversational context across follow-up turns so issues can be drafted from prior analysis.

## Architecture & Tools
| Component | Role |
|---|---|
| **Chat Trigger** | Interactive chat interface for sending triage tasks and follow-up commands |
| **AI Agent (ReAct Loop)** | Orchestrates reasoning, tool selection, and response generation |
| **Simple Memory** | Preserves recent conversation context across turns |
| **`list_repo_files`** | Lists files inside the target GitHub repository |
| **`read_repo_file`** | Reads raw source code from a specified file path |
| **`get_repo_issues`** | Retrieves existing repository issues to avoid duplicates |
| **`create_github_issue`** | Opens a formatted GitHub issue after human approval |

## Quick Setup
1. Download [`workflow.json`](./workflow.json) from this repository.
2. Open your **n8n** workspace, create a new workflow, open the top-right menu (`...`), and select **Import from File**.
3. Configure your credentials inside n8n:
   - **LLM Provider:** Connect your preferred tool-calling chat model (e.g., OpenRouter, Google Gemini, Groq, or OpenAI).
   - **GitHub API:** Add your GitHub Personal Access Token (with `repo` scope for private repositories or issue creation).
   - **Google Sheets (if used):** Replace the placeholder Sheet link/ID with your own Google Sheet.
4. Update the target **Repository Owner** and **Repository Name** fields in the GitHub tool nodes.
5. Click **Open Chat** and test with a prompt such as:
   > `List the files in my repository, read app.py, and report any bugs or security issues.`

## Sanitization Note
All personal API keys, tokens, and private Google Sheet links have been stripped from `workflow.json` before publishing.
