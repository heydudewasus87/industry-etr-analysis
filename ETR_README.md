# Effective Tax Rate Analysis — Big Tech

Why does Nvidia pay a ~15% tax rate when the corporate rate is 21% — and why did Meta's rate
suddenly double to ~30% in a single year? This project analyzes the **effective tax rates (ETR)** of
five large-cap tech firms — Apple, Microsoft, Nvidia, Alphabet, and Meta — and reconciles, line by
line, exactly what drives each one's rate away from the statutory 21%.

It's a financial-statement-analysis project: the kind of work a tax or FP&A analyst does when
reading a company's 10-K tax footnote.

---

## The question

Every US company starts at a **21% statutory federal tax rate**. But the rate they actually pay —
the **effective tax rate** — is usually lower, because of foreign income taxed elsewhere, the FDII
export deduction, R&D credits, and stock-based compensation. Companies disclose this gap in a
**rate reconciliation** table buried in the tax footnote of their annual report. This project pulls
that apart for big tech.

---

## What's inside

`Effective_Tax_Rate_Analysis.ipynb` — a single notebook that:

1. **Pulls ETR live** (income tax ÷ pre-tax income) for each firm over several years and charts it
   against the 21% line.
2. **Reconciles the gap** — a waterfall chart for each company that walks from 21% down to its
   effective rate, one driver at a time.
3. **Compares the levers** — shows which mechanism (foreign income, R&D credits, stock comp) each
   firm leans on most.

---

## How to run it

Open the notebook in Google Colab → **Runtime → Run all**. No setup or API keys. It pulls financial
data automatically (with a researched fallback if the pull fails).

---

## Key findings

- **Underlying, all five firms are taxed below 21%** — recurring effective rates land in the
  low-to-high teens.
- **The same four levers** explain most of it: foreign income at lower rates, the FDII deduction,
  R&D credits, and stock-based compensation.
- **Each firm leans differently:** Apple's savings are overwhelmingly foreign (Ireland); Nvidia
  spreads it across FDII, credits, and stock comp.
- **One-time items can flip the headline rate.** Two firms show a latest-year rate *above* 21% for
  one-off reasons, not higher underlying rates:
  - **Apple FY2024 (~24%):** a single ~$10B EU/Ireland charge.
  - **Meta FY2025 (~30%):** a one-time ~$12B non-cash valuation-allowance charge from the OBBBA
    tax-law change. Strip it out and Meta is back near ~16%. *(This project's live data surfaced
    the ~30% figure; checking Meta's 10-K confirmed it and explained why.)*

Full write-up in [RESULTS.md](RESULTS.md).

---

## Data sources

This project deliberately uses **two different sources** for two different things, because the two
kinds of data live in two different places:

| What | Source | How it's obtained | Live? |
|------|--------|-------------------|-------|
| **Effective tax rate** (tax expense ÷ pre-tax income) | Yahoo Finance, via the `yfinance` Python library | Pulled automatically from each company's annual income statement | Yes — fetched when you run the notebook |
| **Rate reconciliation** (the line items: foreign income, FDII, R&D credits, stock comp, etc.) | Each company's **10-K annual report**, tax footnote, filed on SEC EDGAR | Transcribed by hand from the filings and cited in the notebook | No — these are static, sourced figures |

**Why the split?** The effective tax rate is just two numbers off the income statement, so it pulls
cleanly from an API. The *reconciliation* — the explanation of **why** the rate is what it is —
exists only as a table inside the 10-K tax footnote and is not available in clean machine-readable
form. So those figures are read out of the filings directly. Reading the tax footnote is the actual
analytical skill this project demonstrates, not an API call.

**If the live pull fails** (yfinance is an unofficial wrapper and can be flaky), the notebook falls
back to a researched set of effective tax rates so it always runs. The printout tells you which
source was used: `Data source: yfinance (live)` or `Data source: researched fallback`.

> **Verify before publishing:** the reconciliation line items are transcribed for a representative
> fiscal year. Tax figures change annually, so spot-check a couple against the current 10-Ks (free
> on [SEC EDGAR](https://www.sec.gov/edgar)) before relying on them.

---

## How the code works

The notebook runs top to bottom in a few clear stages:

1. **Setup.** Installs `yfinance`, imports `pandas` and `matplotlib`, and defines the peer set
   (`AAPL, MSFT, NVDA, GOOGL, META`), the 21% statutory rate, and a color for each firm.

2. **Pull effective tax rates.** For each ticker, `pull_etr()` calls `yfinance`, reads the
   `Tax Provision` and `Pretax Income` rows from the annual income statement, and divides them to get
   the ETR for each fiscal year. If any pull fails it uses the hardcoded `ETR_FALLBACK` values. The
   result is a table of ETR by year, by company.

3. **Trend + bar charts.** Plots each firm's ETR over time against the dashed 21% line, then a bar
   chart of the most recent year — showing at a glance that every firm sits below statutory.

4. **Load the reconciliations.** `RECONCILIATIONS` is a dictionary holding the hand-transcribed
   footnote data: for each company, an ordered list of `(driver, rate impact)` pairs that sum to the
   effective rate, plus the source filing. A sanity-check loop confirms each one adds up correctly.

5. **Waterfall charts.** `waterfall()` draws the bridge for one company: it starts a bar at 21%, then
   stacks each driver on top — green when it lowers the rate, red when it raises it — and ends with
   the effective rate. The notebook renders one for each firm in a grid.

6. **Driver comparison.** `bucketize()` sorts each company's reconciliation items into four buckets
   (foreign/FDII, R&D credit, stock comp, state/other) and a stacked bar chart compares them — making
   it obvious which lever each firm leans on.

7. **Summary.** A short written takeaway plus the limitations.

Every number that isn't pulled live is labeled and sourced in the code, so the provenance of each
figure is traceable.

---

## Built with

Python · yfinance (Yahoo Finance data) · pandas · matplotlib · SEC EDGAR 10-K filings (manual)

---

## Disclaimer

Educational and research project. Not tax or investment advice. Reconciliation figures are
representative and should be verified against current filings; tax rates change yearly.
