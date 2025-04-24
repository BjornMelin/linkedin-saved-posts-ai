# LinkedIn Saved Posts AI

![Vercel](https://img.shields.io/badge/Deploy-Vercel-black?logo=vercel)
![Supabase](https://img.shields.io/badge/Powered_by-Supabase-3ECF8E?logo=supabase)
![MIT License](https://img.shields.io/badge/License-MIT-green)

Scrape, classify & chat over your **LinkedIn Saved Posts** using Supabase + pgvector, Vercel Edge Functions, Playwright MCP, Firecrawl MCP, and OpenRouter LLMs.

## ✨ Features

- **One-time bootstrap** scrape of every saved post (≈ 400 posts)
- **Daily incremental sync** via Vercel cron (stops on first duplicate)
- Rigid **Topic → Category → Subcategory** taxonomy for clean filtering
- Fast **vector & full-text search** (pgvector + Postgres)
- **Chat assistant** with switchable models: `o4-mini-high`, `o4-mini`, `gpt-4.1`, `gemini-2.5-flash`
- **Firecrawl enrichment** for external links (optional)
- Cursor AI rule-files for structured, SOLID, KISS code generation

## 🏗 Stack

| Layer     | Tech                                                                                  |
| --------- | ------------------------------------------------------------------------------------- |
| Front-end | Next.js (App Router), Tailwind, shadcn/ui                                             |
| Back-end  | Vercel Edge Functions + Playwright MCP                                                |
| Database  | Supabase Postgres + pgvector                                                          |
| AI / LLM  | OpenRouter (OpenAI & Gemini models)                                                   |
| Agents    | MCP Servers (playwright, firecrawl, tavily, git, github, sequential-thinking, memory) |

## 🚀 Quick Start

```bash
git clone https://github.com/BjornMelin/linkedin-saved-posts-ai.git
cd linkedin-saved-posts-ai
cp .env.example .env.local     # add your keys + LinkedIn li_at cookie
pnpm install
pnpm dev                       # local Next.js + Supabase
```

Then open <http://localhost:3000> and log in with Supabase Email-Link Auth.

## 🛡 Security Notes

Secrets stay only in Vercel’s encrypted env-store — never commit them.  
GitHub secret-scanning is active for public repos. If a secret leaks, rotate immediately.

## 📄 License

[MIT](LICENSE.md)
