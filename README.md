# 📧 n8n Gmail Unread Email Summariser

An AI Agent workflow built in **n8n** that reads your latest 5 unread Gmail emails, summarises each in one line using an AI model, and sends all 5 summaries back to you as a single digest email.

## ✨ Features
- Fetches the 5 most recent unread emails from Gmail
- Uses an AI Agent (OpenAI gpt-4o-mini) to write a one-line (20 words max) summary per email
- Combines all summaries into a single block of text
- Emails the digest back to your own inbox under a clear subject line

## 🛠️ Tech Stack
- **n8n** — workflow automation (self-hosted)
- **Gmail API** (Google Cloud OAuth) — fetch & send mail
- **OpenAI GPT-4o-mini** — email summarisation

## ⚙️ How It Works
1. Manual Trigger starts the workflow
2. **Gmail — Get Many** node fetches the latest 5 unread messages (Read Status: Unread, Limit: 5)
3. **AI Agent** node summarises each email in one line, using its `From`, `Subject`, and `snippet` fields
4. **Aggregate** node (Individual Fields, field: `output`) combines the 5 summaries into one array
5. **Gmail — Send** node emails the joined summaries to your own address

## 📂 Setup
1. Import `Unread Email Summariser.json` into your n8n instance
2. Add credentials:
   - Gmail OAuth2 (via Google Cloud Console — Gmail API enabled, OAuth consent screen, Web application client)
   - OpenAI API Key
3. Activate the workflow and click Execute, or run it on demand

## 👤 Author
Built by [swarnasudarshan3-prog](https://github.com/swarnasudarshan3-prog) as part of the Social Eagle Week 4 Day 1 assignment.
