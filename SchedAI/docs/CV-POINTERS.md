# SchedAI — CV & Portfolio Pointers

## Project Title
**SchedAI — AI-Powered WhatsApp Scheduling Assistant**

---

## One-Line Description
> Engineered a zero-cost AI agent that converts WhatsApp messages (text, voice, multi-event) into Google Calendar events using Groq LLM, n8n automation, and Twilio — with automated reminders and an ideas capture system.

---

## Resume Bullet Points

### Impact-First (Recommended for MBA/Consulting roles)
- Built SchedAI, a production AI scheduling agent that eliminates manual calendar entry by processing natural language WhatsApp messages — text, voice notes, and multi-event inputs — into structured Google Calendar events with sub-3-second response time
- Reduced scheduling friction to zero by integrating Groq Llama 3.3 70B for intelligent event extraction, achieving 90%+ parsing accuracy across ambiguous, multi-event, and time-relative inputs
- Architected a 5-path message classification system routing events, ideas, voice notes, list queries, and task completions through purpose-built n8n workflows serving real-time WhatsApp interactions
- Delivered the complete solution on a $0/month infrastructure stack (Groq free tier, n8n Cloud, Twilio sandbox, Google APIs), demonstrating cost-efficient engineering judgment

### Technical-First (Recommended for Tech/Product roles)
- Designed and deployed a multi-modal AI agent on n8n Cloud integrating 5 APIs: Twilio (WhatsApp), Groq (LLM + Whisper ASR), Google Calendar, Google Sheets — processing text, voice, and bulk event messages end-to-end
- Implemented voice-to-calendar pipeline using Groq Whisper Large v3 for free-tier ASR, with Twilio Basic Auth media download and structured event extraction via Llama 3.3 70B
- Built a cron-based reminder engine (runs every minute) with event-type-aware timing logic (20 min standard, 10 min social) and IST timezone correction for accurate WhatsApp delivery
- Engineered robust JSON parsing with automatic key quoting, markdown stripping, and midnight-crossing end-time correction to handle LLM output variability in production

---

## LinkedIn Post Copy

### Version 1 — Story format
Just shipped SchedAI 🤖📅

As an MBA student juggling classes, case competitions, group projects, and networking events, I was spending way too much time manually entering things into Google Calendar.

So I built a WhatsApp AI assistant that does it for me.

Drop any message → it's scheduled. Voice note → transcribed and scheduled. Multiple events in one message → all scheduled.

The entire stack runs for free:
→ Groq (Llama 3.3 + Whisper) for AI
→ n8n for automation
→ Twilio for WhatsApp
→ Google Calendar + Sheets

Zero manual entry. Zero infrastructure cost.

Built this in a weekend. GitHub link in comments 👇

#BuildInPublic #MBA #AI #Automation #n8n #Groq

### Version 2 — Technical format
Built SchedAI: A WhatsApp AI Scheduling Agent 🤖

Tech stack:
• Groq Llama 3.3 70B → natural language event extraction
• Groq Whisper Large v3 → voice note transcription
• n8n Cloud → workflow automation (25 nodes)
• Twilio → WhatsApp interface
• Google Calendar + Sheets → storage

Features:
✅ Text → calendar events
✅ Voice notes → transcribe → schedule
✅ Multiple events in one message
✅ Ideas capture with AI categorisation
✅ WhatsApp reminders (20 min / 10 min before)

Infrastructure cost: ~$0/month

Full code + setup guide on GitHub 👇

#AI #LLM #Automation #BuildInPublic #n8n #Groq

---

## Interview Talking Points

### "Tell me about a project you built"
> "I built SchedAI, a WhatsApp AI assistant that schedules calendar events from natural language messages. The interesting engineering challenge was handling the variety of inputs — text, voice notes, multiple events in one message — and routing them through the right processing pipeline. I used Groq's Llama 3.3 model for event extraction and Whisper for voice transcription, all orchestrated through n8n. The whole system runs for free on cloud services. What made it genuinely useful was adding a reminder system that sends WhatsApp messages 20 minutes before events based on their type."

### "What technical challenges did you face?"
> "The main challenge was LLM output reliability. Groq's Llama model sometimes returned unquoted JSON keys or markdown-wrapped responses. I wrote a parsing layer that strips backticks, normalises keys with regex, and handles edge cases like midnight-crossing end times. Another challenge was the WhatsApp sandbox authentication — Twilio protects media URLs with Basic Auth, so voice note downloads needed separate credential handling."

### "Why n8n over writing custom code?"
> "For a personal tool with this many API integrations, n8n was the right call. It reduced weeks of boilerplate to hours, gives me a visual interface to debug executions, handles retries and error logging, and runs 24/7 on their free cloud. The tradeoffs — less customisation, vendor dependency — don't matter at this scale. Picking the right tool for the job is itself an engineering decision."

---

## Skills Tags
`Workflow Automation` · `LLM Integration` · `API Design` · `n8n` · `Groq` · `Twilio` · `Google Calendar API` · `Google Sheets API` · `Prompt Engineering` · `Voice AI (Whisper ASR)` · `Product Thinking` · `Zero-cost Architecture` · `Node.js` · `JSON Processing`
