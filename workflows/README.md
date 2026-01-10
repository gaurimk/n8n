# 🎫 Ticket Urgency Classification – n8n Workflow

This repository contains an **n8n automation workflow** that classifies incoming support tickets into urgency levels (**LOW, MEDIUM, HIGH, CRITICAL**) using **OpenAI**.

The workflow is designed to be used as a **Webhook API**, making it easy to integrate with helpdesk systems, forms, or internal tools.

---

## 🚀 What This Workflow Does

- Accepts a support ticket via HTTP POST request  
- Sends the ticket text to an OpenAI model  
- Classifies the ticket urgency based on predefined rules  
- Returns **only the urgency label** as a JSON response  

---
## 📊 Workflow Diagram

![Ticket Urgency Workflow](images/workflow.jpg)


## 🧠 Urgency Classification Rules

The AI strictly follows these rules:

- **CRITICAL** – System down, payment failure, security issue, all users affected  
- **HIGH** – Major feature broken, many users impacted  
- **MEDIUM** – Single-user issue, workaround exists  
- **LOW** – Minor issue, question, or request  

⚠️ The response contains **only the label** (no explanation, no punctuation).

---

## 🧩 Workflow Overview

### Nodes Used

- **Webhook** – Receives ticket data  
- **Set (Edit Fields)** – Extracts the ticket text  
- **OpenAI (LangChain)** – Classifies urgency  
- **Respond to Webhook** – Sends urgency as JSON  

---

## 🔗 Webhook Details

- **Method:** `POST`  
- **Path:** `/ticket-urgency`

### Example Webhook URL
```text
https://your-n8n-domain/webhook/ticket-urgency
