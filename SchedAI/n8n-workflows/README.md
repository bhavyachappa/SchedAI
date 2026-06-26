# n8n Workflows

Export your workflows from n8n and place them here.

## Files

- `SchedAI-Core.json` — Main workflow (30 nodes): handles all WhatsApp messages, event creation, ideas, UNDO/EDIT
- `SchedAI-Reminders.json` — Reminder scheduler (6 nodes): cron every minute, sends WhatsApp alerts before events

## How to Export

1. Open workflow in n8n
2. Top right `...` menu → **Export**
3. Save the JSON file here

## How to Import

1. n8n → Workflows → top right `...` → **Import**
2. Upload the JSON file
3. Connect credentials (Groq, Twilio, Google Calendar, Google Sheets)
4. Publish
