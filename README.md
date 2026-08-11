# Central Bank of Azerbaijan Exchange Rate API client

Official **Central Bank of Azerbaijan** (Azerbaijan) daily exchange rates in Node.js / TypeScript — 38 currencies against the AZN, with history back to 2016. Zero dependencies, works in Node 18+, Bun, Deno, and edge runtimes (uses global `fetch`).

These are the *published central bank rates* required for tax filings, customs valuations, audits, and compliant invoicing — not moving market rates. Every response carries the publisher's own publication date.

Powered by [AllRatesToday](https://allratestoday.com/central-bank-rates-api/cbar/). Get a free API key at [allratestoday.com/register](https://allratestoday.com/register) — no credit card required.

## Install

```bash
npm install cbar-exchange-rate
```

## Quick start

```js
import { getRate, getLatestRates } from 'cbar-exchange-rate';

// One pair at the official Central Bank of Azerbaijan rate
const pair = await getRate('USD', 'AZN', { apiKey: 'art_live_...' });
console.log(pair.rate, pair.rate_date); // e.g. USD -> AZN on the bank's own date

// The bank's full published table
const table = await getLatestRates({ apiKey: 'art_live_...' });
console.log(table.rate_date, table.rates.length);
```

## Historical data (paid plans)

```js
import { getRatesForDate, getHistory } from 'cbar-exchange-rate';

// The official table for an invoice date — weekends/holidays return the
// most recent published date, flagged via published_on_requested_date.
const day = await getRatesForDate('2026-06-30', { apiKey: 'art_live_...' });

// Daily series for one pair
const series = await getHistory(
  { source: 'USD', target: 'AZN', from: '2026-01-01' },
  { apiKey: 'art_live_...' }
);
```

## Currencies covered

Central Bank of Azerbaijan currently publishes rates covering **39 currencies** (as of the latest table):

`AED` · `AUD` · `AZN` · `BYN` · `CAD` · `CHF` · `CNY` · `CZK` · `DKK` · `EUR` · `GBP` · `GEL` · `HKD` · `HUF` · `ILS` · `INR` · `JPY` · `KGS` · `KRW` · `KWD` · `KZT` · `MDL` · `NOK` · `NZD` · `PKR` · `PLN` · `QAR` · `RON` · `RSD` · `RUB` · `SAR` · `SDR` · `SEK` · `SGD` · `TMT` · `TRY` · `UAH` · `USD` · `UZS`

Pairs the central bank does not print directly are resolved from this table (see below).

## Published vs derived rates

If Central Bank of Azerbaijan does not print a pair directly, the API resolves it from the bank's table (inverse, or a cross rate via AZN) and flags it `derived: true` with the `method` — so official and computed values are never confused.

## Notes

- Every request counts toward your AllRatesToday monthly quota. Rates change once per business day — cache a day's table locally and a small quota goes a long way.
- Latest rates are on every plan (including free); historical dates and time series need a [paid plan](https://allratestoday.com/pricing/).
- Full API reference: [allratestoday.com/docs#central-bank](https://allratestoday.com/docs/#central-bank) · All covered sources: [central bank rates API](https://allratestoday.com/central-bank-rates-api/)

## License

MIT
