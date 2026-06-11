# ✍️ Humanizer — Write Like Yourself

A premium, local-first, privacy-respecting AI text humanization workspace. Train a custom style profile on your own writing samples or use advanced style presets to bypass AI detectors (Turnitin, GPTZero, etc.) in real-time.

![License](https://img.shields.io/badge/license-MIT-blue)
![Stack](https://img.shields.io/badge/stack-HTML%20%7C%20CSS%20%7C%20Vanilla%20JS-brightgreen)
![Privacy](https://img.shields.io/badge/privacy-100%25%20Local-emerald)

---

## ✨ Key Features

- **🎯 Custom Style Profile Training:**
  - Paste your writing samples (emails, messages, notes) to automatically extract your unique writing characteristics:
    - **Burstiness** (variation in sentence lengths).
    - **Contraction Rate** (casualness indicators).
    - **Vocabulary & Punctuation Style** (use of em-dashes, semicolons, ellipses).
    - **First-Person voice** and natural hedges.
- **⚡ Real-time Multi-Provider Streaming:**
  - Streams responses token-by-token for all major models:
    - **Anthropic:** Claude 3.5 Sonnet, Claude 3.7 Sonnet, Claude 3.5 Haiku.
    - **OpenAI:** GPT-4o, GPT-4o-mini, o1-mini.
    - **Google Gemini:** Gemini 2.5 Flash, Gemini 1.5 Pro, etc., utilizing a custom client-side SSE/REST stream reader.
- **🔄 Interactive Word-Level Diffing:**
  - See exactly how the text changed in real-time using a custom Longest Common Subsequence (LCS) word-level diff. 
  - Highlights added words in soft green and deleted words in red strikethrough.
- **🎭 Context-Aware Style Presets:**
  - Don't have writing samples ready? Instantly switch between targeted style profiles:
    - **Casual / Conversational** (friendly, low-key, contractions, natural pacing).
    - **Professional / SaaS** (clear, active voice, concise, polite authority).
    - **Academic / Formal** (highly structured, descriptive, objective, no contractions).
    - **Creative / Storyteller** (vivid imagery, rhythmic sentence structures).
- **📊 AI Detection Probability Estimator:**
  - Evaluates the output's naturalness, burstiness uniformity, and contraction metrics, scanning for common "AI tells" (e.g., transition words like *moreover*, *furthermore*, *delve*).
  - Displays a live prediction dashboard containing: **Human Score %**, **Perplexity Level**, and **AI Likelihood**.
- **🔒 Privacy First & Offline Capable:**
  - Serverless structure: Your API keys and writing samples are stored strictly inside your browser's local sandbox (`localStorage`) and never sent to any backend servers besides the direct LLM endpoints.

---

## 🚀 Getting Started

Since **Humanizer** is built using vanilla web technologies, there is **no installation, Node.js server, or compilation required**.

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/SyncAlly/Humanizer.git
   cd Humanizer
   ```

2. **Open the Application:**
   - Double-click `index.html` to open it in your browser of choice.
   - Alternatively, serve it using any local static server:
     ```bash
     npx serve .
     # or
     python -m http.server 8000
     ```

3. **Configure Your API Key:**
   - Go to the **Setup** tab.
   - Choose your provider (Anthropic, OpenAI, or Google Gemini).
   - Paste your API key (obtained from the respective developer console).
   - Check **"Save API key locally"** to persist your key across page refreshes.
   - Click **Test Connection** to verify.

4. **Train & Humanize:**
   - Paste 3–10 samples of your writing in the training block and click **Add Sample**.
   - Click **Build Profile** to extract your style metrics.
   - Navigate to the **Humanize** tab, paste the AI-generated text, select a strength/preset, and click **Humanize**.

---

## 🛠️ Architecture

Humanizer is compiled into a single, highly-optimized file:

```
Humanizer/
├── index.html        # Contains structure, glassmorphic layout, and core app logic
└── README.md         # Documentation
```

### Technical Highlights
- **Dynamic Diffing:** Features a custom client-side Longest Common Subsequence (LCS) matrix comparison to identify word differences between input and output.
- **Gemini Streaming:** Implements a custom character brace-counting parser to decode Google's chunked JSON array stream responses.
- **Responsive Layout:** Adaptive CSS flexbox/grid designed for smooth usage on both ultra-wide screens and mobile devices.

---

## 🔒 Security & Keys

Your keys are stored in the browser's `localStorage` namespace under the key `humanizer_state`. They are transmitted directly to:
- `api.anthropic.com`
- `api.openai.com`
- `generativelanguage.googleapis.com`

No third-party logging or proxy backend is used.

---

## 📄 License

This project is licensed under the MIT License.
