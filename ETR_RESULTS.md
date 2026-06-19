# Findings — Big Tech Effective Tax Rates

How five of the largest US tech companies — Apple, Microsoft, Nvidia, Alphabet, and Meta — are
taxed, why their effective rates differ from the 21% statutory rate, and why a single year's
headline rate can be deeply misleading.

---

## The headline

**Underlying, every firm in the peer set is taxed below the 21% statutory rate** — recurring
effective rates land in the low-to-high teens, using standard, fully-disclosed mechanisms. But
**two firms show a latest-year rate *above* 21%, and in both cases it's a one-time item, not a
higher underlying rate.** Separating recurring drivers from one-offs is the whole point of reading
the reconciliation.

| Company | Latest effective rate | Underlying (ex one-offs) | Biggest recurring lever |
|---------|----------------------|--------------------------|-------------------------|
| Nvidia | ~15.1% | ~15% | FDII + credits + stock comp |
| Apple | ~16% (FY2025) | ~15% | Foreign income (Ireland) |
| Alphabet | ~16.4% | ~16% | Foreign income + FDII |
| Microsoft | ~18.2% | ~18% | Foreign income (Ireland) |
| Meta | **~29.6% (FY2025)** | **~16%** | R&D credits + stock comp |

---

## The four recurring levers

Reconciling each company from 21% to its effective rate, almost all of the *recurring* movement
traces to four items:

- **Foreign income at lower rates.** Profit earned and taxed in lower-rate jurisdictions (Ireland
  recurs) pulls the blended rate down — the dominant driver for Apple and Microsoft.
- **FDII deduction.** A US deduction for income from serving foreign markets that taxes that income
  below 21%. Meaningful for Nvidia and Alphabet.
- **R&D credits.** Direct credits for research spending. A large item for Meta and Nvidia.
- **Stock-based compensation.** When stock awards vest above their grant-date value, the company
  gets an extra deduction. Material for Meta, Nvidia, and Alphabet.

State taxes generally push the rate slightly *up*, partially offsetting these.

---

## The most interesting finding: Meta's rate doubled in one year

Meta was the **lowest-taxed firm in the group in FY2024 at ~12%** — and then jumped to **~30% in
FY2025**, the highest in the peer set. That's not a higher underlying rate; it's almost entirely
**one line in the reconciliation:**

| Meta FY2025 reconciliation | Impact |
|----------------------------|--------|
| Statutory federal rate | +21.0 |
| State & local, net | −0.2 |
| Foreign tax effects | +1.7 |
| R&D tax credits | −4.6 |
| U.S. foreign tax credits | −1.6 |
| **Valuation allowance (OBBBA) — one-time** | **+13.9** |
| Changes in unrecognized tax benefits | +3.6 |
| Excess stock-comp benefits | −5.0 |
| Other | +0.8 |
| **Effective rate** | **29.6%** |

The recurring levers (R&D credits −4.6, stock comp −5.0) are still doing their normal work. What
blew up the rate was a **+13.9-point valuation-allowance charge** — a ~$12B, **non-cash** writedown
of deferred tax assets, driven by the **OBBBA tax-law change** (which altered how R&D costs are
treated for tax). Strip that one item out and Meta's rate is back near **~16%**, right in line with
its peers and its own history.

This is the mirror image of **Apple's FY2024 spike to ~24%**, which came from a one-time ~$10B
EU/Ireland State Aid charge. Two different companies, two different one-time items, same lesson:
**the headline rate and the underlying rate can be very different numbers.**

---

## What's interesting

**Same playbook, different emphasis.** Apple is a foreign-income story — its savings are about where
profit is booked. Meta is a domestic-incentive story — R&D credits and stock-comp deductions do the
recurring work. Nvidia sits in between. Same toolkit, weighted to the business.

**Stock-comp deductions are quietly significant.** For the high-equity-pay firms (Meta, Nvidia,
Alphabet), the benefit from vesting stock awards shaves multiple points off the rate — a direct link
between how these firms pay employees and what they pay in tax.

**Tax-law changes ripple across the whole sector.** The same OBBBA R&D provision that hit Meta's
FY2025 rate is the kind of change that moves *every* big tech ETR — a reminder that these rates sit
on top of shifting legislation, not bedrock.

---

## Why this matters

Effective tax rate flows straight into free cash flow and therefore into valuation — a firm taxed
at 15% keeps more of every dollar than one at 21%. For an analyst, knowing *why* a rate is what it
is also tells you how *durable* it is: a rate built on structural advantages (foreign operations) is
more reliable than one swung by one-time items. And as Meta shows, a rate can spike for a
**non-cash, one-time** reason that says nothing about the underlying business — which is exactly the
kind of thing you only catch by reading the reconciliation, not the headline number.

---

## A note on method (and a catch worth highlighting)

The effective rates here were pulled live from financial data; the reconciliation line items were
read by hand from each 10-K tax footnote. That split mattered: the live data first showed Meta at
~30%, which contradicted an earlier draft built on Meta's FY2024 footnote. Rather than dismiss the
live number, checking it against Meta's actual 10-K confirmed the ~30% was real and surfaced the
OBBBA valuation-allowance charge behind it. The lesson baked into this project: trust the filing,
verify surprising numbers at the source, and let the reconciliation explain the *why*.

---

## Limitations

- **Reconciliation figures are transcribed from 10-K footnotes** and should be verified against
  current filings (Meta's FY2025 figures were confirmed at the source; the others should be
  spot-checked the same way).
- **ETR is a book measure**, not cash taxes paid — the two can differ materially in a given year
  (Meta's FY2025 charge was non-cash).
- **Tax law changes.** FDII, GILTI, R&D expensing, OBBBA, and credits all shift with legislation, so
  these rates are a snapshot, not a constant.
- **Peer set is five firms** — a clean illustration, not a statistical study of the sector.

---

*Educational and research project. Not tax or investment advice.*
