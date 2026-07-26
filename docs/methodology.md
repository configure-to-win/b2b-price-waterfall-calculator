[Back to README](../README.md) · [Open the Excel workbook](../template/b2b-price-waterfall-calculator-template.xlsx) · [Use the online calculator](https://configure.win/resources/price-waterfall-calculator)

# Methodology

This document specifies the workbook’s calculation model and formula logic. For guidance on running a consistent analysis, see [Price-waterfall methodology](price-waterfall-methodology.md).

## Calculation sequence

The model moves through three connected views of the deal:

1. **Price realisation** — gross list value to invoice price to pocket price
2. **Cost economics** — base cost to effective cost
3. **Profitability** — front-end and pocket gross profit and margin

## Core inputs

```text
Gross list value
= List price per unit × Quantity

Base cost
= Unit cost before vendor incentive × Quantity
```

The calculation requires list price and quantity for gross list value. It requires unit cost and quantity for base cost.

## Adjustment modes

In **Calculator** and **Deal log**, each adjustment can use:

- **Amount** — the entered value is used as a monetary amount.
- **Percentage** — the entered value is multiplied by the relevant percentage basis.

### Customer discount

```text
Customer discount amount
= Entered amount

or

= Gross list value × Entered percentage
```

### Promotional discount

```text
Promotional discount amount
= Entered amount

or

= Gross list value × Entered percentage
```

### Freight or service concession

```text
Freight or service concession amount
= Entered amount

or

= Invoice price × Entered percentage
```

### Customer rebate

```text
Customer rebate amount
= Entered amount

or

= Invoice price × Entered percentage
```

### Vendor incentive

```text
Vendor incentive amount
= Entered amount

or

= Base cost × Entered percentage
```

A customer rebate is a customer-facing deduction and reduces pocket price. A vendor incentive is supplier-side and reduces effective cost.

## Price realisation

### Invoice price

```text
Invoice price
= Gross list value
− Customer discount
− Promotional discount
```

### Pocket price

```text
Pocket price
= Invoice price
− Freight or service concession
− Customer rebate
```

### Margin leakage

```text
Margin leakage
= Gross list value − Pocket price
```

Because pocket price already includes all four customer-facing deductions:

```text
Margin leakage
= Customer discount
+ Promotional discount
+ Freight or service concession
+ Customer rebate
```

when the entered values and percentage bases are calculated consistently.

### Leakage percentage

```text
Leakage percentage
= Margin leakage ÷ Gross list value
```

If gross list value is zero or unavailable, the percentage formula returns blank.

## Cost economics

### Effective cost

```text
Effective cost
= Base cost − Vendor incentive
```

The vendor incentive does not reduce invoice price or pocket price in this model.

## Front-end profitability

```text
Front-end gross profit
= Invoice price − Base cost

Front-end margin
= Front-end gross profit ÷ Invoice price
```

Front-end margin uses the price visible after customer and promotional discounts, but before off-invoice concessions and customer rebates. It also uses base cost before supplier-side incentive.

If invoice price is zero or unavailable, the margin formula returns blank.

## Pocket profitability

```text
Pocket gross profit
= Pocket price − Effective cost

Pocket margin
= Pocket gross profit ÷ Pocket price
```

Pocket margin includes customer-facing concessions and rebates in price, and the expected vendor incentive in effective cost.

If pocket price is zero or unavailable, the margin formula returns blank.

## Margin delta

```text
Margin delta
= Pocket margin − Front-end margin
```

The result is a percentage-point difference between two margins that use different price and cost bases.

- A negative delta means pocket margin is below front-end margin.
- A positive delta means pocket margin is above front-end margin.
- The delta is not a monetary value.

## Largest customer-facing deduction

The **Deal log** compares the calculated monetary amounts for:

1. Customer discount
2. Promotional discount
3. Freight or service concession
4. Customer rebate

It returns the label of the largest amount.

When values are tied, the formula resolves the tie in the order above. If all four amounts are zero and a Deal ID is present, the result can therefore display **Customer discount**. Interpret the field only when at least one customer-facing deduction is greater than zero.

Vendor incentive is excluded because it is supplier-side and affects effective cost rather than customer price.

## Approval signal

The user may enter a minimum acceptable pocket margin.

```text
If threshold is blank:
    No threshold set

If pocket margin ≥ threshold:
    Within configured threshold

If pocket margin < threshold:
    Commercial review required
```

The Calculator also displays:

```text
Difference
= Pocket margin − Minimum acceptable pocket margin
```

This signal reflects only the user-entered threshold.

## Deal log formulas

The Deal log applies the aggregate formulas to each row independently.

Rows 6–105 provide capacity for 100 deals.

A row’s derived results depend on its own:

- list price;
- quantity;
- unit cost;
- adjustment modes and values;
- threshold.

The workbook does not convert currencies or aggregate the Deal log into a portfolio result automatically.

## Quote-line formulas

The **Quote lines** worksheet uses a fixed line-input model.

### Line-level price calculations

```text
Line gross list value
= Quantity × Unit list price

Line customer discount amount
= Line gross list value × Customer discount %

Line promotional discount amount
= Line gross list value × Promotional discount %

Line invoice price
= Line gross list value
− Line customer discount amount
− Line promotional discount amount

Line pocket price
= Line invoice price
− Freight or service concession amount
− Customer rebate amount
```

### Line-level cost and margin calculations

```text
Line base cost
= Quantity × Unit cost

Line effective cost
= Line base cost − Vendor incentive amount

Line front-end gross profit
= Line invoice price − Line base cost

Line front-end margin
= Line front-end gross profit ÷ Line invoice price

Line pocket gross profit
= Line pocket price − Line effective cost

Line pocket margin
= Line pocket gross profit ÷ Line pocket price

Line margin leakage
= Line gross list value − Line pocket price
```

The line model uses percentage inputs only for the two invoice discounts. Concessions, customer rebates and vendor incentives are entered as monetary amounts.

## Selected-quote aggregation

The selected-quote summary sums each monetary field for rows whose Quote ID matches the selected Quote ID.

```text
Selected quote gross list value
= Sum of matching line gross list values

Selected quote invoice price
= Sum of matching line invoice prices

Selected quote pocket price
= Sum of matching line pocket prices

Selected quote base cost
= Sum of matching line base costs

Selected quote vendor incentive
= Sum of matching line vendor incentives
```

The quote-level profit and margin formulas are:

```text
Selected quote front-end gross profit
= Sum of matching line front-end gross profit

Selected quote front-end margin
= Selected quote front-end gross profit
÷ Selected quote invoice price

Selected quote pocket gross profit
= Sum of matching line pocket gross profit

Selected quote pocket margin
= Selected quote pocket gross profit
÷ Selected quote pocket price
```

This weighting is mathematically different from averaging line-level percentages.

## Blank and error handling

The workbook applies several blank-result rules:

- Gross list value remains blank until list price and quantity are available.
- Base cost remains blank until unit cost and quantity are available.
- Margin percentages return blank when their denominator is zero or unavailable.
- A selected-quote summary remains blank when no line matches the selected Quote ID.
- In arithmetic formulas, blank adjustment cells are treated as zero once the required base value exists.

A blank adjustment therefore behaves as no adjustment, not as an explicitly unknown value. Document uncertainty in Notes rather than relying on a blank to preserve an “unknown” state.

## Worked example

The workbook’s fictional example produces:

| Metric | Result |
| --- | ---: |
| Gross list value | €60,000 |
| Invoice price | €53,000 |
| Pocket price | €49,000 |
| Base cost | €38,000 |
| Effective cost | €36,500 |
| Front-end margin | 28.3% |
| Pocket margin | 25.5% |
| Margin leakage | €11,000 |
| Leakage percentage | 18.3% |
| Margin delta | −2.8 percentage points |
| Approval signal | Commercial review required |

See [Worked example](worked-example.md) for the complete reconciliation.
