# NEXUS — Personal File Server
> by **Nikkil Prithivn**

A personal Iron Man-style file server built with pure Python. Access, upload, download and manage your Mac's files from any browser — on your phone, laptop, or anywhere in the world.

![Python](https://img.shields.io/badge/Python-3.9+-blue?style=flat-square&logo=python)
![Zero Dependencies](https://img.shields.io/badge/dependencies-zero-green?style=flat-square)
![macOS](https://img.shields.io/badge/platform-macOS-lightgrey?style=flat-square&logo=apple)
![License](https://img.shields.io/badge/license-MIT-blue?style=flat-square)

---

## What is NEXUS?

NEXUS turns your Mac into a personal file server you can access from anywhere. No cloud, no subscription, no third-party storing your files. Everything runs on your machine and only you have access.

Think of it as your own private Google Drive — but running on your Mac, built from scratch.

---

## Features

| Feature | Details |
|---|---|
| 🌐 **Internet access** | Built-in SSH tunnel via serveo.net — zero install |
| 🔍 **Search** | Search across all your files instantly |
| ⬆ **Upload** | Drag and drop files from any device |
| ⬇ **Download** | Download any file or folder as ZIP |
| 👁 **Preview** | Images, code, and text preview in-browser |
| 🔗 **Share links** | Generate temporary public links for single files |
| ✎ **Rename** | Rename files and folders inline |
| 📁 **New folder** | Create directories from the browser |
| 🗑 **Delete** | Delete files and folders with confirmation |
| 🔒 **Auth** | Password-protected with HMAC-signed session tokens |
| 📊 **Vitals** | Live disk usage, session count, uptime |
| 🌙 **Stark UI** | Dark blue-grey futuristic interface |

---

## Requirements

- macOS (uses built-in SSH for tunnel)
- Python 3.9 or higher
- Nothing else — zero pip installs

---

## Quick Start

```bash
# 1. Clone the repo
git clone https://github.com/yourusername/nexus.git
cd nexus

# 2. Run it
bash start.sh

# 3. Open in browser
# http://localhost:8080

```



## Tailscale (recommended for daily use)

For a permanent private URL that never changes and requires no tunnel command:

1. Install [Tailscale](https://tailscale.com) on your Mac and phone
2. Sign in with the same account on both
3. Your Mac gets a permanent IP like `100.x.x.x`
4. Run `bash start.sh` and open `http://100.x.x.x:8080` from anywhere


## Keyboard Shortcuts

| Key | Action |
|---|---|
| `F2` | Rename selected file |
| `Delete` | Delete selected file |
| `Enter` | Download selected file |
| `Cmd + F` | Focus search |
| `Escape` | Close any modal |

---

## Share Links

Generate a temporary public link for any file:

1. Select a file
2. Click **🔗 Share** in the preview panel
3. Copy the link — share it with anyone
4. Link expires in **6 hours**
5. No password needed to access a share link

---

## Security Notes

- **Always change the default password** before exposing to the internet
- Share links are public — anyone with the URL can download that file
- The server runs over HTTP by default — Serveo and localhost.run provide HTTPS at the tunnel level
- Session tokens expire after 24 hours
- Path traversal attacks are blocked — users cannot escape the served directory

---

## API Reference

| Endpoint | Method | Auth | Description |
|---|---|---|---|
| `/api/login` | POST | — | Get session token |
| `/api/status` | GET | ✓ | Server stats + disk info |
| `/api/ls` | GET | ✓ | List directory |
| `/api/get` | GET | ✓ | Download file |
| `/api/preview` | GET | ✓ | Preview file (inline) |
| `/api/zip` | GET | ✓ | Download folder as ZIP |
| `/api/search` | GET | ✓ | Search files |
| `/api/upload` | POST | ✓ | Upload file |
| `/api/delete` | POST | ✓ | Delete file or folder |
| `/api/rename` | POST | ✓ | Rename file or folder |
| `/api/mkdir` | POST | ✓ | Create directory |
| `/api/share` | POST | ✓ | Generate share link |

---

## Built With

- **Python stdlib only** — `http.server`, `pathlib`, `hmac`, `hashlib`, `zipfile`, `subprocess`
- **No frameworks** — no Flask, no FastAPI, no Django
- **No npm** — no Node.js, no build step
- **Orbitron + Rajdhani + Share Tech Mono** — Google Fonts for the HUD aesthetic

---

## License

MIT — do whatever you want with it.

---

<div align="center">
  <strong>NEXUS</strong> · built by Nikkil Prithivn
</div>
