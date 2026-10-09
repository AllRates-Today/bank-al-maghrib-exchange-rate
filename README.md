# Bank Al-Maghrib Exchange Rates API — bank-al-maghrib-exchange-rate

[![npm version](https://img.shields.io/npm/v/bank-al-maghrib-exchange-rate.svg)](https://www.npmjs.com/package/bank-al-maghrib-exchange-rate)
[![license](https://img.shields.io/npm/l/bank-al-maghrib-exchange-rate.svg)](https://github.com/AllRates-Today/bank-al-maghrib-exchange-rate/blob/main/LICENSE)
[![zero dependencies](https://img.shields.io/badge/dependencies-0-brightgreen.svg)](https://www.npmjs.com/package/bank-al-maghrib-exchange-rate)
[![TypeScript](https://img.shields.io/badge/TypeScript-types%20included-3178C6.svg)](https://www.typescriptlang.org/)
[![USD/MAD today](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fallratestoday.com%2Fapi%2Fopen%2Fcentral-bank%2Fbam%3Fsource%3DUSD%26target%3DMAD&query=%24.rate&label=USD%2FMAD%20published%20by%20Bank%20Al-Maghrib&color=0A7E8C&cacheSeconds=3600)](https://allratestoday.com/central-bank-rates-api/bam/)
[![rate date](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fallratestoday.com%2Fapi%2Fopen%2Fcentral-bank%2Fbam%3Fsource%3DUSD%26target%3DMAD&query=%24.rate_date&label=rate%20date&color=555&cacheSeconds=3600)](https://allratestoday.com/central-bank-rates-api/bam/)

**Official Bank Al-Maghrib (Morocco) daily exchange rates for Node.js and TypeScript. The published central bank rates behind tax filings, customs valuations, audits, and compliant invoicing — not market estimates, but the numbers Bank Al-Maghrib itself prints, every business day.**

## 🚀 Why this client?

- 🏛️ **Official published rates** — Bank Al-Maghrib's own table, with the publisher's own `rate_date` on every response
- 📅 **History back to 2000** — point-in-time tables and daily series for any past date
- 🔀 **Published vs derived, always flagged** — computed inverse/cross pairs carry `derived: true`, never mixed with official prints
- ⚡ **Zero dependencies** — pure ESM + CJS over global `fetch`; Node 18+, Bun, Deno, and edge runtimes
- 🔷 **Type-safe** — full TypeScript definitions shipped with the package
- 🧾 **Compliance-grade metadata** — `rate_type`, publication date, and source disclaimer on every response

> **Official rate, not mid-market:** every value here is a number Bank Al-Maghrib itself published, fixed once printed and carrying the central bank's own `rate_date` — what filings and audits require. Need the live mid-market rate for pricing or display instead? Use the [mid-market API](https://allratestoday.com/docs/) or [`@allratestoday/sdk`](https://www.npmjs.com/package/@allratestoday/sdk). The two can diverge by several percent.

## ⚡ Try it without a key

The latest Bank Al-Maghrib table is also served keyless, CORS-open and edge-cached, for evaluation, embeds and AI agents:

```bash
curl "https://allratestoday.com/api/open/central-bank/bam?source=USD&target=MAD"
```

```js
const r = await fetch('https://allratestoday.com/api/open/central-bank/bam').then((x) => x.json());
console.log(r.rate_date, r.rates.length); // the central bank's latest published table, no key
```

The open endpoint serves the *latest* table only and asks for a visible attribution link. The client below uses the keyed API, which adds point-in-time tables, history, and CSV/XML/Excel output.

## 📈 Latest published table

Today's full Bank Al-Maghrib table, straight from the central bank's latest publication. On GitHub it is refreshed by [a daily Action](.github/workflows/daily-table.yml) that reads the keyless endpoint above and commits only when the central bank publishes a new table; the copy on npm is as of the package's publish date.

<!-- daily-table:start -->
Published **2026-10-08** by Bank Al-Maghrib — 30 rates. Updated 2026-10-08.

| Base | Quote | Type | Rate |
| --- | --- | --- | ---: |
| AED | MAD | reference | 2.708 |
| AUD | MAD | reference | 6.9208 |
| BHD | MAD | reference | 26.372 |
| BRL | MAD | reference | 1.9834 |
| CAD | MAD | reference | 6.98 |
| CHF | MAD | reference | 11.931 |
| CNY | MAD | reference | 1.484 |
| DKK | MAD | reference | 1.4898 |
| DZD | MAD | reference | 0.07394 |
| EGP | MAD | reference | 0.1899 |
| EUR | MAD | reference | 11.1346 |
| GBP | MAD | reference | 13.134 |
| GIP | MAD | reference | 13.134 |
| INR | MAD | reference | 0.1028 |
| JOD | MAD | reference | 14.033 |
| JPY | MAD | reference | 0.062868 |
| KWD | MAD | reference | 31.994 |
| LYD | MAD | reference | 1.9292 |
| MRU | MAD | reference | 0.25137 |
| NOK | MAD | reference | 1.04 |
| OMR | MAD | reference | 25.835 |
| QAR | MAD | reference | 2.7287 |
| RUB | MAD | reference | 0.1163 |
| SAR | MAD | reference | 2.6495 |
| SEK | MAD | reference | 0.99474 |
| TND | MAD | reference | 3.3083 |
| TRY | MAD | reference | 0.2021 |
| USD | MAD | reference | 9.9466 |
| XOF | MAD | reference | 0.016974 |
| ZAR | MAD | reference | 0.5974 |

Source: [Official rates published by BAM, served by AllRatesToday](https://allratestoday.com/central-bank-rates-api/bam/). Rates are as printed by the central bank; AllRatesToday is not affiliated with it.
<!-- daily-table:end -->

## 🔑 Get your API key

Get a free API key at [allratestoday.com/register](https://allratestoday.com/register) — no credit card required. Latest rates are on every plan, including free.

## 📦 Installation

```bash
npm install bank-al-maghrib-exchange-rate
```

```bash
yarn add bank-al-maghrib-exchange-rate
```

```bash
pnpm add bank-al-maghrib-exchange-rate
```

Requires Node 18+ (global `fetch`); also runs on Bun, Deno and edge runtimes. Also published under the org scope as [`@allratestoday/bank-al-maghrib-exchange-rate`](https://www.npmjs.com/package/@allratestoday/bank-al-maghrib-exchange-rate) — same code, same versions.

## 🏁 Quick start

```js
import { getRate } from 'bank-al-maghrib-exchange-rate';

const pair = await getRate('USD', 'MAD', { apiKey: 'art_live_...' });
console.log(pair.rate, pair.rate_date); // the official Bank Al-Maghrib rate, on the central bank's own date
```

## 📚 API reference

- [Latest pair rate](#latest-pair-rate) — one pair from the latest published table
- [Full published table](#full-published-table) — everything the central bank printed, in one call
- [Table for a date](#table-for-a-date) — the official table for an invoice or filing date
- [Daily time series](#daily-time-series) — one pair across a date range

---

### Latest pair rate

Free plan and up. Pairs the central bank does not print directly are resolved from its table and flagged (see *Published vs derived rates* below).

```js
const pair = await getRate('USD', 'MAD', { apiKey: 'art_live_...' });
```

**Response:**

```javascript
{
  bank: 'bam',
  name: 'Bank Al-Maghrib',
  rate_date: '2026-10-08',   // Bank Al-Maghrib's own publication date
  source: 'USD',
  target: 'MAD',
  rate: 9.9466,
  rate_type: 'reference',
  derived: false,
  method: 'published',
  disclaimer: 'Official rates as published by the named central bank. On weekends/holidays the most recent published rate_date is returned.'
}
```

### Full published table

Free plan and up. The complete table for the latest publication date.

```js
import { getLatestRates } from 'bank-al-maghrib-exchange-rate';

const table = await getLatestRates({ apiKey: 'art_live_...' });
console.log(table.rate_date, table.rates.length);
```

**Response:**

```javascript
{
  bank: 'bam',
  name: 'Bank Al-Maghrib',
  rate_date: '2026-10-08',
  rates: [
    { "base": "USD", "quote": "MAD", "type": "reference", "value": 9.9466 },
    // … the rest of the published table (28 currencies vs MAD)
  ],
  disclaimer: '…'
}
```

### Table for a date

Paid plans. The official table for any date since 2000 — weekends and holidays return the most recent published date, flagged via `published_on_requested_date`, which is exactly the in-force rate a filing needs.

```js
import { getRatesForDate } from 'bank-al-maghrib-exchange-rate';

const day = await getRatesForDate('2026-06-30', { apiKey: 'art_live_...' });
// Optionally narrow to one pair:
const one = await getRatesForDate('2026-06-30', { apiKey: 'art_live_...', source: 'USD', target: 'MAD' });
```

**Response:**

```javascript
{
  bank: 'bam',
  requested_date: '2026-06-30',
  rate_date: '2026-06-30',                // the date actually published
  published_on_requested_date: true,      // false when a weekend/holiday fell back
  rates: [ /* the full table for that date */ ],
  disclaimer: '…'
}
```

### Daily time series

Paid plans. One resolved rate per publication date — ready for charting, revaluation runs, or audit workpapers.

```js
import { getHistory } from 'bank-al-maghrib-exchange-rate';

const series = await getHistory(
  { source: 'USD', target: 'MAD', from: '2026-01-01', to: '2026-10-08' },
  { apiKey: 'art_live_...' }
);
```

**Response:**

```javascript
{
  bank: 'bam',
  source: 'USD',
  target: 'MAD',
  from: '2026-01-01',
  to: '2026-10-08',
  count: 152,
  rates: [
    // one entry per publication date
    { date: '2026-10-08', rate: 9.9466, rate_type: 'reference', derived: false, method: 'published' },
    // …
  ],
  disclaimer: '…'
}
```

Pass `{ symbol: 'USD' }` instead of `source`/`target` to get the raw published rows for one currency (all rate types, no pair resolution).

---

## 🗺️ Currencies covered

Bank Al-Maghrib currently publishes rates covering **28 currencies** against the MAD (as of the latest table):

🇦🇪 `AED` · 🇦🇺 `AUD` · 🇧🇭 `BHD` · 🇧🇷 `BRL` · 🇨🇦 `CAD` · 🇨🇭 `CHF` · 🇨🇳 `CNY` · 🇩🇰 `DKK` · 🇪🇬 `EGP` · 🇪🇺 `EUR` · 🇬🇧 `GBP` · 🇬🇮 `GIP` · 🇮🇳 `INR` · 🇯🇴 `JOD` · 🇯🇵 `JPY` · 🇰🇼 `KWD` · 🇱🇾 `LYD` · 🇲🇷 `MRU` · 🇳🇴 `NOK` · 🇴🇲 `OMR` · 🇷🇺 `RUB` · 🇸🇦 `SAR` · 🇸🇪 `SEK` · 🇹🇳 `TND` · 🇹🇷 `TRY` · 🇺🇸 `USD` · `XOF` · 🇿🇦 `ZAR`

## 🏛️ Source

Bank Al-Maghrib publishes daily reference exchange rates (cours de référence) for the Moroccan dirham — around 30 currencies quoted against the dirham each business day around midday Rabat time. Under Morocco's managed-float regime it is the official benchmark Moroccan accounting, customs and contracts reference; the archive on the bank's site reaches back to 2000, with buy/sell quotes in the earlier years and a published mid rate since 2017.

- Publisher's own page: [Cours de référence](https://www.bkam.ma/Marches/Principaux-indicateurs/Marche-des-changes/Cours-de-change/Cours-de-reference) · [www.bkam.ma](https://www.bkam.ma)
- Publication: every business day; the exact schedule, freshness status and any current delay are on the [Bank Al-Maghrib rates page](https://allratestoday.com/central-bank-rates-api/bam/)
- Values are stored unmodified, with the publisher's own `rate_date` on every row — see the [methodology](https://allratestoday.com/official-rates-methodology/)

## 🧭 Reading the numbers

- `value` is always **quote currency per 1 unit of base currency** (`base: "EUR", quote: "USD", value: 1.15` means 1 EUR = 1.15 USD).
- Bank Al-Maghrib quotes **MAD per 1 unit of foreign currency** (e.g. `base: "USD", quote: "MAD"` means MAD per one US dollar).
- Need the other way round? Ask `getRate(target, source)` and the API inverts or crosses for you, flagged `derived: true` — never divide a published rate yourself in a compliance workflow.
- `rate_type` tells you which of the central bank's series a row belongs to (`reference` here); some publishers print buy/sell or several fixings for the same pair.

## 🧩 ERP & accounting systems

Loading the official Bank Al-Maghrib rate into an accounting system is a supported workflow, not a hack. Step-by-step guides with the direction each system expects:

- [Dynamics 365 Business Central](https://allratestoday.com/docs/integrations/business-central/) — built-in Currency Exchange Rate Service, no code
- [Xero](https://allratestoday.com/docs/integrations/xero/) · [QuickBooks Online](https://allratestoday.com/docs/integrations/quickbooks/) · [SAP S/4HANA and ECC](https://allratestoday.com/docs/integrations/sap/) · [Odoo](https://allratestoday.com/docs/integrations/odoo/)

The same keyed endpoints return `?format=csv`, `?format=xml` and `?format=xlsx`, and accept the key as `?api_key=` on the URL for importers that cannot send headers:

```bash
curl "https://allratestoday.com/api/v1/central-bank/bam/latest?format=xml&api_key=art_live_..."
```

## 🤖 AI agents

- MCP server: `npx -y @allratestoday/central-bank-mcp` (stdio) or the hosted endpoint `https://allratestoday.com/api/mcp` — tools for official rates, history, cross-bank comparison and publication calendars
- Already using the general SDK or MCP server? Since 2026-10-01 [`@allratestoday/sdk`](https://www.npmjs.com/package/@allratestoday/sdk) 1.4+ has `officialRates('bam')` and [`@allratestoday/mcp-server`](https://www.npmjs.com/package/@allratestoday/mcp-server) 0.6+ has a `get_official_rates` tool — both return this source's latest table with no key, so you can add it without a second dependency
- Claude Code plugin (no key): `/plugin marketplace add AllRates-Today/claude-code-plugin` then `/plugin install allratestoday@allratestoday` — bundles both MCP servers plus an `/official-rate bam ...` command
- Machine-readable site guide: [llms.txt](https://allratestoday.com/llms.txt) · [for-ai-agents](https://allratestoday.com/for-ai-agents/)

## ⚖️ Published vs derived rates

If Bank Al-Maghrib does not print a pair directly, the API resolves it from the central bank's own table and says so — official and computed values are never confused:

| `method` | `derived` | Meaning |
| --- | --- | --- |
| `published` | `false` | The central bank printed this pair directly |
| `inverse` | `true` | Computed as 1 ÷ the published opposite direction |
| `cross` | `true` | Computed via MAD from two published rates |

## 🛡️ Error handling

Errors are thrown as `Error` with `status` (HTTP code) and `body` (the API's JSON error) attached:

```js
try {
  const pair = await getRate('USD', 'XXX', { apiKey: 'art_live_...' });
} catch (err) {
  console.log(err.message); // human-readable reason
  console.log(err.status);  // e.g. 404
}
```

| Status | Meaning |
| ------ | ------- |
| — | Missing `apiKey` (thrown before any request) |
| `400` | Malformed date or parameters |
| `401` | Invalid API key |
| `403` | Endpoint needs a [paid plan](https://allratestoday.com/pricing/) (historical dates & series) |
| `404` | Pair or date range not covered by Bank Al-Maghrib |
| `429` | Monthly quota exceeded |

## 🔷 TypeScript

Full definitions ship with the package — no `@types` install:

```ts
import type { LatestRates, PairRate, DatedRates, RateEntry, HistoryQuery, RequestOptions } from 'bank-al-maghrib-exchange-rate';
```

## 📦 CommonJS

```javascript
const { getRate } = require('bank-al-maghrib-exchange-rate');

getRate('USD', 'MAD', { apiKey: 'art_live_...' }).then((pair) => console.log(pair.rate));
```

## 💡 Quota tips

- Rates change once per business day — cache the published table locally and a small monthly quota goes a long way.
- Every request counts toward your AllRatesToday quota, shared across all AllRatesToday endpoints on your key.

## 📖 Methods reference

| Method | Plan | Description |
| ------ | ---- | ----------- |
| `getRate(source, target, { apiKey })` | Free | Latest rate for one pair, resolved from the published table |
| `getLatestRates({ apiKey })` | Free | The central bank's full latest published table |
| `getRatesForDate(date, { apiKey, source?, target? })` | Paid | The official table (or one pair) for a YYYY-MM-DD date |
| `getHistory({ symbol \| source+target, from?, to? }, { apiKey })` | Paid | Daily series since 2000 |

## 📥 Bulk data (no key)

Need the whole archive rather than an API call? The same published tables are mirrored daily as open data:

- Hugging Face: [AllRates/central-bank-exchange-rates](https://huggingface.co/datasets/AllRates/central-bank-exchange-rates) — one CSV per institution (`rates/bam.csv`)
- Kaggle: [allratestoday/central-bank-exchange-rates](https://www.kaggle.com/datasets/allratestoday/central-bank-exchange-rates)
- CDN JSON: `https://cdn.jsdelivr.net/gh/AllRates-Today/central-bank-exchange-rates@main/data/bam/latest.json`

## 🔗 Links

- [Bank Al-Maghrib rates page](https://allratestoday.com/central-bank-rates-api/bam/) — live table, publication cadence, FAQ
- [All central bank sources](https://allratestoday.com/central-bank-rates-api/)
- [Package docs on the site](https://allratestoday.com/docs/sdk/bank-al-maghrib-exchange-rate/) · [ERP integration guides](https://allratestoday.com/docs/integrations/)
- [API documentation](https://allratestoday.com/docs/#central-bank) · [Interactive reference](https://allratestoday.com/api-reference/) · [Methodology](https://allratestoday.com/official-rates-methodology/)
- [Register (free)](https://allratestoday.com/register) · [Pricing](https://allratestoday.com/pricing/)
- [GitHub](https://github.com/AllRates-Today/bank-al-maghrib-exchange-rate)

## 📜 License

MIT
