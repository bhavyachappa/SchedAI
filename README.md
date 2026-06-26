# SchedAI 🤖📅

**WhatsApp AI Scheduling Assistant**

Drop any message into WhatsApp — text, voice note, or multiple events at once — and SchedAI creates the calendar events, sends you reminders, and captures your ideas. Reply UNDO to any confirmation to delete it instantly.

Built for personal use. Runs entirely on free-tier services.

---

## Features

| What you send | What happens |
|---|---|
| `Finance exam Friday 2pm Auditorium B` | Single event created |
| `Marketing 9am Mon, Finance 2pm Wed, Study group 6pm Fri` | 3 events created |
| `Breakfast 7:30-10:30am for 27,28,29,30 June` | 4 events created |
| Voice note | Transcribed by Groq Whisper → event created |
| Reply UNDO to any confirmation | Event deleted from calendar |
| `idea: pitch SchedAI to MBA tech club` | Saved to Google Sheets with auto-category |
| `show my ideas` / `show career ideas` | Lists open ideas |
| `done with idea 2` | Marks idea as done |
| — | WhatsApp reminder 20 min before every event |

---

## How It Works

```
WhatsApp → Twilio → n8n (30 nodes) → Groq AI → Google Calendar
                                   → Google Sheets (ideas)
                                   → Twilio → WhatsApp (confirmation)

Reminders: cron every minute → Google Calendar → Twilio → WhatsApp
```

Every confirmation message contains a hidden `[ref:EVENT_ID]`. When you reply with `UNDO`, SchedAI reads the ref and deletes exactly that event.

---

## Stack

| Service | Purpose | Cost |
|---|---|---|
| Twilio | WhatsApp sandbox | Free |
| n8n Cloud | Workflow automation | Free tier |
| Groq Llama 3.3 70B | Event extraction + idea categorisation | Free |
| Groq Whisper Large v3 | Voice note transcription | Free |
| Google Calendar API | Event creation and deletion | Free |
| Google Sheets | Ideas storage | Free |

**Total monthly cost: ~$0**

---

## Workflows

| File | Nodes | Purpose |
|---|---|---|
| `n8n-workflows/SchedAI-Core.json` | 30 | Main message handler |
| `n8n-workflows/SchedAI-Reminders.json` | 6 | Cron reminder scheduler |

Export these from your n8n instance and commit them here so others can import and run.

---

## Setup

See [docs/SETUP.md](docs/SETUP.md) for the full step-by-step guide.

**Services needed:**
- [Twilio](https://twilio.com) — WhatsApp sandbox
- [Groq](https://console.groq.com) — free API key
- [n8n Cloud](https://n8n.io) — workflow host
- Google account — Calendar + Sheets OAuth

---

## License

MIT © 2026 Bhavya Sri Chappa
