# 🤖 AI Knowledge Base Chat
 
A lightweight, single-file AI chat app that lets you instantly turn any document, SOP, FAQ, or company content into an interactive chatbot — powered by Claude (Anthropic).
 
No frameworks. No backend. No deployment complexity. One `.html` file.
 
![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)
![HTML](https://img.shields.io/badge/Built%20With-HTML%2FJS-orange)
![Claude](https://img.shields.io/badge/Powered%20By-Claude%20API-6C63FF)
 
---
 
## ✨ Features
 
- **Instant setup** — paste any content, name your knowledge base, start chatting in seconds
- **Strictly grounded answers** — Claude only responds using the content you provide; it won't hallucinate or go off-script
- **Full conversation memory** — each message is sent with the full chat history so Claude maintains context
- **Clean chat UI** — iMessage-style bubbles, user on right, AI on left, animated typing indicator
- **Branded header** — displays your knowledge base name like a dedicated bot
- **Source attribution** — every AI response shows a "Source: [KB Name]" tag
- **Graceful errors** — friendly messages for bad API keys, rate limits, or network issues
- **Zero dependencies** — pure HTML, CSS, and vanilla JavaScript; no npm, no build tools
- **Mobile-friendly** — responsive layout works on any screen size
- **Optional hardcoded API key** — pre-fill the key for client demos
 
---
 
## 📸 Screenshots
 
> **Setup Screen** — paste your content and API key to get started
 
> **Chat Interface** — ask questions; Claude answers only from your source
 
*(Add your own screenshots here after deploying)*
 
---
 
## 🚀 Quick Start
 
### Option A — Run locally (fastest)
1. Download `ai-knowledge-base-chat.html`
2. Open it in any browser (Chrome, Firefox, Safari, Edge)
3. Enter your [Anthropic API key](https://console.anthropic.com/)
4. Paste your content and start chatting
 
### Option B — Host on GitHub Pages (shareable link)
1. Fork or upload this repo to your GitHub account
2. Go to **Settings → Pages → Deploy from branch (main)**
3. Your app will be live at:
   ```
   https://carson-emenecker.github.io/ai-knowledge-base-chat/ai-knowledge-base-chat.html
   ```
 
### Option C — Host anywhere static
Drop the HTML file on any static host:
- [Netlify Drop](https://app.netlify.com/drop) — drag and drop, live in 30 seconds
- [Vercel](https://vercel.com) — free static hosting
- Any web server, S3 bucket, or CDN
 
---
 
## 🔑 API Key Setup
 
You need an Anthropic API key to use this app.
 
1. Sign up at [console.anthropic.com](https://console.anthropic.com/)
2. Go to **API Keys → Create Key**
3. Copy the key (starts with `sk-ant-api03-...`)
 
The key is entered in the setup screen and **stored in memory only** — it is never saved to disk, localStorage, or sent anywhere other than Anthropic's API.
 
### Hardcoding the API key (for client demos)
 
To pre-fill and hide the API key field, open the HTML file and find this line near the top of the `<script>` block:
 
```js
const HARDCODED_API_KEY = '';
```
 
Replace it with your key:
 
```js
const HARDCODED_API_KEY = 'sk-ant-api03-...';
```
 
> ⚠️ **Warning:** Only hardcode your key in files shared with trusted users. Anyone who can view the HTML source will see the key. For public deployments, always use the input field.
 
---
 
## 💡 Use Cases
 
| Use Case | What to Paste |
|---|---|
| Customer support bot | Product docs, FAQs, return policies |
| Internal HR assistant | Employee handbook, onboarding SOPs |
| Sales enablement tool | Product specs, pricing, competitive FAQs |
| Legal/compliance Q&A | Policy documents, contracts, guidelines |
| Knowledge base demo | Any structured text content |
| Client onboarding | Service agreements, process documents |
 
---
 
## 🏗️ How It Works
 
```
User pastes content
        │
        ▼
Content injected into Claude system prompt
        │
        ▼
User asks a question
        │
        ▼
Full message history sent to Anthropic API (/v1/messages)
        │
        ▼
Claude answers strictly from the provided content
        │
        ▼
Response displayed in chat UI
```
 
The system prompt instructs Claude to:
- Only answer from the pasted knowledge base content
- Explicitly say when information is not available in the source
- Never fabricate or infer beyond what's provided
 
---
 
## 🛠️ Customization
 
Everything is in one file — open it in any text editor.
 
| What to change | Where to find it |
|---|---|
| Accent color | `--accent: #5b5ef4` in `:root` CSS variables |
| AI model | `model: 'claude-opus-4-5'` in the `sendMessage()` function |
| Max response length | `max_tokens: 1024` in the fetch body |
| System prompt behavior | `buildSystemPrompt()` function |
| App title/branding | `<title>` tag and `.setup-header h1` |
| Default KB name placeholder | `placeholder` on `#kb-name` input |
 
---
 
## ⚙️ Technical Details
 
- **Model:** Claude claude-opus-4-5 (Anthropic)
- **API:** `https://api.anthropic.com/v1/messages`
- **Auth:** API key via `x-api-key` header
- **Context:** Full conversation history passed on every request
- **No backend:** API called directly from the browser using `fetch()`
- **No storage:** All state lives in JavaScript memory; cleared on refresh
 
---
 
## 📋 Requirements
 
- A modern web browser (Chrome 90+, Firefox 88+, Safari 14+, Edge 90+)
- An [Anthropic API key](https://console.anthropic.com/) with available credits
- Internet connection (for API calls)
 
---
 
## 🔒 Privacy & Security
 
- Your API key is never stored — it lives in memory for the duration of the browser session
- Your knowledge base content never leaves your browser except as part of API calls to Anthropic
- No analytics, no tracking, no third-party scripts
- Review [Anthropic's privacy policy](https://www.anthropic.com/privacy) for how your API data is handled
 
---
 
## 📄 License
 
MIT License — free to use, modify, and sell. Attribution appreciated but not required.
 
---
 
## 🤝 Contributing
 
Pull requests welcome. For major changes, open an issue first to discuss what you'd like to change.
 
---
 
## 🙋 FAQ
 
**Can I use this commercially?**
Yes. MIT license — build it into products, sell it to clients, white-label it.
 
**Does this work with large documents?**
Yes, up to Claude's context window (~200k tokens for claude-opus-4-5). For very large content, consider summarizing or chunking your source material.
 
**Why does it sometimes say it doesn't know something that's in my content?**
The content may be ambiguously worded or the question may use different terminology. Try rephrasing or being more specific.
 
**Can I add multiple knowledge bases?**
Not in the current version. Each session supports one knowledge base. Hit "New KB" to load different content.
 
**Is this production-ready?**
It's a single-file prototype — great for demos, internal tools, and MVPs. For production use with multiple users, you'd want a backend to protect your API key.
 
---
 
*Built with [Claude API](https://www.anthropic.com/api) by Anthropic*
 
