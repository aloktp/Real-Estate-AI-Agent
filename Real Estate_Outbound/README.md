🏡 Real Estate AI Agent – Outbound Call Automation
This project enables automated, human-like outbound calls to real estate leads using ElevenLabs Conversational AI and Twilio.
It fetches lead data from Airtable, makes outbound calls, streams voice in real time, and logs results or triggers workflows using Make.com.
You can host it locally with ngrok or deploy it serverlessly via Replit. Built in JavaScript using Fastify.

✨ Features
📞 Outbound Calling: Initiate real phone calls via Twilio’s programmable voice API.

🧠 AI Conversations: Conduct real-time voice interactions using ElevenLabs' WebSocket-based Conversational AI.

📊 Airtable Integration:

Fetch lead phone numbers before the call

Log captured info (name, email, etc.) after the call

⚙️ Workflow Automation: Use Make.com to trigger CRM updates, emails, or SMS follow-ups after the call.

🌐 Hosting Options:

ngrok for local development

Replit for always-on cloud deployment

🧪 Built With: JavaScript, Fastify, dotenv, WebSockets, Twilio SDK, and ElevenLabs SDK

🚀 Getting Started
1. Clone the Repository
bash
Copy
Edit
git clone git@github.com:aloktp/Real-Estate-AI-Agent-.git
cd Real-Estate-AI-Agent-
2. Install Dependencies
bash
Copy
Edit
npm install
3. Configure Environment
Create a .env file in the root directory and add the following:

ini
Copy
Edit
ELEVENLABS_AGENT_ID=your-elevenlabs-agent-id
TWILIO_ACCOUNT_SID=your-twilio-sid
TWILIO_AUTH_TOKEN=your-twilio-auth
TWILIO_PHONE_NUMBER=your-twilio-phone
AIRTABLE_API_KEY=your-airtable-key
AIRTABLE_BASE_ID=your-airtable-base-id
PORT=8000
4. Start the Server
bash
Copy
Edit
node index.js
5. Start ngrok (for Twilio webhooks)
bash
Copy
Edit
ngrok http 8000
Update your Twilio Console under Voice > Webhook settings with the new https://<your-ngrok-url>.

🔁 Making an Outbound Call
Send a POST request to initiate a call:

bash
Copy
Edit
curl -X POST http://localhost:8000/make-outbound-call \
-H "Content-Type: application/json" \
-d '{"to": "+1234567890"}'
🧠 AI Prompt Design
ElevenLabs Conversational AI is triggered via WebSocket using a customizable prompt.
You can edit the prompt to change tone, purpose, or persona.
See the file:

nginx
Copy
Edit
The prompt used in Elevenlabs ConvAI.txt
🛠️ Tech Stack Summary
Tool	Purpose
JavaScript	Server-side logic
Fastify	HTTP server framework
Twilio	Outbound calling + media stream handling
ElevenLabs	Voice AI for real-time conversations
AirTable	Lead source + CRM-style post-call storage
Make.com	Post-call automation (email, updates, etc)
ngrok	Expose local server to public internet
Replit	Cloud deployment option

📁 Additional Files
index.js: Main server with Fastify and WebSocket handlers

.env: Environment config (not committed)

Make.com blueprint*.json: Predefined workflows for post-call automation

*.mp3: Sample audio from AI-generated conversations

