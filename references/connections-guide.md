# Connections Guide — MCP vs API

How to wire your tools. Two paths. Pick based on how often you use the tool and how much token efficiency matters to you.

---

## The trade-off

| | MCP | API (.env + script) |
|---|---|---|
| **Setup time** | Minutes | 30-60 min per tool |
| **Token cost** | Higher — tool descriptions load every session | Lower — you fetch only what you need |
| **Control** | Limited — what the MCP exposes | Full — any endpoint, any data shape |
| **Maintenance** | Managed by the vendor | Yours to maintain |
| **Best for** | Testing, infrequent use | Daily-use tools, token-sensitive workflows |

**Rule of thumb:** Start with MCP. Switch to API when a tool becomes part of your daily workflow and you notice the token overhead.

---

## Path A — MCP (fast start)

1. Find the MCP for your tool (most major tools have one — check the tool's docs or `claude mcp add --search {tool}`)
2. Run: `claude mcp add {tool-name}`
3. Restart Claude Code
4. Update `connections.md` — set mechanism to `mcp`

No API key needed. Auth handled by Claude's OAuth where available.

---

## Path B — API key + script (token-efficient)

1. Get your API key from the tool's dashboard (see `references/{tool}-api.md` for exact steps)
2. Copy `.env.example` to `.env` and paste the key
3. Write a script in `scripts/{tool}_fetch.py` that pulls what you need
4. Save endpoint docs to `references/{tool}-api.md` — research once, reuse forever
5. Update `connections.md` — set mechanism to `key+ref`

Your `.env` is gitignored — keys never leave your machine.

---

## Which tools to connect first

Priority order based on leverage:

1. **Revenue tracking** (Stripe, your CRM) — highest ROI, directly tied to money
2. **Email** (Gmail, Outlook) — highest daily volume, most automatable
3. **Calendar** — scheduling intelligence, meeting prep
4. **Task tracker** (Notion, ClickUp) — closes the loop between OS and execution
5. **Meeting intelligence** (Fathom, Granola) — turns calls into structured data
6. **Knowledge/files** — lowest urgency, highest friction to set up

Don't connect everything on Day 1. Pick one, wire it properly, use it for a week. Then connect the next.

---

## The .env file

```bash
# Copy the template
cp .env.example .env

# Open and fill in your keys
open .env
```

Never commit `.env` — it's in `.gitignore`. Share `.env.example` (with placeholders) if you ever share this repo.
