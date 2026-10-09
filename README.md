# HDFC Bank Key Fact Statement (KFS) Loan Calculator

A clean, modern, responsive single-page web application (HTML5 + CSS3 + Vanilla JavaScript) that recreates an official-grade **HDFC Bank Key Fact Statement (KFS)** loan amortisation and APR disclosure calculator.

Compliant with RBI harmonized disclosure standards for retail loans.

---

## Features

- **Live Dynamic Computations:** Real-time updates on every keystroke or slider change.
- **Direct Interest Rate Input:** Enter the annual interest rate directly ($R\%$) with an optional toggle for floating-rate **Benchmark ($B$) + Spread ($S$)** split.
- **Indian Number Formatting:** Native Lakh & Crore formatting with verbal preview (`Intl.NumberFormat('en-IN')`).
- **Exact Bank Rounding:** Implements integer rupee ceiling rounding matching HDFC Bank KFS sheets and RBI formulas.
- **Amortisation Schedule:**
  - Configurable row indexing (Start at `0` for HDFC Bank format, or Start at `1`).
  - Columns: Instalment No., Due Date, Opening Balance, Principal, Interest, Instalment, Closing Balance.
  - Sticky table headers, pagination ($12$, $24$, $60$, or All rows), and jump-to-instalment search.
  - One-click CSV export (`.csv`).
- **Rate-Change Impact Sensitivity:**
  - Option A: Revised EMI with fixed tenure.
  - Option B: Revised tenure (EPIs) with fixed EMI: $n' = \left\lceil \frac{-\ln(1 - P \cdot r' / \text{EMI})}{\ln(1 + r')} \right\rceil$.
  - Editable BPS delta (default 25 bps).
- **Upfront Fee Schedule & Effective APR:**
  - Editable breakdown: Processing fees, Insurance charges, Administrative fees, CERSAI registration, Any other charges.
  - 18% GST toggle on lender processing fees.
  - **Sheet APR** ($R\%$) vs. **Effective APR** (solved via Newton-Raphson IRR on net disbursed amount).
- **Part-Prepayment Simulator:**
  - Lump-sum prepayment testing with Tenure Reduction or Monthly EMI Reduction.
  - Live calculation of total interest saved and months saved.
- **Visual Analytics:**
  - Outstanding principal vs. cumulative interest curve over time.
  - Doughnut breakdown of principal vs. interest vs. upfront fees.
- **Official KFS Statement & Print Export:**
  - Formal RBI Harmonized Disclosure format ready to print or save as PDF (`Cmd+P` / `Ctrl+P`).
- **Presets Included:**
  - **Home Loan:** ₹ 2,00,00,000 | 360 months | 7.75%
  - **Insurance Premium Funding:** ₹ 15,96,020 | 240 months | 7.25%

---

## Acceptance Test Verifications

| Test Case | Sanctioned ($P$) | Tenor ($n$) | Rate ($R$) | EMI | Row 0 Interest | Row 0 Principal | $+25\text{ bps}$ Scenario | Upfront Fees |
|:---|:---|:---|:---|:---|:---|:---|:---|:---|
| **Preset 1 (Home)** | ₹ 2,00,00,000 | 360 m | 7.75% | **₹ 1,43,283** | ₹ 1,29,167 | ₹ 14,116 | at 8.00%: **₹ 1,46,753** or **402 EPIs** | ₹ 9,100 |
| **Preset 2 (Insurance)** | ₹ 15,96,020 | 240 m | 7.25% | **₹ 12,615** | ₹ 9,643 | ₹ 2,972 | at 7.50%: **₹ 12,858** or **252 EPIs** | ₹ 9,100 |

---

## Local Development

Open `index.html` directly in any web browser, or serve it locally:

```bash
python3 -m http.server 8080
```

Then visit [http://localhost:8080](http://localhost:8080).

---

## Disclaimer

*Illustrative calculator, not an official bank document. Calculations strictly conform to HDFC Bank KFS formulas & RBI Master Directions. Final terms, charges, and amortization are subject to bank sanction and terms.*
