# Project Aegis (Auto-Mod Bot) 🛡️

> **Privacy-Preserving Edge AI & High-Concurrency Threat Detection for Real-Time Platforms**

A Rust-based Discord Antinuke and Automod system featuring Redis-backed rate limiting and a hybrid local AI defense layer for phishing and social-engineering detection.

## 📖 Overview

Traditional security bots rely purely on deterministic rules (regex and blacklists). Malicious actors can bypass these using obfuscated text, phishing links, and social engineering. Standard Node.js or Python bots can also become constrained during high-volume event bursts.

**Project Aegis** addresses these problems with a two-tier moderation architecture built on Rust and the Twilight ecosystem:

1. **Layer 1 (The Shield):** A non-blocking engine using a Redis token-bucket algorithm via atomic pipelines. It tracks state changes across distributed shards, mitigates rogue permissions, and blocks known bad patterns.
2. **Layer 2 (The Brain):** Complex or novel payloads are routed asynchronously to an edge AI microservice using local DeepSeek/Ollama. User data stays outside third-party hosted AI APIs.

## 🚀 Key Features

- Redis pipeline-backed token-bucket rate limiting
- Non-blocking Tokio tasks for asynchronous AI analysis
- Local-first inference for privacy-preserving moderation
- Memory-safe Rust implementation
- Load-testing support for high-volume event scenarios

## 🛠️ Technology Stack

- **Core Engine:** Rust (Edition 2021)
- **Async Runtime:** Tokio
- **Discord Gateway & HTTP:** Twilight (`twilight-rs`)
- **State & Rate Limiting:** Redis (`redis-rs`)
- **Long-term Storage:** PostgreSQL (Supabase / `sqlx`)
- **AI Microservice:** Local Ollama (`deepseek-r1`)

## ⚙️ Installation & Setup

### Prerequisites

1. [Rust](https://www.rust-lang.org/tools/install) installed (`cargo`).
2. A running [Redis](https://redis.io/) instance.
3. A [Supabase](https://supabase.com/) PostgreSQL database.
4. [Ollama](https://ollama.com/) running locally or over a secure tunnel.

### Configuration

1. Clone the repository:
   ```bash
   git clone https://github.com/Himadryy/auto-mod-bot.git
   cd auto-mod-bot
   ```
2. Create a `.env` file in the root directory based on `.env.example`:
   ```env
   DISCORD_TOKEN=your_bot_token_here
   REDIS_URL=redis://...
   DATABASE_URL=postgresql://...
   OLLAMA_URL=http://localhost:11434
   OLLAMA_MODEL=deepseek-r1:8b
   ```
3. Run the bot:
   ```bash
   cargo run --release
   ```

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
