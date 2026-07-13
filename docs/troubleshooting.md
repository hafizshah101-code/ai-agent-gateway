#🧠 Technical Challenges & Solutions

Challenge 1 — SSH Authentication
Problem

PuTTY rejected the configured SSH private key while Windows OpenSSH successfully connected.

Server refused our key
Root Cause

The server rejected the supplied SSH key and fell back to password authentication. Windows OpenSSH automatically attempted password authentication after the public key was rejected, whereas the PuTTY configuration was using an incorrect .ppk key.

Solution
Verified SSH authentication using verbose mode (ssh -v)
Identified authentication order
Confirmed successful password login
Continued administration using Windows OpenSSH
Challenge 2 — Hidden Hermes Configuration
Problem

Hermes configuration files appeared to be missing after connecting to the VPS.

Root Cause

Hermes stores all runtime configuration inside the hidden directory:

~/.hermes

which is not displayed using the default ls command.

Solution

Used:

ls -la

to reveal hidden directories and locate:

.hermes/
├── config.yaml
├── .env
├── memories/
├── logs/
├── sessions/
├── state.db
Challenge 3 — Multi-User Session Isolation
Problem

Running a single AI agent for multiple users raises the risk of conversation history leaking between users.

Solution

Hermes maintains separate session and memory data for each user, allowing multiple WhatsApp and Telegram users to share one AI model while preserving isolated conversation histories.

Challenge 4 — Lightweight AI Deployment
Problem

Deploy an AI assistant on a small cloud instance without requiring GPU resources.

Solution

Optimized deployment using:

2 vCPU
2 GB RAM
DeepSeek API
Hermes Agent
Local SQLite state storage

This architecture enables continuous AI service with minimal infrastructure cost.

Challenge 5 — Secure API Management
Problem

Protect AI provider credentials while supporting multiple services.

Solution

Sensitive configuration is stored in:

~/.hermes/.env

including:

DeepSeek API
Telegram Bot Token
User whitelist
Runtime configuration

No credentials are committed to source control.
