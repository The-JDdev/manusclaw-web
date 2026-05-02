<div align="center">

<h1>🌐 manusclaw-web</h1>

<p><strong>The official Web UI for <a href="https://github.com/The-JDdev/ManusClaw">ManusClaw</a> — connect your browser to a local or remote autonomous AI agent.</strong></p>

<p><em>By <a href="https://github.com/The-JDdev">The-JDdev (SHS Shobuj)</a> — JD Lab</em></p>

[![ManusClaw](https://img.shields.io/badge/backend-ManusClaw%20v3-58a6ff?logo=github)](https://github.com/The-JDdev/ManusClaw)
[![License](https://img.shields.io/badge/license-MIT-green)](LICENSE)
[![No Build](https://img.shields.io/badge/build-none%20required-brightgreen)](index.html)
[![CORS](https://img.shields.io/badge/CORS-all%20origins-orange)](https://github.com/The-JDdev/ManusClaw/blob/main/app/server/main.py)

</div>

---

## What is this?

**manusclaw-web** is a zero-build-step HTML/JS/Tailwind web interface that connects to a [ManusClaw v3](https://github.com/The-JDdev/ManusClaw) WebSocket server.

It provides:
- **Chat interface** — send prompts to the agent, see streaming output in real time
- **Tool call log** — right panel shows every tool call, status, and output
- **Tool Intelligence scores** — live confidence bar chart for each tool
- **Session history** — left panel lists all prior sessions with step counts
- **Session replay** — click any session to replay its messages and tool calls
- **Multi-agent toggle** — switch between single-agent and PM→Arch→Eng→QA pipeline
- **Build/Plan mode** — toggle autonomous vs. confirmation-gated execution

---

## Quick Start

```bash
# Clone
git clone https://github.com/The-JDdev/manusclaw-web.git
cd manusclaw-web

# Open (no build step — pure HTML)
open index.html
# or: python -m http.server 3000 && open http://localhost:3000
```

Then:
1. Start your ManusClaw server: `python run_server.py --port 8765`
2. In the UI: set Server URL to `ws://localhost:8765`
3. Click **Connect** → enter a prompt → click **▶ Run**

---

## Remote / Cross-Origin Usage

Since the ManusClaw server enables **full CORS (allow all origins)**, this UI works from:

| Hosting | Backend |
|---|---|
| GitHub Pages | Local PC running `run_server.py` |
| Vercel | Remote VPS |
| Termux browser | Same-device Termux `run_server.py` |
| Any CDN | Any reachable WebSocket URL |

```
# Example: serve UI on GitHub Pages, backend on Termux
UI URL:     https://The-JDdev.github.io/manusclaw-web
Server URL: ws://192.168.1.x:8765   ← your phone's local IP on WiFi
```

---

## WebSocket Events

The UI handles these events from the ManusClaw server:

| Event | Description |
|---|---|
| `connected` | Server ready |
| `agent_start` | Agent began execution |
| `step_start` | A new PAORR step started |
| `step_output` | Step produced output |
| `agent_done` | Agent finished successfully |
| `agent_error` | Agent encountered an unrecoverable error |

---

## Stack

- Pure HTML5 + Vanilla JS — no npm, no build step, no dependencies to install
- [Tailwind CSS](https://tailwindcss.com/) via CDN
- [JetBrains Mono](https://fonts.google.com/specimen/JetBrains+Mono) via Google Fonts
- WebSocket + Fetch API (native browser APIs)

---

## License

MIT — see [LICENSE](LICENSE).

---

## Support

If ManusClaw or manusclaw-web is useful to you, please star ⭐ the repos and consider [donating](https://github.com/The-JDdev/ManusClaw#-support-the-vision).

*— The-JDdev (SHS Shobuj) · JD Lab*
