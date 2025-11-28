# 🤖 Portfólio de Automações com IA (n8n + LLM)

Este repositório reúne automações criadas para demonstrar domínio em:
- Integração n8n (iPaaS)
- Modelos de linguagem (OpenAI)
- Design de fluxos com IA
- Validação, parsing e tratamento de erros
- Conexões com Google Sheets, Gmail e APIs externas

Cada automação inclui:
- Resumo do caso de uso
- Prints do fluxo
- JSON de exportação
- Explicação técnica do funcionamento

---

## 📌 1. Classificação Automática de Leads (IA + Retry)

### 🎯 Objetivo
Classificar leads automaticamente como **alta**, **média** ou **baixa** prioridade com base na descrição fornecida.

### 🧩 Tecnologias
- n8n
- OpenAI GPT-4o-mini
- Google Sheets
- Gmail

### 🖼 Prints
![workflow-1-img1.png](screenshots/auto-classification/img1.png)
![workflow-1-img2.png](screenshots/auto-classification/img2.png)
![workflow-1-img3.png](screenshots/auto-classification/img3.png)
![workflow-1-img4.png](screenshots/auto-classification/img4.png)

---

### 🧠 Explicação Técnica
- Trigger captura nova linha no Google Sheets.
- Node de IA classifica o lead retornando JSON estrito (`prioridade`, `motivo`).
- Código faz parsing seguro e validação rigorosa (tipos, campos obrigatórios).
- Em caso de erro, uma **retentativa** é acionada com prompt mais restritivo.
- Se ambas falharem, um email é enviado; senão, a linha é atualizada na planilha.

---

### 🧾 JSON Exportado
[Auto-Classification Workflow.json](workflows/Auto-Classification%20Workflow.json)

---

## 📌 2. Em Desenvolvimento

### 🎯 Objetivo
TBD

### 🧠 Explicação Técnica)
- TBD

### 🖼 Prints


### 🧾 JSON Exportado

---
## 📎 Contato

Se quiser discutir automação com IA, desenho de Workflow ou projetos n8n:

**gestevao04@gmail.com**  
**LinkedIn: https://www.linkedin.com/in/giordanome/?locale=pt**

