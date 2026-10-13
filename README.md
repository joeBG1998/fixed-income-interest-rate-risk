# Fixed Income Interest Rate Risk & Hedging

End-to-end fixed-income portfolio risk project covering bond valuation, yield-curve modelling, duration and convexity, DV01, key-rate duration, stress testing and hedge construction.

## Project Overview

This project develops a fixed-income interest-rate risk framework for a multi-bond portfolio.

The analysis progresses from individual bond pricing and yield sensitivity to portfolio-level duration, DV01 and key-rate risk. It then evaluates portfolio behaviour under parallel and non-parallel yield-curve shocks and constructs alternative hedging strategies.

The project demonstrates the distinction between hedging aggregate interest-rate exposure and managing the distribution of risk across the yield curve.

## Methodology

The project covers:

- Bond pricing from yield to maturity
- Price-yield relationship
- Yield-to-maturity estimation
- Macaulay duration
- Modified duration
- Convexity
- Duration and convexity price approximations
- Yield-curve interpolation
- Spot-curve bond valuation
- Fixed-income portfolio construction
- Portfolio duration and convexity
- Parallel and non-parallel yield-curve stress testing
- DV01
- Key-rate duration
- Localized yield-curve shocks
- Single-instrument DV01 hedging
- Multi-instrument key-rate hedging
- Constrained least-squares hedge optimization
- Hedge effectiveness and stress testing

## Portfolio

The illustrative portfolio contains four fixed-income securities across different maturities:

| Instrument | Face Value | Coupon | Maturity |
|---|---:|---:|---:|
| 2Y Note | $1,000,000 | 3.5% | 2 years |
| 5Y Note | $1,000,000 | 4.0% | 5 years |
| 10Y Note | $1,000,000 | 4.5% | 10 years |
| 20Y Bond | $1,000,000 | 5.0% | 20 years |

The initial portfolio market value is approximately **$4.08 million**.

## Key Risk Metrics

The portfolio has:

- Modified duration of approximately **6.94**
- Convexity of approximately **83.40**
- DV01 of approximately **$2,832 per basis point**

Exact repricing under a parallel 1 bp yield shift produces a DV01 of approximately **$2,826**, demonstrating the accuracy of the duration-based approximation for small yield changes.

## Yield-Curve Stress Testing

The portfolio is evaluated under several interest-rate scenarios, including:

- Parallel +100 bp
- Parallel -100 bp
- Bear steepener
- Bear flattener

The analysis uses full bond repricing rather than relying exclusively on duration approximations.

This captures the nonlinear price response of fixed-income securities and differences in sensitivity across maturities.

## Key-Rate Duration

Aggregate duration measures exposure to broad changes in interest rates but does not identify where that exposure is located along the yield curve.

Key-rate duration is therefore estimated at:

- 2Y
- 5Y
- 10Y
- 20Y

The analysis demonstrates that a portfolio can have its aggregate DV01 substantially hedged while retaining meaningful exposure to localized yield-curve movements.

## Hedging Analysis

Two practical hedge structures are examined.

### Single 10Y DV01 Hedge

A 10-year instrument is used to offset aggregate portfolio DV01.

The required hedge notional is approximately:

**$3.47 million**

This hedge performs strongly under broad yield-curve scenarios because those scenarios contain substantial common movements across maturities.

However, localized key-rate shocks demonstrate that aggregate DV01 neutrality does not imply neutrality to changes in yield-curve shape.

### Constrained 5Y/10Y Key-Rate Hedge

A second hedge is constructed using only the 5-year and 10-year instruments.

Because two hedge instruments cannot independently neutralize four key-rate exposures, the hedge notionals are estimated using least squares.

Approximate hedge positions are:

- **5Y:** -$1.13 million
- **10Y:** -$1.36 million

The constrained hedge reduces the norm of the portfolio's key-rate DV01 vector by approximately **32.5%**.

Under the broad stress scenarios, it reduces absolute portfolio P&L by approximately **52–64%**.

## Hedge Trade-Off

The two strategies illustrate an important fixed-income risk-management trade-off.

| Strategy | Gross Hedge Notional | Portfolio Value Ratio |
|---|---:|---:|
| Single 10Y DV01 Hedge | $3.47m | 85.0% |
| Constrained 5Y/10Y Hedge | $2.49m | 61.0% |

The single-instrument hedge provides stronger protection against the selected broad rate scenarios but requires greater gross notional and does not eliminate curve-shape risk.

The constrained hedge requires less gross positioning and targets maturity-specific exposures, but substantial residual risk remains where the available hedge instruments cannot span the portfolio's yield-curve exposure.

## Key Takeaways

- Bond prices exhibit a nonlinear inverse relationship with yields.
- Duration provides an effective first-order approximation for small yield changes.
- Convexity materially improves approximation accuracy for larger shocks.
- Portfolio DV01 measures aggregate interest-rate sensitivity but does not reveal where risk is concentrated along the yield curve.
- Key-rate duration provides a more granular view of curve exposure.
- A portfolio can be DV01-neutral while remaining exposed to non-parallel yield-curve movements.
- Hedge effectiveness depends on the risk factor being targeted and the instruments available.
- More complete hedging generally requires additional instruments, gross positioning and implementation capacity.

## Technologies

- Python
- NumPy
- pandas
- SciPy
- Matplotlib
- Jupyter Notebook

## Repository Structure

```text
fixed-income-interest-rate-risk/
│
├── fixed_income_interest_rate_risk.ipynb
├── requirements.txt
└── README.md

