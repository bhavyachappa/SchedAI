# Setup Guide

## Prerequisites

- [Twilio](https://twilio.com) account (free)
- [Groq](https://console.groq.com) account (free)
- [n8n Cloud](https://n8n.io) account (free tier)
- Google account (Calendar + Sheets)

---

## Step 1 — Twilio WhatsApp Sandbox

1. Sign up at twilio.com → verify your phone number
2. Dashboard → **Messaging → Try it out → Send a WhatsApp message**
3. Note your sandbox number: `+1 415 523 8886`
4. Send `join [your-code]` from your WhatsApp to activate
5. Set **"When a message comes in"** to your n8n webhook URL:
   ```
   https://[your-n8n].app.n8n.cloud/webhook/schedai
   ```
   Method: `POST` → Save

---

## Step 2 — Groq API Key

1. Sign up at console.groq.com
2. API Keys → Create Key → copy it
3. In n8n → Credentials → Add → **Groq** → paste key → Save

---

## Step 3 — Google Calendar

1. n8n → Credentials → Add → **Google Calendar OAuth2 API**
2. Sign in with Google → Allow
3. Note your calendar email

---

## Step 4 — Google Sheets (Ideas)

1. Create a new Google Sheet named **SchedAI Ideas**
2. Row 1 headers: `Date | Idea | Category | Status`
3. Copy the Sheet ID from the URL
4. n8n → Credentials → Add → **Google Sheets OAuth2 API** → Sign in

---

## Step 5 — Import Workflows

1. n8n → Workflows → Import
2. Import `n8n-workflows/SchedAI-Core.json`
3. Import `n8n-workflows/SchedAI-Reminders.json`
4. In SchedAI Core — update these values:
   - All Twilio nodes: change `+917671841401` to your number (with country code)
   - All Twilio nodes: change `+14155238886` to your Twilio sandbox number
   - All Google Sheets nodes: update the Sheet ID
5. Open **Categorise Idea** and **Groq — Extract Event** nodes → set Groq credential
6. Open **Download Audio** → set HTTP Basic Auth (Twilio SID + Auth Token)
7. Publish both workflows

---

## Twilio Basic Auth (for voice notes)

When setting up the Download Audio node:
```
Username: your Twilio Account SID (starts with AC)
Password: your Twilio Auth Token
```

---

## Testing

Send these from your WhatsApp to your sandbox number:

```
Coffee meeting tomorrow 3pm Starbucks
```
→ Event created, WhatsApp confirmation received

```
idea: build a pitch deck for case competition
```
→ Row added to Google Sheet

```
[reply to any confirmation with] UNDO
```
→ Event deleted from Google Calendar

---

## Troubleshooting

| Issue | Fix |
|---|---|
| No execution fires | Check Twilio webhook URL matches n8n production URL |
| Wrong time in reminder | Server runs UTC — IST (+5:30) is applied in code |
| Voice note fails | Check Twilio Basic Auth on Download Audio node |
| Ideas not saving | Verify Sheet ID and column header spelling |
| UNDO not working | Must reply to the exact confirmation bubble, not type UNDO fresh |
