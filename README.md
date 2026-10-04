## Jean Calvain Doumba

Full-stack engineer and founder of **DaDa** · Garoua, Cameroon

I build systems where money moves through Mobile Money: asynchronous payments, escrow, reconciliation, and apps that keep working when the network drops.

---

### DaDa - rent held in escrow

In Cameroon, tenants often pay several months of rent upfront, to a broker or a landlord, with no recourse if the place isn't what was promised. DaDa holds that payment in escrow: after paying, the tenant has 72 hours to check the property before the money is released. DaDa is built for real-estate agents first: their commission is taken at the source, out of escrow.

```
Mobile Money payment
 └▶ collected by the payment provider
     └▶ escrow, 72 h
         ├─ confirmed, or silence ─▶ payout (landlord, agent)
         └─ dispute ───────────────▶ mediation, timer frozen
```

**Decisions that matter**

- **DaDa never holds the funds.** The payment provider collects and pays out; the app stores a reference, never a balance. Escrow lives in code as a state machine: every state has an explicit transition table, and an illegal transition returns 409.
- **Payments are isolated**: a dedicated PostgreSQL schema and SQL role, one interface in. Switching providers means writing one adapter.
- **A webhook is verified before it is applied**: signature (RFC 9421), then idempotency on the event id, then the transition. A lost event is recovered by reconciling against the ledger.
- **Field agents work offline.** Geotagged photos and listings wait in a durable queue and sync when the network comes back.
- **No token ever reaches the browser.** The web app's BFF keeps tokens in `httpOnly` cookies, and every request is signed with a non-extractable device key.

**Stack** — Laravel 13 (modular monolith, 8 modules) · PostgreSQL + PostGIS · Redis · Next.js 16 · React Native / Expo  
**Quality** — 2,500+ Pest tests, CI on all three repos, built for Cameroon's 2024/017 personal data law  
**Status** — pre-launch. The code is private; happy to walk you through the architecture on a call.

<!-- Uncomment once calvino-framework has a real README, tests and CI:
### Also

[**calvino**](https://github.com/DOUMBAJC/calvino-framework) — a PHP micro-framework written from scratch: router, query builder, migrations, CLI.
-->

---

<!-- calvinopro.com did not resolve on 2026-10-04: add it back once the site is up. -->
[LinkedIn](https://www.linkedin.com/in/jean-calvain-doumba) · [Telegram](https://t.me/calvino_pro) · [Email](mailto:jeancalvaindoumba07@gmail.com)
