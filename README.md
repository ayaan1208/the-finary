# THE FINARY

**Your personal commute newspaper — research → learn → practice → email.**

THE FINARY is a daily automation that builds a newspaper-style briefing (~8–9 pages), renders it to PDF, and emails it each morning.

```
F  Finance
I  Indo-Canada & World
N  Networks / Cloud
A  AWS SAA (chained day-by-day learning)
R  Reliable systems (DSA / System Design)
Y  Yield from AI + skills + vocabulary
```

> Not another news dump. Each edition explains **what happened**, **why it matters to you**, and gives something you can **practice**.

---

## What's in this repo

| Path | Purpose |
|------|---------|
| `finary/send_finary.py` | Unattended HTML → PDF → email delivery |
| `finary/requirements.txt` | WeasyPrint toolchain |
| `docs/AUTOMATION.md` | Full Cursor Automation prompt + setup |
| `docs/PRODUCT.md` | Product idea & positioning (short) |
| `.cursor/environment.json` | Cloud agent install / runtime hints |

---

## Quick start (local)

```bash
# 1) Install PDF renderer
pip install -r finary/requirements.txt

# 2) Dry-run (no secrets required)
python finary/send_finary.py \
  --html path/to/edition.html \
  --to you@example.com \
  --subject "THE FINARY — test" \
  --dry-run
```

### Email secrets (pick one)

| Provider | Env vars |
|----------|----------|
| **Gmail SMTP** (recommended) | `GMAIL_ADDRESS`, `GMAIL_APP_PASSWORD` |
| **Resend** | `RESEND_API_KEY` (optional `RESEND_FROM`) |
| **SendGrid** | `SENDGRID_API_KEY`, `SENDGRID_FROM` |
| **Generic SMTP** | `SMTP_HOST`, `SMTP_PORT`, `SMTP_USERNAME`, `SMTP_PASSWORD`, `SMTP_FROM` |

Then send for real:

```bash
python finary/send_finary.py \
  --html /tmp/finary/finary.html \
  --to ayanpathan012@gmail.com \
  --subject "THE FINARY — $(date +%F)" \
  --body "Your THE FINARY commute edition is attached."
```

---

## Daily automation (Cursor)

1. Open [Cursor Automations](https://cursor.com/automations/new)
2. Name: **THE FINARY**
3. Schedule: `0 8 * * *` (confirm timezone)
4. Point the run at **this repository**
5. Paste instructions from [`docs/AUTOMATION.md`](docs/AUTOMATION.md)
6. Add mail secrets in the environment / secrets panel

The agent writes `/tmp/finary/finary.html`, then runs `send_finary.py` — no interactive OAuth.

---

## What an edition includes

1. **World desk** — India & Canada + geopolitics (plain English)
2. **Finance desk** — one lesson + relevant fintech news
3. **AWS SAA** — one step in a continuing learning chain
4. **DSA / System Design** — lesson + practice prompt
5. **Skills** — practical AI workflow tips
6. **Vocabulary** — 4 words + drill
7. **Professional English** — interview phrases
8. **Wire** — Cloud / DevOps / AI stories that actually teach something

Hard rules: cite sources, no invented facts, skip useless release noise, keep ~8–9 pages.

---

## Product direction

THE FINARY started as a personal commute tool. The longer idea:

> Take what’s happening in the world and turn it into information, learning, and skill development relevant to **you**.

Read → Understand → Learn → Practice → Improve → Repeat

See [`docs/PRODUCT.md`](docs/PRODUCT.md).

---

## Privacy & safety

- Do **not** commit API keys, Gmail app passwords, or `.env` files
- Delivery uses environment secrets only
- Not investment, legal, or immigration advice

---

## Author

**Mohammad Ayankhan Pathan** ([@ayaan1208](https://github.com/ayaan1208))  
Prototype for personal use + early sharing with friends / validators.

---

## License

Private personal project for now. Ask before redistributing.
