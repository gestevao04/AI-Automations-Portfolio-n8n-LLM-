# 🤖 AI Automation Portfolio (n8n + LLM)

This repository showcases a collection of AI-powered automations built with **n8n**, **OpenAI**, **Google Sheets**, and supporting integrations.  
It is designed to demonstrate practical skills in:

- Building end-to-end workflows with AI
- Designing robust validation and retry logic
- Integrating systems and APIs through iPaaS
- Creating structured prompts and reliable outputs
- Logging, monitoring, and error handling in automation flows

You will find:
- Workflow descriptions
- Technical explanations
- Execution screenshots
- Exported JSON files

---

## 📌 1. Lead Auto-Classification (AI + Retry Logic)

### 🎯 Purpose
Automatically classify incoming leads as **high**, **medium**, or **low** priority based on a free-text description.

### 🧩 Tech Stack
- n8n
- OpenAI GPT-4o / GPT-4o-mini
- Google Sheets
- Gmail (fallback notification)

---

### 🖼 Screenshots
![workflow-1-img1.png](screenshots/auto-classification/img1.png)
![workflow-1-img2.png](screenshots/auto-classification/img2.png)
![workflow-1-img3.png](screenshots/auto-classification/img3.png)
![workflow-1-img4.png](screenshots/auto-classification/img4.png)

---

### 🧠 Technical Overview

- Trigger monitors a Google Sheets row insert.
- The LLM receives a structured classification prompt and must return a strict JSON schema.
- A JavaScript node parses and validates the JSON (type checks, required fields, allowed values).
- If parsing or validation fails, a **second AI attempt** is triggered with a more restrictive prompt.
- On success, the workflow updates the row; on repeated failure, an email alert is generated with debugging details.

---

### 🧾 Workflow Export (JSON)
[Auto-Classification Workflow.json](workflows/Auto-Classification%20Workflow.json)

---

## 📌 2. Developing

### 🎯 Purpose
TBD

### 🧠 Technical Overview

- TBD

### 🖼 Screenshots


### 🧾 Workflow Export  

---
## 📎 Contact

If you'd like to discuss AI automation, workflow design, or n8n projects:

**gestevao04@gmail.com**  
**LinkedIn: https://www.linkedin.com/in/giordanome/**
