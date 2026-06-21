# ✍️ Content Writer Agent

An AI-powered content generation agent built with **n8n** that automatically writes 
high-quality blog posts, social media captions, and marketing copy — on demand, 
with zero manual writing effort.

---

## 🚀 Features

- 📝 **Generates full blog posts** with structure and flow
- 📱 **Writes social media content** for multiple platforms
- 🧠 **AI understands tone and context** for relevant output
- ⚡ **On-demand generation** — trigger anytime you need content
- 🔄 **Fully automated** — no manual writing needed
- 🎯 **Customizable prompts** — adapt content for any niche or brand

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| n8n | Workflow automation engine |
| Anthropic Claude / Gemini | AI content generation |
| Gmail / Google Docs | Output delivery and storage |

---

## 🔄 How It Works
Trigger Fires (manual or scheduled)

↓

Topic / Prompt Received

↓

Sent to AI Model

↓

AI Generates Full Content

↓

Content Formatted & Structured

↓

Delivered to Output (email / doc / sheet)

---

## ⚙️ Setup & Installation

1. Make sure you have **n8n** running (local or cloud)
2. Import the `content-writer-agent.json` file into your n8n instance
3. Add your **LLM API key** (Anthropic or Gemini) in credentials
4. Configure your preferred **output destination**
5. Customize the **prompt template** to match your brand tone
6. **Activate** the workflow
7. Done — start generating content instantly!

---

## 📁 Project Structure
content-writer-agent/

│

├── content-writer-agent.json   # n8n workflow file (import this)

└── README.md                   # Project documentation

---

## 🧠 AI Integration

The AI layer handles the entire creative process:
- **Understands the topic** and generates relevant, structured content
- **Maintains consistent tone** across blog posts and social captions
- **Adapts writing style** based on the platform (LinkedIn vs Twitter vs blog)
- **Produces ready-to-publish content** with minimal editing needed
- Works with both **Anthropic Claude** and **Google Gemini** interchangeably

---

## ⚡ Challenges & How I Solved Them

### 1. 🔑 API Credit Exhaustion Mid-Development
**Problem:** The Anthropic API key ran out of credits right in the middle of 
testing content generation, which completely halted the workflow.  
**Solution:** Swapped to Google Gemini (free tier via Google AI Studio) as a 
replacement LLM. This also led me to build the AI node in a 
**provider-agnostic way** — making it easy to switch between Claude and Gemini 
without rebuilding the workflow.

### 2. 🎯 Prompt Engineering for Quality Output
**Problem:** Early versions of the agent produced generic, low-quality content 
that felt robotic and lacked structure — not useful for real publishing.  
**Solution:** Iterated heavily on the prompt template, adding clear instructions 
for tone, structure, word count, and formatting. The final prompt instructs the 
AI to write with headings, bullet points, and a natural human tone — dramatically 
improving output quality.

### 3. ⚙️ Trigger Configuration Issues
**Problem:** The "Source for Prompt" setting inside n8n was incorrectly set to 
"Define below" instead of reading from the connected trigger node — meaning the 
AI was receiving empty input and generating nonsense content.  
**Solution:** Corrected the setting to **"Connected Chat Trigger Node"** so the 
AI properly receives the topic input before generating content.

### 4. ⚠️ Rate Limiting on Free Tier
**Problem:** Generating multiple pieces of content back to back hit Gemini's 
free-tier rate limits, causing the workflow to fail silently on bulk runs.  
**Solution:** Added delays between requests inside the workflow and documented 
the limitation. For production use, a paid API tier or a request queue would 
handle bulk generation reliably.

---

## 💡 Use Cases

- Blog post generation for websites
- Social media content calendars
- Marketing copy for campaigns
- Product description writing
- Newsletter content automation

---

## 🙋‍♂️ Author

**Asad** — Software Engineer  
Building AI-powered automation tools for real-world use cases.# content-writer-agent
AI-powered content writer agent built with n8n that automatically generates blog posts and social media content
