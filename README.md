# Creator Marketing Automation Platform 🚀

An end-to-end production-ready automation platform that streamlines influencer/creator outreach, personalized email generation, response tracking, and CRM status updates using **n8n**, **Gmail API**, **Groq LLM (`compound-mini`)**, and **Google Sheets**.

---

## 🏗 System Architecture Flow

1. **Outreach Candidates Ingestion:** Ingests creator profiles from Google Sheets (`Qualified Creators`).
2. **AI-Powered Outreach Drafting:** Uses Groq API (`compound-mini`) to generate hyper-personalized outreach emails.
3. **Human-in-the-Loop Approval:** Holds drafts until reviewed and marked as `APPROVED`.
4. **Automated Dispatch:** Dispatches approved emails via Gmail API.
5. **Real-Time Reply Processing:** Listens for incoming email responses using Gmail Trigger.
6. **Sentiment Parsing:** Parses creator reply sentiment and generates concise summaries via Groq LLM.
7. **Automated CRM Update:** Updates corresponding rows in Google Sheets (`status`, `reply_sentiment`, `reply_summary`).

---

## 🛠 Tech Stack

- **Workflow Engine:** n8n Cloud
- **Email Gateway:** Gmail API (OAuth2)
- **Database / CRM:** Google Sheets API
- **AI / LLM Engine:** Groq API (`compound-mini`)

---

## ⚙️ Key Technical Features

### 1. Regex Email Extraction
Extracts clean email addresses from RFC-compliant headers (e.g., `John Smith <john@example.com>`):
```javascript
={{ $json.From.match(/<([^>]+)>/)?.[1] || $json.From }}
