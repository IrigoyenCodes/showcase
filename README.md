# Showcase — private AI products, public stories

Case studies for products whose **source stays private**.  
No application code in this repo — narrative, architecture at a high level, metrics, and screenshots.

**Author:** [Santiago Irigoyen](https://github.com/IrigoyenCodes) · [Portfolio](https://portfolio-santiago-theta.vercel.app) · [Profile README](https://github.com/IrigoyenCodes/IrigoyenCodes)

---

## Products

| # | Product | Live | Folder |
| --- | --- | --- | --- |
| 01 | **Atlas** — AI conversational sales for creators | [hyatlas.ai](https://hyatlas.ai) | [`docs/images/atlas/`](docs/images/atlas/) |
| 02 | **Marko** — Instagram-first content OS | [trymarko.com](https://trymarko.com) | [`docs/images/marko/`](docs/images/marko/) |
| 03 | **UDLAP Extractor** — institutional PDF → structured data | [demo](https://udlap-extractor-ti.vercel.app) | [`docs/images/udlap-extractor/`](docs/images/udlap-extractor/) |

---

## 01 · Atlas

<a href="https://hyatlas.ai"><img alt="Atlas placeholder — drop hero screenshot in docs/images/atlas/hero.png" src="docs/images/atlas/hero.png" width="100%" /></a>

**Atlas** clones a creator’s setter on **Instagram and WhatsApp**, with **TikTok as a production DM channel** (ManyChat `tt`): same playbook voice, qualification, follow-ups, booking, and a **full closer CRM** so the sales team can close without digging through chats.

Public results: **$400k+ generated for clients/creators**, plus **$10k+/month** saved on human setter payroll.

### Problem

DM volume outruns human setters. Leads go cold between inbox and calendar; closers inherit names without context, Calendly answers, or a clear path to cash.

### What shipped

**Channels & AI setter**
- **Instagram · WhatsApp** (Meta Business Partner / Graph + WhatsApp Business paths via the messaging stack) and **TikTok DMs** via ManyChat — channel-scoped CTAs, flows, and playbooks  
- Voice / style clone; voice notes & short video where the channel allows (on TikTok, voice notes **degrade to text**)  
- CTA-driven capture with **per-CTA funnel KPIs** (leads → conversation → pitch → won/booked). Comment / follower / outbound triggers remain **Instagram-oriented** — treat TikTok as a **DM channel**, not full IG parity

**Closer CRM · Opportunities**
- Closer CRM: **Agendas / Leads / Cuotas** with attendance, result, and monthly **cash collected** vs billed  
- Creator Opportunities hub: team pipeline + **week/month agenda calendar** (lista also) + Rendimiento  
- Lead ficha: **AI psych summary** on demand (desire / pain / friction / key quote), then persisted  
- **Calendly invitee questions** on the ficha when the creator enables them (Atlas form answers preferred when present)  
- **Full conversation transcript** on the opportunity ficha (inbox has last-message snippets separately)  
- On win: **close amount**, payment type (upfront / reservation / installments), **recording URL**, and **cuotas** with paid/pending tracking

**Analytics for creators**
- Funnel dashboard (response → qualify → pitch → book → show → close) + booking rate / cash  
- **Pain themes**: AI classifies conversations into a pain taxonomy and ranks **Dolores más comunes** on Performance (also via MCP `get_pain_themes`)  
- **Per-CTA** metrics and period exports — not native social `post_id` media KPIs (a Comment CTA is the practical proxy for a post/reel)

**Ops stack (high level)**
- Postgres + **Redis** + **Celery** workers/queues for webhooks and LLM jobs  
- Multi-provider LLM routing  
- **Atlas Creator MCP** — read-only Claude Cloud/Desktop connector (`mcp.hyatlas.ai`) for creators to inspect KPIs, pains, CTAs, and playbook without opening the panel  

### Results (public)

| Metric | Value |
| --- | --- |
| Generated for clients / creators | **$400k+** |
| Setter payroll saved | **$10k+/month** (reported) |
| Channels | Instagram · WhatsApp · TikTok DMs (ManyChat) |
| Live | [hyatlas.ai](https://hyatlas.ai) |

### Stack (high level)

`Django` · `Postgres` · `Redis` · `Celery` · Meta / WhatsApp / TikTok messaging · multi-LLM agents · `Atlas Creator MCP` (FastMCP) · product UI on the Atlas app  

### Screenshots

Drop files into `docs/images/atlas/` (suggested names):

| File | Shot |
| --- | --- |
| `hero.png` | Landing or product hero |
| `dashboard.png` | Funnel dashboard |
| `conversations.png` | Inbox + lead ficha |
| `opportunities.png` | Opportunities · agenda / summary / Calendly |
| `closer-crm.png` | Closer CRM · cuotas / cash |
| `analytics-pains.png` | Pain themes ranking |
| `ctas.png` | Per-CTA / post KPIs |

```markdown
![Dashboard](docs/images/atlas/dashboard.png)
![Opportunities](docs/images/atlas/opportunities.png)
![Closer CRM](docs/images/atlas/closer-crm.png)
![Pain themes](docs/images/atlas/analytics-pains.png)
```

---

## 02 · Marko

<a href="https://trymarko.com"><img alt="Marko placeholder — drop hero screenshot in docs/images/marko/hero.png" src="docs/images/marko/hero.png" width="100%" /></a>

**Marko** is the **Instagram command center** for creators: inspiration vault, voice-aware scripts & captions, calendar, native publish (photo / Reel / carousel), analytics, stories drop-off, and competitor signals — instead of Notion + Docs + ChatGPT + Insights.

### Honest scope

- **Today:** Instagram publish + insights; TikTok trends in Discover; Marko AI with account context when IG is connected  
- **Next:** publish to TikTok / YouTube / LinkedIn; Meta ads metrics  

### What shipped

- Vault + format templates + Discover  
- Voice profile → scripts / captions  
- Composer with real preview + schedule/publish via Instagram Graph  
- Analytics: engagement, best hours, post ranking, stories sessions  

### Stack (high level)

`Next.js 15` · `Supabase` (Auth, Postgres, RLS, storage) · `Instagram Graph` · Framer Motion  

### Screenshots

| File | Shot |
| --- | --- |
| `hero.png` | Marketing or app hero |
| `analytics.png` | Analytics panel |
| `calendar.png` | Editorial calendar |
| `composer.png` | Post composer / preview |
| `scripts.png` | Scripts / voice profile |

```markdown
![Analytics](docs/images/marko/analytics.png)
![Calendar](docs/images/marko/calendar.png)
![Composer](docs/images/marko/composer.png)
```

---

## 03 · UDLAP Document Extractor

<img alt="Extractor placeholder — docs/images/udlap-extractor/hero.png" src="docs/images/udlap-extractor/hero.png" width="100%" />

Internal tool for UDLAP IT: **PDF / scan → vision-LLM extraction → Excel / ZIP**, cutting manual processing time (~80% reported). Public demo: [udlap-extractor-ti.vercel.app](https://udlap-extractor-ti.vercel.app)

**Stack:** React · TypeScript · OpenRouter / vision models · Vercel  

---

## Adding your images

1. Export PNGs/WebPs from the product (no PII / real lead chats — blur names).  
2. Place them under `docs/images/<product>/` using the names above.  
3. Uncomment or keep the markdown image lines — GitHub will render them on this README.  

Until images land, broken-image icons are expected; the copy and structure are ready.

---

## License / IP

Product source code is **not** published here.  
All product rights remain with their owners (HYATLAS / Marko / UDLAP tooling as applicable).  
This repository is documentation-only.
