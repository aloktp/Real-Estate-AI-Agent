# 🏡 Real Estate AI Agent – Outbound Call Automation

This project enables automated, human-like outbound calls to real estate leads using **ElevenLabs Conversational AI** and **Twilio**.
It pulls lead data from **Airtable**, places outbound calls, handles real-time voice streaming, and logs results or triggers workflows via **Make.com**.
You can run the system locally with **ngrok** or host it on the cloud using **Replit**.
The backend is built entirely in **JavaScript** using **Fastify**.

---

## ✨ Features

* **📞 Outbound Calling**: Initiate real phone calls via Twilio’s programmable voice API.
* **🧠 AI Conversations**: Handle live voice interactions using ElevenLabs' WebSocket-based Conversational AI.
* **📊 Airtable Integration**:

  * Fetch lead phone numbers before the call
  * Log captured details (name, email, etc.) after the call
* **⚙️ Workflow Automation**: Use Make.com to build automations like CRM updates, SMS alerts, or email follow-ups.
* **🌐 Hosting Options**:

  * `ngrok` for local testing
  * `Replit` for serverless, always-on deployment

---

## 🚀 Getting Started

### 1. Clone the Repository

```bash
git clone git@github.com:aloktp/Real-Estate-AI-Agent-.git
cd Real-Estate-AI-Agent-
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Configure Environment

Create a `.env` file in the root directory and populate it with the following values:

```env
ELEVENLABS_AGENT_ID=your-elevenlabs-agent-id
TWILIO_ACCOUNT_SID=your-twilio-sid
TWILIO_AUTH_TOKEN=your-twilio-auth
TWILIO_PHONE_NUMBER=your-twilio-phone
AIRTABLE_API_KEY=your-airtable-key
AIRTABLE_BASE_ID=your-airtable-base-id
PORT=8000
```

### 4. Start the Server

```bash
node index.js
```

### 5. Start ngrok (for Twilio Webhooks)

```bash
ngrok http 8000
```

Use the HTTPS forwarding URL (e.g., `https://abcd1234.ngrok.io`) in your Twilio Console → Voice → Webhook URL field.

### 6. Make an Outbound Call

Send a POST request to initiate a call:

```bash
curl -X POST http://localhost:8000/make-outbound-call \
-H "Content-Type: application/json" \
-d '{"to": "+1234567890"}'
```

---

## 🧠 AI Prompt Design

The voice agent’s behavior is defined using a custom prompt passed to ElevenLabs’ Conversational AI over WebSocket.
This prompt controls tone, flow, and data capture logic.

**See:** `The prompt used in Elevenlabs ConvAI.txt` for a customizable example.

---

## 🛠️ Tech Stack Summary

| Tool       | Purpose                                        |
| ---------- | ---------------------------------------------- |
| JavaScript | Server-side scripting                          |
| Fastify    | Lightweight HTTP server framework              |
| Twilio     | Outbound calls and audio streaming (WebSocket) |
| ElevenLabs | Real-time conversational voice AI              |
| Airtable   | Lead data management and CRM logging           |
| Make.com   | Post-call automation workflows                 |
| ngrok      | Expose local server to public (for Twilio)     |
| Replit     | Optional cloud hosting                         |

---

## 📁 Key Project Files

* `index.js` – Core server logic using Fastify and WebSockets
* `.env` – Credentials and config (excluded from Git)
* `Make.com blueprint*.json` – Ready-made Make.com workflow templates
* `The prompt used in Elevenlabs ConvAI.txt` – Custom prompt logic for AI calls
* `Audio for conversation*.mp3` – Sample generated calls by the AI system
