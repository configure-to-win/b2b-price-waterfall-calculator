[Back to README](../README.md) · [Open the Excel workbook](../template/b2b-price-waterfall-calculator-template.xlsx) · [Use the online calculator](https://configure.win/resources/price-waterfall-calculator)

# Deal log guide

Use the **Deal log** to record and compare up to 100 deals using the workbook’s aggregate price-waterfall model.

The input and formula rows run from row 6 through row 105.

## Column structure

| Columns | Group |
| --- | --- |
| A–D | Deal identification and context |
| E–G | Core price and cost inputs |
| H–Q | Adjustment modes and values |
| R | Optional minimum pocket margin |
| S–AF | Derived results |
| AG | Notes |

## Identification and context

| Column | Field | Guidance |
| --- | --- | --- |
| A | Deal ID | Enter a unique reference for the deal. The largest-deduction field remains blank when Deal ID is blank. |
| B | Measurement date | Record the date used for the analysis or deal snapshot. |
| C | Customer or segment | Add the customer, segment or comparison group. |
| D | Currency | Select EUR, USD, GBP, CAD, AUD, CHF, DKK, NOK or SEK. |

The currency field does not convert values.

## Core inputs

| Column | Field | Guidance |
| --- | --- | --- |
| E | List price per unit | Enter the list price for one unit. |
| F | Quantity | Enter the number of units. |
| G | Unit cost | Enter cost per unit before vendor incentive. |

Gross list value requires E and F.

Base cost requires G and F.

## Adjustment modes and values

Each adjustment uses two columns: a mode and an entered value.

| Columns | Adjustment | Percentage basis |
| --- | --- | --- |
| H–I | Customer discount | Gross list value |
| J–K | Promotional discount | Gross list value |
| L–M | Freight or service concession | Invoice price |
| N–O | Customer rebate | Invoice price |
| P–Q | Vendor incentive | Base cost |

Select:

- **Amount** to use the value directly;
- **Percentage** to multiply the value by the stated basis.

Enter 10% as `10%` or `0.10`, not `10`.

Blank adjustment values are treated as zero once the required basis exists.

## Optional threshold

| Column | Field | Guidance |
| --- | --- | --- |
| R | Minimum pocket margin | Enter the user’s own minimum threshold or leave blank. |

The threshold does not change the economics. It changes only the Approval signal.

## Derived results

### Price realisation

| Column | Field | Formula |
| --- | --- | --- |
| S | Gross list value | List price per unit × quantity |
| T | Invoice price | Gross list value − customer discount − promotional discount |
| U | Pocket price | Invoice price − concession − customer rebate |

### Cost economics

| Column | Field | Formula |
| --- | --- | --- |
| V | Base cost | Unit cost × quantity |
| W | Effective cost | Base cost − vendor incentive |

### Profitability

| Column | Field | Formula |
| --- | --- | --- |
| X | Front-end gross profit | Invoice price − base cost |
| Y | Front-end margin | Front-end gross profit ÷ invoice price |
| Z | Pocket gross profit | Pocket price − effective cost |
| AA | Pocket margin | Pocket gross profit ÷ pocket price |

### Leakage and comparison

| Column | Field | Formula or meaning |
| --- | --- | --- |
| AB | Margin leakage | Gross list value − pocket price |
| AC | Leakage percentage | Margin leakage ÷ gross list value |
| AD | Margin delta | Pocket margin − front-end margin |
| AE | Largest customer-facing deduction | Highest monetary amount among the four customer-facing deductions |
| AF | Approval signal | Compares pocket margin with the threshold in R |

### Notes

| Column | Field | Guidance |
| --- | --- | --- |
| AG | Notes | Record assumptions, missing information, unusual terms or comparison context. |

## Largest-deduction behavior

The workbook compares the calculated amounts for:

1. Customer discount
2. Promotional discount
3. Freight or service concession
4. Customer rebate

If two or more values tie, it returns the first item in this order.

If all four amounts are zero and a Deal ID is present, it can return **Customer discount**. Use the field only when at least one deduction is greater than zero.

## Approval-signal behavior

The result is:

- **No threshold set** when R is blank;
- **Within configured threshold** when pocket margin is equal to or above R;
- **Commercial review required** when pocket margin is below R.

The workbook does not provide the threshold.

## Recommended entry procedure

1. Enter Deal ID, date, customer or segment and currency.
2. Enter list price, quantity and unit cost.
3. Select the adjustment mode for each item.
4. Enter every known adjustment.
5. Enter a threshold only when required for the analysis.
6. Review the derived values from left to right.
7. Confirm that the largest-deduction result is meaningful.
8. Document missing or estimated values in Notes.
9. Repeat using the same definitions for comparable deals.

## Comparing rows

Before comparing deals:

- use consistent definitions;
- convert currencies externally when required;
- compare sufficiently similar deal types;
- distinguish actual deals from averages;
- confirm that blank adjustments mean zero;
- use the same threshold policy where threshold signals are compared.

Useful comparison fields include:

- invoice price as a share of gross list value;
- pocket price as a share of gross list value;
- front-end margin;
- pocket margin;
- leakage percentage;
- margin delta;
- largest deduction;
- approval signal.

The workbook does not automatically create a portfolio average or benchmark.

## Data-quality checks

For each row, confirm:

- Deal ID is present;
- currency is selected;
- quantity uses the intended unit;
- list price and cost are on the same unit basis;
- percentage values use decimal percentage storage;
- customer rebates and vendor incentives are classified correctly;
- no deduction unintentionally exceeds its price basis;
- the threshold is documented where used;
- Notes explain estimates or exceptions.

## Related documentation

- [Workbook guide](workbook-guide.md)
- [Methodology](methodology.md)
- [Price-waterfall methodology](price-waterfall-methodology.md)
- [Margin and leakage definitions](margin-and-leakage-definitions.md)
- [Limitations](limitations.md)
