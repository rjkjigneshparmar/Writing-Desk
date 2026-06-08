# The Writing Desk ✦

> Your personal AI-powered writing assistant — built with Electron, React, and your choice of AI provider.

![Version](https://img.shields.io/badge/version-4.0.0-black)
![Platform](https://img.shields.io/badge/platform-Windows%20%7C%20Mac-black)
![License](https://img.shields.io/badge/license-MIT-black)
![Providers](https://img.shields.io/badge/AI-Anthropic%20%7C%20OpenAI%20%7C%20Google-black)

---

## What is it?

The Writing Desk is a desktop app that acts as your personal editor. Paste any text, pick a mode, and get back a polished, improved version — with specific suggestions explaining every change.

It works with **Anthropic (Claude)**, **OpenAI (GPT)**, and **Google Gemini**. You bring your own API key. Everything runs locally on your machine.

---

## Features

| Mode | What it does |
|---|---|
| **✓ Check** | Grammar, spelling, punctuation, clarity — with tone control |
| **↻ Rewrite** | Shorter, longer, more confident, simpler, and more |
| **✉ Email** | Polish drafts tuned to your recipient (boss, client, colleague, friend) |
| **⇆ Translate** | Any language → polished English (Hindi, Gujarati, Spanish, French, German) |
| **◎ Social** | Optimised for Twitter, LinkedIn, Instagram, SMS with character limits |

**Other highlights:**
- Side-by-side Original vs Polished comparison
- Annotated suggestions with type labels (spelling, grammar, clarity, tone)
- 2 alternative versions for every result
- Copy & Apply buttons
- Dark / light mode
- Supports 3 AI providers — switch anytime from Settings
- API keys stored locally, never shared

---

## Screenshots

> <img width="1116" height="942" alt="image" src="https://github.com/user-attachments/assets/e155b003-1a31-45f9-b5b5-7a601b702245" />


---

## Getting Started

### Prerequisites

- [Node.js](https://nodejs.org) v18 or newer
- An API key from one of the supported providers (see below)

### Installation

```bash
# Clone the repository
git clone https://github.com/rjkjigneshparmar/writing-desk.git
cd writing-desk

# Install dependencies
npm install --legacy-peer-deps

# Run in development mode
npm run dev
```

### Adding your API Key

1. Open the app
2. Click the **⚙ gear icon** in the top-right corner
3. Select your AI provider
4. Select a model
5. Paste your API key
6. Click **Save Settings** → **Test Connection**
7. Click **← Back** to start using the app

---

## Supported AI Providers

| Provider | Models | Pricing | Get a Key |
|---|---|---|---|
| **Anthropic** | Claude Sonnet 4, Haiku 4.5, Opus 4.6 | ~$0.003 / request | [console.anthropic.com](https://console.anthropic.com) |
| **OpenAI** | GPT-4o, GPT-4o Mini, GPT-4 Turbo | ~$0.001–0.01 / request | [platform.openai.com](https://platform.openai.com) |
| **Google Gemini** | Gemini 2.0 Flash, 2.0 Flash Lite, 1.5 Pro | Free tier available | [aistudio.google.com](https://aistudio.google.com) |

> **Tip:** Start with Google Gemini — it has a free tier so you can try the app at zero cost.

---

## Building the Installer

### Windows (.exe)
```bash
npm run dist:win
```

### Mac (.dmg)
```bash
npm run dist:mac
```

Output is saved to the `release/` folder.

> **Note:** The build skips code signing by default (`CSC_IDENTITY_AUTO_DISCOVERY=false`). Windows may show a SmartScreen warning on first launch — click **More info → Run anyway**.

---

## Project Structure

```
writing-desk/
├── electron/
│   ├── main.js          # Main process — window, API proxy, key storage
│   └── preload.js       # Secure IPC bridge to renderer
├── src/
│   ├── main.jsx         # React entry point
│   └── App.jsx          # Full UI — Writing Desk + Settings page
├── public/              # App icons (optional)
├── index.html           # HTML entry point
├── vite.config.js       # Vite configuration
└── package.json         # Scripts and dependencies
```

---

## How it Works

- **Frontend:** React + Vite, served by Electron's BrowserWindow
- **API calls:** Proxied through Electron's main process via `net.request` (no CORS issues, API key never exposed to renderer)
- **Key storage:** Saved to OS user data folder (`config.json`) via Node.js `fs` — never leaves your machine except for API calls
- **IPC bridge:** `preload.js` exposes `getSettings`, `saveSettings`, and `callClaude` via `contextBridge`

---

## Tech Stack

- [Electron](https://electronjs.org) — desktop wrapper
- [React 18](https://react.dev) — UI framework
- [Vite 5](https://vitejs.dev) — build tool
- [electron-builder](https://www.electron.build) — packaging and installer

---

## Development Scripts

| Command | Description |
|---|---|
| `npm run dev` | Run in development mode (hot reload) |
| `npm run build` | Build the React app for production |
| `npm run dist:win` | Build Windows installer (.exe) |
| `npm run dist:mac` | Build Mac installer (.dmg) |
| `npm run dist:both` | Build both platforms |

---

## Contributing

Contributions, issues, and feature requests are welcome. Feel free to open a pull request or file an issue.

---

## License

MIT © [Jignesh Parmar](https://github.com/rjkjigneshparmar)

---

<div align="center">
  <sub>Built with ❤ using Claude AI &nbsp;·&nbsp; The Writing Desk v4.0</sub>
</div>
