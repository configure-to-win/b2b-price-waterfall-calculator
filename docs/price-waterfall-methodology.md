[Back to README](../README.md) · [Open the Excel workbook](../template/b2b-price-waterfall-calculator-template.xlsx) · [Use the online calculator](https://configure.win/resources/price-waterfall-calculator)

# Price-waterfall methodology

This document describes how to conduct a consistent price-waterfall analysis using the workbook. It complements [Methodology](methodology.md), which specifies the formulas.

## 1. Define the unit of analysis

Choose one of three units:

### One aggregated deal

Use **Calculator** for one representative deal or for average values from a comparable group.

### Multiple individual deals

Use **Deal log** when each deal should remain a separate observation.

### One multi-line quote

Use **Quote lines** when product, service or vendor lines must be modelled separately before calculating quote-level economics.

Do not mix different units of analysis without explaining how values were aggregated.

## 2. Define the commercial boundary

The price waterfall begins with:

```text
List price per unit × Quantity
```

and ends with:

```text
Pocket gross profit
= Pocket price − Effective cost
```

The model includes:

- customer discounts;
- promotional discounts;
- freight or service concessions;
- customer rebates;
- unit cost;
- vendor incentives.

It does not include settlement, accrual or accounting processes.

## 3. Establish one currency basis

Select the currency used for the deal or quote.

Before entry:

1. identify the currency of each source value;
2. convert values externally where required;
3. use one currency within the calculation;
4. preserve the conversion context in Notes when relevant.

The workbook does not perform currency conversion.

## 4. Confirm list price, quantity and cost

Start with the three core commercial inputs:

- list price per unit;
- quantity;
- unit cost before vendor incentive.

These establish:

```text
Gross list value
```

and:

```text
Base cost
```

Check that price and cost use the same unit basis as quantity.

## 5. Classify every adjustment correctly

Separate adjustments by commercial side and waterfall position.

### Customer-facing deductions before invoice price

- Customer discount
- Promotional discount

### Customer-facing deductions after invoice price

- Freight or service concession
- Customer rebate

### Supplier-side cost adjustment

- Vendor incentive

Do not enter a vendor incentive as a customer rebate or vice versa. They affect different parts of the model.

## 6. Apply the correct percentage basis

When using Percentage mode:

| Adjustment | Basis |
| --- | --- |
| Customer discount | Gross list value |
| Promotional discount | Gross list value |
| Freight or service concession | Invoice price |
| Customer rebate | Invoice price |
| Vendor incentive | Base cost |

Enter percentages as Excel percentages, for example `10%`, or as decimal values such as `0.10`.

## 7. Review price realisation first

Read the customer-price sequence:

```text
Gross list value
→ Invoice price
→ Pocket price
```

Ask which monetary deductions explain each step.

### Gross list value to invoice price

This difference consists of:

- customer discount;
- promotional discount.

### Invoice price to pocket price

This difference consists of:

- freight or service concession;
- customer rebate.

### Gross list value to pocket price

This total difference is margin leakage as defined by the workbook.

## 8. Review cost economics separately

Read the supplier-cost sequence:

```text
Base cost
→ Effective cost
```

The difference is the expected vendor incentive.

A vendor incentive can improve pocket profitability without changing pocket price.

## 9. Compare front-end and pocket profitability

Review:

```text
Front-end gross profit
Front-end margin
Pocket gross profit
Pocket margin
Margin delta
```

Front-end economics use invoice price and base cost.

Pocket economics use pocket price and effective cost.

Do not interpret front-end margin as the final deal margin when concessions, customer rebates or vendor incentives are material.

## 10. Apply the optional threshold

Enter a minimum pocket margin only when it represents the user’s own commercial policy for the analysis.

Interpret the output as:

- a comparison signal;
- a reason to review the entered economics;
- not an automatic approval decision.

Record the threshold used when sharing results.

## 11. Identify the largest customer-facing deduction

In the Deal log, use the Largest customer-facing deduction field to identify the highest calculated deduction amount.

Then review the underlying context in Notes.

The result indicates where the largest entered reduction sits. It does not determine whether the adjustment is incorrect or avoidable.

## 12. Analyse multiple deals consistently

Before comparing Deal log rows:

1. use consistent definitions;
2. use one currency basis or convert externally;
3. compare sufficiently similar deals;
4. confirm that blank adjustments genuinely mean zero;
5. preserve customer, segment and date context;
6. distinguish actual deal values from averages or estimates.

Review patterns across:

- invoice-price realisation;
- pocket-price realisation;
- front-end margin;
- pocket margin;
- leakage percentage;
- margin delta;
- threshold signals;
- largest deductions.

## 13. Analyse multi-line quotes correctly

For Quote lines:

1. use the same Quote ID for every line belonging to the quote;
2. use one currency basis;
3. enter discounts as percentages;
4. enter concessions, rebates and incentives as amounts;
5. confirm that all intended lines are present;
6. select the Quote ID in the summary;
7. use the aggregated quote margins.

Do not average line-level margins. The workbook calculates quote-level margins from aggregated prices, costs and gross profits.

## 14. Reconcile the result

For an aggregate analysis, confirm:

```text
Gross list value
− Customer discount
− Promotional discount
= Invoice price
```

```text
Invoice price
− Freight or service concession
− Customer rebate
= Pocket price
```

```text
Base cost
− Vendor incentive
= Effective cost
```

For a quote-line analysis, compare the selected-quote summary with the sum of the matching line values.

## 15. Report the result within scope

When sharing results, state:

- unit of analysis;
- currency;
- measurement date where relevant;
- whether inputs are actual, expected or averaged;
- customer-facing deductions included;
- vendor incentive included;
- threshold used;
- whether all inputs were known;
- that the workbook does not provide an external benchmark or recommended policy.

## Recommended interpretation sequence

Use this order:

1. Gross list value
2. Invoice price
3. Pocket price
4. Margin leakage
5. Base cost
6. Effective cost
7. Front-end margin
8. Pocket margin
9. Margin delta
10. Threshold signal
11. Largest deduction and Notes

This sequence keeps price realisation, cost economics and policy interpretation separate.
