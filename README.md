# WhatsApp Voice Agent

This repository contains an n8n workflow that turns incoming WhatsApp voice messages into a conversational AI voice experience using Groq models.

## What this workflow does

The flow performs the following steps:

1. Receives a new WhatsApp message event.
2. Extracts the attached audio file from the message.
3. Sends the audio to Groq for speech-to-text transcription.
4. Passes the transcribed text to an AI agent for a concise, conversational reply.
5. Converts the AI response into speech with Groq text-to-speech.
6. Sends the generated audio back to the same WhatsApp conversation.

## Included files

- [whatsapp-voice-agent-workflow.json](whatsapp-voice-agent-workflow.json) — the exported n8n workflow for the voice agent.

## Prerequisites

Before importing and running the workflow, make sure you have:

- An n8n instance
- A Groq API key with access to transcription, chat, and speech endpoints
- A WhatsApp integration connected to your n8n instance
- Appropriate credentials configured inside n8n

## Setup instructions

1. Import [whatsapp-voice-agent-workflow.json](whatsapp-voice-agent-workflow.json) into n8n.
2. Create or update the Groq credential used by the workflow.
3. Connect the WhatsApp trigger and WhatsApp send nodes to your active WhatsApp integration.
4. Activate the workflow.
5. Send a voice note to the configured WhatsApp number and wait for the reply.

## Notes

- The workflow uses the Groq chat model `llama-3.3-70b-versatile`.
- Speech-to-text uses `whisper-large-v3`.
- Text-to-speech uses `canopylabs/orpheus-v1-english` with the `hannah` voice.
- The AI agent prompt is tuned for short, natural-sounding voice replies.

## Customization ideas

You can improve or extend the workflow by:

- Changing the system prompt to adjust tone or behavior
- Switching to different Groq models for better speed or quality
- Adding fallback logic for unsupported audio or failed requests
- Connecting additional services such as CRM, support tickets, or knowledge bases

## Security note

Keep your API keys and WhatsApp credentials inside n8n credentials rather than hardcoding them in the workflow.
