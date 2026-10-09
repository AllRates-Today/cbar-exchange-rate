# Central Bank of Azerbaijan Exchange Rates API — cbar-exchange-rate

[![npm version](https://img.shields.io/npm/v/cbar-exchange-rate.svg)](https://www.npmjs.com/package/cbar-exchange-rate)
[![license](https://img.shields.io/npm/l/cbar-exchange-rate.svg)](https://github.com/AllRates-Today/cbar-exchange-rate/blob/main/LICENSE)
[![zero dependencies](https://img.shields.io/badge/dependencies-0-brightgreen.svg)](https://www.npmjs.com/package/cbar-exchange-rate)
[![TypeScript](https://img.shields.io/badge/TypeScript-types%20included-3178C6.svg)](https://www.typescriptlang.org/)
[![USD/AZN today](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fallratestoday.com%2Fapi%2Fopen%2Fcentral-bank%2Fcbar%3Fsource%3DUSD%26target%3DAZN&query=%24.rate&label=USD%2FAZN%20published%20by%20Central%20Bank%20of%20Azerbaijan&color=0A7E8C&cacheSeconds=3600)](https://allratestoday.com/central-bank-rates-api/cbar/)
[![rate date](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fallratestoday.com%2Fapi%2Fopen%2Fcentral-bank%2Fcbar%3Fsource%3DUSD%26target%3DAZN&query=%24.rate_date&label=rate%20date&color=555&cacheSeconds=3600)](https://allratestoday.com/central-bank-rates-api/cbar/)

**Official Central Bank of Azerbaijan (Azerbaijan) daily exchange rates for Node.js and TypeScript. The published central bank rates behind tax filings, customs valuations, audits, and compliant invoicing — not market estimates, but the numbers Central Bank of Azerbaijan itself prints, every business day.**

## 🚀 Why this client?

- 🏛️ **Official published rates** — Central Bank of Azerbaijan's own table, with the publisher's own `rate_date` on every response
- 📅 **History back to 2016** — point-in-time tables and daily series for any past date
- 🔀 **Published vs derived, always flagged** — computed inverse/cross pairs carry `derived: true`, never mixed with official prints
- ⚡ **Zero dependencies** — pure ESM + CJS over global `fetch`; Node 18+, Bun, Deno, and edge runtimes
- 🔷 **Type-safe** — full TypeScript definitions shipped with the package
- 🧾 **Compliance-grade metadata** — `rate_type`, publication date, and source disclaimer on every response

> **Official rate, not mid-market:** every value here is a number Central Bank of Azerbaijan itself published, fixed once printed and carrying the central bank's own `rate_date` — what filings and audits require. Need the live mid-market rate for pricing or display instead? Use the [mid-market API](https://allratestoday.com/docs/) or [`@allratestoday/sdk`](https://www.npmjs.com/package/@allratestoday/sdk). The two can diverge by several percent.

## ⚡ Try it without a key

The latest Central Bank of Azerbaijan table is also served keyless, CORS-open and edge-cached, for evaluation, embeds and AI agents:

```bash
curl "https://allratestoday.com/api/open/central-bank/cbar?source=USD&target=AZN"
```

```js
const r = await fetch('https://allratestoday.com/api/open/central-bank/cbar').then((x) => x.json());
console.log(r.rate_date, r.rates.length); // the central bank's latest published table, no key
```

The open endpoint serves the *latest* table only and asks for a visible attribution link. The client below uses the keyed API, which adds point-in-time tables, history, and CSV/XML/Excel output.

## 📈 Latest published table

Today's full Central Bank of Azerbaijan table, straight from the central bank's latest publication. On GitHub it is refreshed by [a daily Action](.github/workflows/daily-table.yml) that reads the keyless endpoint above and commits only when the central bank publishes a new table; the copy on npm is as of the package's publish date.

<!-- daily-table:start -->
Published **2026-10-08** by Central Bank of Azerbaijan — 38 rates. Updated 2026-10-08.

| Base | Quote | Type | Rate |
| --- | --- | --- | ---: |
| AED | AZN | reference | 0.4628 |
| AUD | AZN | reference | 1.1824 |
| BYN | AZN | reference | 0.5638 |
| CAD | AZN | reference | 1.1919 |
| CHF | AZN | reference | 2.0409 |
| CNY | AZN | reference | 0.2536 |
| CZK | AZN | reference | 0.078 |
| DKK | AZN | reference | 0.2548 |
| EUR | AZN | reference | 1.9048 |
| GBP | AZN | reference | 2.2455 |
| GEL | AZN | reference | 0.6547 |
| HKD | AZN | reference | 0.2166 |
| HUF | AZN | reference | 0.005205 |
| ILS | AZN | reference | 0.5546 |
| INR | AZN | reference | 0.0176 |
| JPY | AZN | reference | 0.010743 |
| KGS | AZN | reference | 0.0194 |
| KRW | AZN | reference | 0.00127 |
| KWD | AZN | reference | 5.4759 |
| KZT | AZN | reference | 0.0038 |
| MDL | AZN | reference | 0.0954 |
| NOK | AZN | reference | 0.1776 |
| NZD | AZN | reference | 0.9526 |
| PKR | AZN | reference | 0.006114 |
| PLN | AZN | reference | 0.4351 |
| QAR | AZN | reference | 0.4664 |
| RON | AZN | reference | 0.3558 |
| RSD | AZN | reference | 0.0162 |
| RUB | AZN | reference | 0.019883 |
| SAR | AZN | reference | 0.4528 |
| SDR | AZN | reference | 2.2987 |
| SEK | AZN | reference | 0.1701 |
| SGD | AZN | reference | 1.3278 |
| TMT | AZN | reference | 0.4857 |
| TRY | AZN | reference | 0.0345 |
| UAH | AZN | reference | 0.0379 |
| USD | AZN | reference | 1.7 |
| UZS | AZN | reference | 0.000144 |

Source: [Official rates published by CBAR, served by AllRatesToday](https://allratestoday.com/central-bank-rates-api/cbar/). Rates are as printed by the central bank; AllRatesToday is not affiliated with it.
<!-- daily-table:end -->

## 🔑 Get your API key

Get a free API key at [allratestoday.com/register](https://allratestoday.com/register) — no credit card required. Latest rates are on every plan, including free.

## 📦 Installation

```bash
npm install cbar-exchange-rate
```

```bash
yarn add cbar-exchange-rate
```

```bash
pnpm add cbar-exchange-rate
```

Requires Node 18+ (global `fetch`); also runs on Bun, Deno and edge runtimes. Also published under the org scope as [`@allratestoday/cbar-exchange-rate`](https://www.npmjs.com/package/@allratestoday/cbar-exchange-rate) — same code, same versions.

## 🏁 Quick start

```js
import { getRate } from 'cbar-exchange-rate';

const pair = await getRate('USD', 'AZN', { apiKey: 'art_live_...' });
console.log(pair.rate, pair.rate_date); // the official Central Bank of Azerbaijan rate, on the central bank's own date
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
const pair = await getRate('USD', 'AZN', { apiKey: 'art_live_...' });
```

**Response:**

```javascript
{
  bank: 'cbar',
  name: 'Central Bank of Azerbaijan',
  rate_date: '2026-10-08',   // Central Bank of Azerbaijan's own publication date
  source: 'USD',
  target: 'AZN',
  rate: 1.7,
  rate_type: 'reference',
  derived: false,
  method: 'published',
  disclaimer: 'Official rates as published by the named central bank. On weekends/holidays the most recent published rate_date is returned.'
}
```

### Full published table

Free plan and up. The complete table for the latest publication date.

```js
import { getLatestRates } from 'cbar-exchange-rate';

const table = await getLatestRates({ apiKey: 'art_live_...' });
console.log(table.rate_date, table.rates.length);
```

**Response:**

```javascript
{
  bank: 'cbar',
  name: 'Central Bank of Azerbaijan',
  rate_date: '2026-10-08',
  rates: [
    { "base": "USD", "quote": "AZN", "type": "reference", "value": 1.7 },
    // … the rest of the published table (38 currencies vs AZN)
  ],
  disclaimer: '…'
}
```

### Table for a date

Paid plans. The official table for any date since 2016 — weekends and holidays return the most recent published date, flagged via `published_on_requested_date`, which is exactly the in-force rate a filing needs.

```js
import { getRatesForDate } from 'cbar-exchange-rate';

const day = await getRatesForDate('2026-06-30', { apiKey: 'art_live_...' });
// Optionally narrow to one pair:
const one = await getRatesForDate('2026-06-30', { apiKey: 'art_live_...', source: 'USD', target: 'AZN' });
```

**Response:**

```javascript
{
  bank: 'cbar',
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
import { getHistory } from 'cbar-exchange-rate';

const series = await getHistory(
  { source: 'USD', target: 'AZN', from: '2026-01-01', to: '2026-10-08' },
  { apiKey: 'art_live_...' }
);
```

**Response:**

```javascript
{
  bank: 'cbar',
  source: 'USD',
  target: 'AZN',
  from: '2026-01-01',
  to: '2026-10-08',
  count: 152,
  rates: [
    // one entry per publication date
    { date: '2026-10-08', rate: 1.7, rate_type: 'reference', derived: false, method: 'published' },
    // …
  ],
  disclaimer: '…'
}
```

Pass `{ symbol: 'USD' }` instead of `source`/`target` to get the raw published rows for one currency (all rate types, no pair resolution).

---

## 🗺️ Currencies covered

Central Bank of Azerbaijan currently publishes rates covering **38 currencies** against the AZN (as of the latest table):

🇦🇪 `AED` · 🇦🇺 `AUD` · 🇧🇾 `BYN` · 🇨🇦 `CAD` · 🇨🇭 `CHF` · 🇨🇳 `CNY` · 🇨🇿 `CZK` · 🇩🇰 `DKK` · 🇪🇺 `EUR` · 🇬🇧 `GBP` · 🇬🇪 `GEL` · 🇭🇰 `HKD` · 🇭🇺 `HUF` · 🇮🇱 `ILS` · 🇮🇳 `INR` · 🇯🇵 `JPY` · 🇰🇬 `KGS` · 🇰🇷 `KRW` · 🇰🇼 `KWD` · 🇰🇿 `KZT` · 🇲🇩 `MDL` · 🇳🇴 `NOK` · 🇳🇿 `NZD` · 🇵🇰 `PKR` · 🇵🇱 `PLN` · 🇶🇦 `QAR` · 🇷🇴 `RON` · 🇷🇸 `RSD` · 🇷🇺 `RUB` · 🇸🇦 `SAR` · `SDR` · 🇸🇪 `SEK` · 🇸🇬 `SGD` · 🇹🇲 `TMT` · 🇹🇷 `TRY` · 🇺🇦 `UAH` · 🇺🇸 `USD` · 🇺🇿 `UZS`

## 🏛️ Source

The Central Bank of Azerbaijan sets the official manat exchange rate for around 38 currencies each business day — the official reference for accounting, customs, and contracts in Azerbaijan.

- Publisher's own page: [Official exchange rates](https://www.cbar.az/currency/rates) · [www.cbar.az](https://www.cbar.az)
- Publication: every business day; the exact schedule, freshness status and any current delay are on the [Central Bank of Azerbaijan rates page](https://allratestoday.com/central-bank-rates-api/cbar/)
- Values are stored unmodified, with the publisher's own `rate_date` on every row — see the [methodology](https://allratestoday.com/official-rates-methodology/)

## 🧭 Reading the numbers

- `value` is always **quote currency per 1 unit of base currency** (`base: "EUR", quote: "USD", value: 1.15` means 1 EUR = 1.15 USD).
- Central Bank of Azerbaijan quotes **AZN per 1 unit of foreign currency** (e.g. `base: "USD", quote: "AZN"` means AZN per one US dollar).
- Need the other way round? Ask `getRate(target, source)` and the API inverts or crosses for you, flagged `derived: true` — never divide a published rate yourself in a compliance workflow.
- `rate_type` tells you which of the central bank's series a row belongs to (`reference` here); some publishers print buy/sell or several fixings for the same pair.

## 🧩 ERP & accounting systems

Loading the official Central Bank of Azerbaijan rate into an accounting system is a supported workflow, not a hack. Step-by-step guides with the direction each system expects:

- [Dynamics 365 Business Central](https://allratestoday.com/docs/integrations/business-central/) — built-in Currency Exchange Rate Service, no code
- [Xero](https://allratestoday.com/docs/integrations/xero/) · [QuickBooks Online](https://allratestoday.com/docs/integrations/quickbooks/) · [SAP S/4HANA and ECC](https://allratestoday.com/docs/integrations/sap/) · [Odoo](https://allratestoday.com/docs/integrations/odoo/)

The same keyed endpoints return `?format=csv`, `?format=xml` and `?format=xlsx`, and accept the key as `?api_key=` on the URL for importers that cannot send headers:

```bash
curl "https://allratestoday.com/api/v1/central-bank/cbar/latest?format=xml&api_key=art_live_..."
```

## 🤖 AI agents

- MCP server: `npx -y @allratestoday/central-bank-mcp` (stdio) or the hosted endpoint `https://allratestoday.com/api/mcp` — tools for official rates, history, cross-bank comparison and publication calendars
- Already using the general SDK or MCP server? Since 2026-10-01 [`@allratestoday/sdk`](https://www.npmjs.com/package/@allratestoday/sdk) 1.4+ has `officialRates('cbar')` and [`@allratestoday/mcp-server`](https://www.npmjs.com/package/@allratestoday/mcp-server) 0.6+ has a `get_official_rates` tool — both return this source's latest table with no key, so you can add it without a second dependency
- Claude Code plugin (no key): `/plugin marketplace add AllRates-Today/claude-code-plugin` then `/plugin install allratestoday@allratestoday` — bundles both MCP servers plus an `/official-rate cbar ...` command
- Machine-readable site guide: [llms.txt](https://allratestoday.com/llms.txt) · [for-ai-agents](https://allratestoday.com/for-ai-agents/)

## ⚖️ Published vs derived rates

If Central Bank of Azerbaijan does not print a pair directly, the API resolves it from the central bank's own table and says so — official and computed values are never confused:

| `method` | `derived` | Meaning |
| --- | --- | --- |
| `published` | `false` | The central bank printed this pair directly |
| `inverse` | `true` | Computed as 1 ÷ the published opposite direction |
| `cross` | `true` | Computed via AZN from two published rates |

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
| `404` | Pair or date range not covered by Central Bank of Azerbaijan |
| `429` | Monthly quota exceeded |

## 🔷 TypeScript

Full definitions ship with the package — no `@types` install:

```ts
import type { LatestRates, PairRate, DatedRates, RateEntry, HistoryQuery, RequestOptions } from 'cbar-exchange-rate';
```

## 📦 CommonJS

```javascript
const { getRate } = require('cbar-exchange-rate');

getRate('USD', 'AZN', { apiKey: 'art_live_...' }).then((pair) => console.log(pair.rate));
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
| `getHistory({ symbol \| source+target, from?, to? }, { apiKey })` | Paid | Daily series since 2016 |

## 📥 Bulk data (no key)

Need the whole archive rather than an API call? The same published tables are mirrored daily as open data:

- Hugging Face: [AllRates/central-bank-exchange-rates](https://huggingface.co/datasets/AllRates/central-bank-exchange-rates) — one CSV per institution (`rates/cbar.csv`)
- Kaggle: [allratestoday/central-bank-exchange-rates](https://www.kaggle.com/datasets/allratestoday/central-bank-exchange-rates)
- CDN JSON: `https://cdn.jsdelivr.net/gh/AllRates-Today/central-bank-exchange-rates@main/data/cbar/latest.json`

## 🔗 Links

- [Central Bank of Azerbaijan rates page](https://allratestoday.com/central-bank-rates-api/cbar/) — live table, publication cadence, FAQ
- [All central bank sources](https://allratestoday.com/central-bank-rates-api/)
- [Package docs on the site](https://allratestoday.com/docs/sdk/cbar-exchange-rate/) · [ERP integration guides](https://allratestoday.com/docs/integrations/)
- [API documentation](https://allratestoday.com/docs/#central-bank) · [Interactive reference](https://allratestoday.com/api-reference/) · [Methodology](https://allratestoday.com/official-rates-methodology/)
- [Register (free)](https://allratestoday.com/register) · [Pricing](https://allratestoday.com/pricing/)
- [GitHub](https://github.com/AllRates-Today/cbar-exchange-rate)

## 📜 License

MIT
