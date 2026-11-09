# FileSentinel — Website Sensitive File Access Blocker (Cloudflare)

**FileSentinel** is a complete, production-ready **Cloudflare WAF custom rule pack** that blocks probes for sensitive and hidden files (`.env`, backups, dumps, Git metadata, config leaks) — **without breaking public HTML/PHP pages**.

| | |
|---|---|
| **Product** | FileSentinel |
| **Author** | Imran Ahmed |
| **License** | MIT |
| **Demo site** | [`index.html`](./index.html) |
| **Rule pack** | [`rules/cloudflare-custom-rule.txt`](./rules/cloudflare-custom-rule.txt) |
| **Support / future work** | [imrandev.bd/contact](https://imrandev.bd/contact) |

---

## Dashboard preview

### Edge protection overview
![FileSentinel dashboard overview](docs/images/dashboard-overview.svg)

### Rule pack
![FileSentinel Cloudflare rule pack](docs/images/dashboard-rules.svg)

---

## What’s included

- Premium product website (`index.html`) with live-style security dashboard UI
- Production Cloudflare expression using safe `ends_with` / path checks
- Compact + full rule packs under `/rules`
- Full README with install steps and contact footer

### Important fix vs older stub

The previous root expression used broad `contains ".html" / ".php" / ".json"` checks that would **block legitimate pages**. FileSentinel replaces that with precise matching.

---

## Features

- Blocks secret & backup extensions: `.env*`, `.bak`, `.backup`, `.sql`, `.dump`, `.log`, keys, configs
- Blocks path probes: `/.git/`, `/.env`, `wp-config.php`, `/.ssh/`, `server-status`
- Action: **Block** at Cloudflare edge (no origin code changes)
- Safe for marketing sites, Laravel, WordPress, and APIs when tuned per stack

---

## Install (Cloudflare)

1. Open **Cloudflare Dashboard** → your domain  
2. **Security** → **WAF** → **Custom rules** → **Create rule**  
3. Paste the expression from [`rules/cloudflare-custom-rule.txt`](./rules/cloudflare-custom-rule.txt)  
4. Set action to **Block** → Deploy  

Quick start expression (subset):

```txt
(
  ends_with(http.request.uri.path, ".env")
  or ends_with(http.request.uri.path, ".bak")
  or ends_with(http.request.uri.path, ".sql")
  or ends_with(http.request.uri.path, ".htaccess")
  or http.request.uri.path contains "/.git/"
  or http.request.uri.path contains "/.env"
  or http.request.uri.path contains "/wp-config.php"
)
```

---

## File structure

```text
index.html                 Product / docs website
rules/security.rules       Compact expression
rules/cloudflare-custom-rule.txt   Full production pack
security.rules             Compatibility stub (points to safe rules)
docs/images/               README dashboard visuals
LICENSE                    MIT
```

---

## Roadmap / future development

Industry packs (Laravel SaaS, WordPress, fintech APIs), managed rule updates, and audit services — contact below.

---

## Author — Imran Ahmed (Imran Dev)

| Platform | Link |
|----------|------|
| Portfolio | [imrandev.bd](https://imrandev.bd) |
| Contact / hire | [imrandev.bd/contact](https://imrandev.bd/contact) |
| Email | [me@imrandev.bd](mailto:me@imrandev.bd) |
| WhatsApp | [+880 1576-918420](https://wa.me/8801576918420) |
| LinkedIn | [linkedin.com/in/imranbru99](https://linkedin.com/in/imranbru99) |
| GitHub | [github.com/imranbru99](https://github.com/imranbru99) |
| X / Twitter | [@imrandev_bd](https://x.com/imrandev_bd) |
| YouTube | [@ImranDevBD](https://youtube.com/@ImranDevBD) |
| Instagram | [@imranbru99](https://instagram.com/imranbru99) |
| Facebook | [ExpertImranDev](https://facebook.com/ExpertImranDev) |
| TikTok | [@imrandev_bd](https://tiktok.com/@imrandev_bd) |
| Threads | [@imranbru99](https://www.threads.net/@imranbru99) |
| Pinterest | [@imrandev_bd](https://pinterest.com/imrandev_bd) |
| All links | [linktr.ee/ExpertImranDev](https://linktr.ee/ExpertImranDev) |

---

© Imran Ahmed · FileSentinel · Future development: [imrandev.bd/contact](https://imrandev.bd/contact) · [me@imrandev.bd](mailto:me@imrandev.bd) · WhatsApp [+880 1576-918420](https://wa.me/8801576918420)
