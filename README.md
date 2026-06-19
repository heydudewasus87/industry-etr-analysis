# Effective Tax Rate Analysis for Big Tech

I have always wondered why a company like NVIDIA pays a ~15% tax rate when the corporate rate is 21%. This project analyzes the **effective tax rates (ETR)** of
five large-cap tech firms — Apple, Microsoft, Nvidia, Alphabet, and Meta — and reconciles, line by
line, exactly what drives each one's rate away from the statutory 21%.

---

## The question

Every US company starts at a **21% statutory federal tax rate**. But the rate they actually pay are usually lower, because of foreign income taxed elsewhere, the FDII
export deduction, R&D credits, and stock-based compensation. Companies disclose this gap in a
**rate reconciliation** table buried in the tax footnote of their annual report. This project pulls
that apart for big tech.

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
    tax-law change. 

---

## Data sources

This project deliberately uses **two different sources** for two different things, because the two
kinds of data live in two different places:

| What | Source | How it's obtained | Live? |
|------|--------|-------------------|-------|
| **Effective tax rate** (tax expense ÷ pre-tax income) | Yahoo Finance, via the `yfinance` Python library | Pulled automatically from each company's annual income statement | Yes — fetched when you run the notebook |
| **Rate reconciliation** (the line items: foreign income, FDII, R&D credits, stock comp, etc.) | Each company's **10-K annual report**, tax footnote, filed on SEC EDGAR | Transcribed by hand from the filings and cited in the notebook | Static figures |

**Why the split?** The effective tax rate is just two numbers off the income statement, so it pulls
cleanly from an API. The *reconciliation* exists only as a table inside the 10-K tax footnote and is not available in clean machine-readable
form. So those figures are read out of the filings directly. 


---

## Built with

Python · yfinance (Yahoo Finance data) · pandas · matplotlib · SEC EDGAR 10-K filings (manual)

---

## Disclaimer

Educational and research project. Not tax or investment advice. Reconciliation figures are
representative and should be verified against current filings; tax rates change yearly.
