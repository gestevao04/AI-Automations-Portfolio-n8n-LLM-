# 🤖 Portfólio de Automações com IA (n8n + LLM)

Este repositório reúne automações
criadas para demonstrar domínio em:
- Integração n8n (iPaaS)
- Modelos de linguagem (Gemini)
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
- Google Gemini 2.0 Flash
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

## 📌 2. AI Ticket Intake

### 🎯 Objetivo
Classificar, resumir e gerar uma resposta inicial automática para tickets enviados via webhook, garantindo consistência, validação rigorosa e retentativas inteligentes quando o modelo retorna dados inválidos.

### 🧩 Tecnologias
- n8n
- Webhook Trigger
- Google Gemini 2.0 Flash
- PostgreSQL
- Gmail
- JavaScript

### 🖼 Prints
![workflow-2-img1.png](screenshots/helpdesk-ai/img1.png)
![workflow-2-img2.png](screenshots/helpdesk-ai/img2.png)
![workflow-2-img3.png](screenshots/helpdesk-ai/img3.png)
![workflow-2-img4.png](screenshots/helpdesk-ai/img4.png)

---

### 🧠 Explicação Técnica
- Webhook recebe o ticket com `title`, `description` e `customer_id`.
- Campos são normalizados para uso consistente entre todos os LLMs.
- Três modelos Gemini atuam separadamente:
    - **Classificação:** categoria + urgência (JSON estrito)
    - **Resumo:** frase curta para dashboards internos
    - **Resposta sugestiva:** mensagem inicial para o cliente
- Node de código faz **parsing e validação** da classificação:
    - checa JSON, tipos, campos obrigatórios
    - aplica **retentativas automáticas** (até 3x)
    - em falha final, envia alerta por email
- Resultados consolidados e logs são persistidos no PostgreSQL para uso interno.

---

### 🧾 JSON Exportado
[AI Ticket Intake Workflow.json](workflows/AI%20Ticket%20Intake%20Workflow.json)

## 📌 3. Revenue Ops Automation

### 🎯 Objetivo
Automatizar o intake e tratamento de oportunidades (deals) usando IA, garantindo **validação de dados**, **enriquecimento com Gemini**, **classificação automática**, criação de **next steps**, geração de **KPIs** e **notificações inteligentes** no Telegram.

### 🧩 Tecnologias
- n8n
- Schedule Trigger
- HTTP Request (JSON Mapping)
- Google Gemini 2.0 Flash
- PostgreSQL
- Google Sheets
- Gmail
- JavaScript
- Telegram

### 🖼 Prints
![workflow-2-img1.png](screenshots/sales-ai/img1.png)
![workflow-2-img1.png](screenshots/sales-ai/img2.png)
![workflow-2-img1.png](screenshots/sales-ai/img3.png)
![workflow-2-img1.png](screenshots/sales-ai/img4.png)
![workflow-2-img1.png](screenshots/sales-ai/img5.png)

---

### 🧠 Explicação Técnica
- Trigger recebe deals via **Webhook** e transforma cada item do array em **execuções independentes** (Split in Batches / Item Lists).
- Função JS valida dados obrigatórios: `amount`, `description`, `close_date`, `stage`.
- Campos inválidos viram um array `missing_fields` e influenciam o fluxo (normal vs. missing data).
- IA gera um resumo estruturado (`ai_summary`), prioridade, classificação e next steps, com **validação rigorosa de JSON**.
- Fluxo implementa **retentativas**, se a IA retornar valores inválidos ou fora do schema.
- Writes no Google Sheets criam uma linha consolidada com timestamps, dados originais, enriquecimento e erros.
- Telegram envia dois tipos de mensagens:
  - Deals válidos → mensagem padrão
  - Deals com problemas → alerta destacando quais campos estão faltando
- Logs de auditoria são gerados em nova aba da planilha, com `uuid`, status, etapa e payload de erro.

---

### 🧾 JSON Exportado
[Revenue Ops Automation Workflow.json](workflows/Revenue%20Ops%20Automation%20Workflow.json)

---
## 📎 Contato

Se quiser discutir automação com IA, desenho de Workflow ou projetos n8n:

**gestevao04@gmail.com**  
**LinkedIn: https://www.linkedin.com/in/giordanome/?locale=pt**

