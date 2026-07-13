# 🚀 Deployment Guide

This guide describes the deployment process used for this project.

---

## Prerequisites

Before deployment, prepare the following:

- Tencent Cloud Lighthouse VPS
- Ubuntu Server 24.04 LTS
- SSH access
- Hermes Agent installed
- DeepSeek API Key
- Telegram Bot Token (optional)
- WhatsApp integration (optional)

---

# Step 1 - Connect to the VPS

SSH into the server.

```bash
ssh ubuntu@<SERVER_IP>
```

---

# Step 2 - Configure Environment Variables

Navigate to the Hermes configuration directory.

```bash
cd ~/.hermes
nano .env
```

Example configuration:

```env
DEEPSEEK_API_KEY=your-api-key

OPENAI_API_BASE=https://api.deepseek.com
OPENAI_API_KEY=your-api-key
LLM_MODEL=deepseek-chat

TELEGRAM_BOT_TOKEN=xxxxxxxx

TELEGRAM_ALLOWED_USERS=123456789
```

Save the file.

---

# Step 3 - Configure Hermes

Configure the AI provider.

```bash
hermes config set llm.provider deepseek
hermes config set llm.model deepseek-chat
```

---

# Step 4 - Start the Gateway

Launch the Hermes Gateway.

```bash
hermes gateway start
```

Verify the gateway status.

```bash
hermes gateway status
```

---

# Step 5 - Test the AI Agent

Send a message from:

- WhatsApp
- Telegram

Verify that the AI responds correctly.

---

# Useful Commands

Start

```bash
hermes gateway start
```

Stop

```bash
hermes gateway stop
```

Restart

```bash
hermes gateway restart
```

Status

```bash
hermes gateway status
```

---

# Project Directory

```text
~/.hermes
├── .env
├── config.yaml
├── memories/
├── sessions/
├── logs/
├── state.db
└── whatsapp/
```

---

# Troubleshooting

## Unable to connect via SSH

Verify:

- SSH Port (22)
- Firewall Rules
- Username
- SSH Key or Password

---

## Telegram bot does not respond

Check:

- Bot Token
- Allowed User IDs
- Gateway status

---

## WhatsApp not responding

Verify:

- WhatsApp connection
- Hermes Gateway is running
- DeepSeek API key is valid

---

## Verify Gateway

```bash
hermes gateway status
```

If the gateway is not running:

```bash
hermes gateway restart
```

---

# Deployment Completed

The AI Agent is now accessible through:

- WhatsApp
- Telegram

The server will continue running as long as the VPS remains online.