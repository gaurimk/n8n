🎫 Ticket Urgency Classification – n8n Workflow

This repository contains an n8n automation workflow that classifies incoming support tickets into urgency levels (LOW, MEDIUM, HIGH, CRITICAL) using OpenAI.

The workflow is designed to be used as a Webhook API, making it easy to integrate with helpdesk systems, forms, or internal tools.

🚀 What This Workflow Does

Accepts a support ticket via HTTP POST request

Sends the ticket text to an OpenAI model

Classifies the ticket urgency based on predefined rules

Returns only the urgency label as a JSON response

🧠 Urgency Classification Rules

The AI strictly follows these rules:

CRITICAL – System down, payment failure, security issue, all users affected

HIGH – Major feature broken, many users impacted

MEDIUM – Single-user issue, workaround exists

LOW – Minor issue, question, or request

⚠️ The response contains only the label (no explanation, no punctuation).

🧩 Workflow Overview

Nodes used:

Webhook – Receives ticket data

Set (Edit Fields) – Extracts the ticket text

OpenAI (LangChain) – Classifies urgency

Respond to Webhook – Sends urgency as JSON

🔗 Webhook Details

Method: POST

Path: /ticket-urgency

Example Webhook URL
https://your-n8n-domain/webhook/ticket-urgency

📥 Request Format

Send a POST request with JSON body:

{
  "ticket": "Users are unable to complete payments on checkout"
}

📤 Response Format
{
  "urgency": "CRITICAL"
}

🛠️ Requirements

n8n (self-hosted or cloud)

OpenAI API key

OpenAI credentials configured inside n8n

⚙️ Setup Instructions

Open n8n

Click Import Workflow

Upload ticket-urgency-classification.json

Configure OpenAI credentials

Activate the workflow

Copy the webhook URL

Send POST requests to start classifying tickets

🧪 Testing

You can test using:

Browser extensions (REST Client)

Postman

cURL

Example cURL:

curl -X POST https://your-n8n-domain/webhook/ticket-urgency \
  -H "Content-Type: application/json" \
  -d '{"ticket":"Login service is completely down for all users"}'
