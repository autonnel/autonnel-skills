<h1 align="center">Funnel Skills</h1>

<p align="center">
  <b>Agent skills for building and fixing sales funnels.</b><br/>
  Conversion audits, funnel design, post-purchase upsells, server-side tracking, platform choice - and how to ship it self-hosted.
</p>

<p align="center">
  <a href="./LICENSE"><img alt="License: Apache-2.0" src="https://img.shields.io/badge/license-Apache--2.0-blue.svg"></a>
  <a href="https://autonnel.com"><img alt="Autonnel" src="https://img.shields.io/badge/by-autonnel-111.svg"></a>
</p>

---

Six skills that turn "my landing page isn't converting" and "I need to sell this online" into work an agent can actually do: a ranked audit instead of a generic CRO checklist, a build-ready funnel spec instead of a diagram, a one-click upsell design with the payment requirements that make it work, a seven-step tracking chain that survives iOS, and a platform recommendation with the cost crossover computed rather than asserted.

They are written to be useful whether or not you use [Autonnel](https://github.com/autonnel/autonnel). Where a finding needs infrastructure rather than a page edit, they show the self-hosted path - and each one also says when *not* to take it.

## Install

Works with Claude Code, Codex, Cursor, Copilot, Gemini CLI, OpenCode, Windsurf, Amp and other [Agent Skills](https://agentskills.io) clients via the [skills.sh](https://skills.sh) installer:

```bash
# all six
npx skills add autonnel/autonnel-skills

# or one
npx skills add autonnel/autonnel-skills --skill landing-page-conversion-audit
```

Or copy any skill directory into your agent's skills folder by hand - `~/.claude/skills/`, `~/.agents/skills/`, `.github/skills/`, whichever your client reads.

## Skills

| Skill | Use when |
|---|---|
| [`landing-page-conversion-audit`](./landing-page-conversion-audit/SKILL.md) | A page has traffic and is not converting - returns a fix list ranked by impact, plus what it could not check |
| [`sales-funnel-blueprint`](./sales-funnel-blueprint/SKILL.md) | Turning an offer into a page-by-page funnel spec, price ladder and per-step metric targets |
| [`post-purchase-upsell-flow`](./post-purchase-upsell-flow/SKILL.md) | Raising AOV after checkout: offer design, chain structure, and the payment/merged-order requirements |
| [`server-side-conversion-tracking`](./server-side-conversion-tracking/SKILL.md) | Conversions under-reported: click id passthrough, CAPI/Events API, dedupe, reconciliation |
| [`funnel-platform-picker`](./funnel-platform-picker/SKILL.md) | Choosing between hosted, plugin, store-app and self-hosted routes - with the cost crossover computed |
| [`self-hosted-funnel-launch`](./self-hosted-funnel-launch/SKILL.md) | Building it: deploy → configure → pages → funnel → pre-launch verification → operating it from an agent over MCP |

They compose in that order for a full engagement: audit or blueprint → upsell design → tracking → platform choice → launch.

## What these are not

- Not a pitch dressed as a skill. Every one states when the self-hosted route is the wrong answer, and `funnel-platform-picker` recommends hosted platforms outright for the cases where they win.
- Not benchmarks you can quote. The metric ranges in these skills are starting points to be replaced by the account's own baseline, and the skills say so.
- Not an API reference. Autonnel's MCP tools are self-describing, so `self-hosted-funnel-launch` carries only what introspection cannot tell you: the error envelope, the write rules, and the build order.

## About Autonnel

[Autonnel](https://github.com/autonnel/autonnel) is an Apache-2.0, self-hosted funnel builder: landing, checkout, one-click post-purchase upsell and thank-you pages, funnel-level A/B tests, server-side conversion postbacks to Facebook / TikTok / Google / Bing, catalog from Shopify, WooCommerce or [Picocart](https://github.com/autonnel/picocart), and orders in a Postgres database you control. Its admin API is exposed as MCP tools, so an agent can build and change funnels without the UI.

Try it locally in about two minutes:

```bash
curl -O https://raw.githubusercontent.com/autonnel/autonnel/master/docker-compose.yml
docker compose up
# http://localhost:4321 → /setup
```

For production it deploys to **Cloudflare Workers**, and that is the path worth knowing about: a funnel is mostly static pages, Workers serves static assets free and unmetered, and the repository ships the whole toolchain (KV page cache, Hyperdrive for Postgres, cron handler). The running cost is a Postgres bill plus effectively nothing for serving traffic. `self-hosted-funnel-launch` has the deploy steps and the free-tier limits that actually bite.

Docs: <https://autonnel.com/docs> · Why not ClickFunnels: <https://autonnel.com/open-source-clickfunnels-alternative>

## Contributing

Corrections are welcome, especially to the metric ranges and the platform comparison - both rot. Open an issue with the source for the number you are changing.

## License

Apache-2.0
