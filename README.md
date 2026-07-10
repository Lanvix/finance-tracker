# Runway

A private, offline-first personal finance PWA focused on debt payoff. No account, no bank connection, no subscription — your figures never leave your device.

**Live app:** https://lanvix.github.io/finance-tracker/

## Why it exists

Most debt payoff apps put their best features behind a paywall and their worst bugs behind a bank sync. Runway takes the opposite approach: manual entry as a deliberate feature (logging a payment keeps you conscious of it), everything computed locally, and the full feature set free because there's no server to pay for.

## Features

**Debt payoff engine**
- Projected debt-free date, total interest, and per-debt payoff dates
- Avalanche (highest rate first), snowball (smallest balance first), or fully custom ordering
- Rate-aware simulation: 0% promotional rates automatically flip to their post-promo APR on the end date and re-prioritise
- Scenario comparison (minimums only / current plan / +£50 / +£100) and lump-sum what-ifs
- One-tap payment logging with full payment history per debt

**Intelligence layer**
- "Next best move" recommendations — always explained in plain English, never an unexplained score
- Proactive alerts: promo deadlines at risk, over-budget categories, bills due this week, plans that never clear
- Goals trade-off analysis ("pausing £X/mo savings gets you debt-free N months sooner")

**Budgeting**
- Category budgets with plain-English pacing ("By today you'd be on track under £82 — you're £14 ahead of pace")
- Month and week views, optional rollover of unspent money
- Bills and recurring commitments with due-day reminders and paid tracking
- Savings goals with progress tracking

**Foundation**
- Accounts layer and monthly net-position snapshots
- Activity log of every payment, spend and change
- Spreadsheet import (.xlsx/.csv with flexible header detection via SheetJS)
- JSON backup/restore and CSV export
- Guided onboarding for first run
- Dark and light themes
- Installable PWA with offline support (service worker, cache-versioned updates)

## Tech

Single-file vanilla JavaScript — no framework, no build step. One HTML file plus a service worker, manifest, and icons. State persists to `localStorage` (with a pluggable storage adapter). The payoff engine is a month-by-month simulation with date-aware interest rates and rollover of cleared minimums.

## Running it

It's a static site. Clone, open `index.html`, done — or host the five files anywhere (GitHub Pages works out of the box). To install on Android: open the hosted URL in Chrome → menu → Install app.

## Privacy model

All data stays in the browser's local storage on your device. Backups are exported manually by you. There is no analytics, no tracking, no network traffic beyond fetching the app itself and the SheetJS library.
