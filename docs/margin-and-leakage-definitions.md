[Back to README](../README.md) · [Open the Excel workbook](../template/b2b-price-waterfall-calculator-template.xlsx) · [Use the online calculator](https://configure.win/resources/price-waterfall-calculator)

# Margin and leakage definitions

This guide explains the relationship between front-end margin, pocket margin, margin leakage, margin delta and supplier-side incentives in the workbook.

## The two commercial views

The workbook provides two profitability views.

### Front-end view

```text
Invoice price
− Base cost
= Front-end gross profit
```

```text
Front-end margin
= Front-end gross profit ÷ Invoice price
```

This view includes:

- customer discount;
- promotional discount;
- base cost.

It does not yet include:

- freight or service concession;
- customer rebate;
- vendor incentive.

### Pocket view

```text
Pocket price
− Effective cost
= Pocket gross profit
```

```text
Pocket margin
= Pocket gross profit ÷ Pocket price
```

This view includes the full set of modelled customer-facing deductions and the expected supplier-side vendor incentive.

## Why front-end and pocket margin can differ

The two margins use different prices and different costs.

| Measure | Price basis | Cost basis |
| --- | --- | --- |
| Front-end margin | Invoice price | Base cost |
| Pocket margin | Pocket price | Effective cost |

Customer-facing concessions and rebates reduce pocket price.

Vendor incentive reduces effective cost.

The final relationship depends on the size of both effects.

## Margin delta

```text
Margin delta
= Pocket margin − Front-end margin
```

Interpretation:

- **Negative delta** — pocket margin is lower than front-end margin.
- **Zero delta** — both margin percentages are equal.
- **Positive delta** — pocket margin is higher than front-end margin.

A positive delta can occur when the vendor incentive’s effect on effective cost more than offsets the effect of post-invoice customer deductions in the percentage calculation.

A negative delta can occur when concessions and customer rebates reduce realised price more than the vendor incentive improves cost economics.

The delta is expressed in percentage points.

## Margin leakage

The workbook defines:

```text
Margin leakage
= Gross list value − Pocket price
```

This equals the total modelled customer-facing reduction from list value:

```text
Customer discount
+ Promotional discount
+ Freight or service concession
+ Customer rebate
```

Vendor incentive is not included in leakage because it affects cost rather than customer price.

## Leakage percentage

```text
Leakage percentage
= Margin leakage ÷ Gross list value
```

This expresses the reduction from list value to pocket price as a share of gross list value.

If gross list value is zero or unavailable, the formula returns blank.

## Leakage does not automatically equal lost profit

The workbook measures the monetary reduction from list to pocket price. It does not determine whether a deduction is:

- contractually required;
- strategically justified;
- temporary;
- avoidable;
- recovered through another commercial mechanism.

The term should therefore be interpreted as a price-realisation measure within this model, not as an automatic statement that the full amount should be removed.

## Customer rebate versus vendor incentive

### Customer rebate

- Customer-facing
- Off-invoice benefit or credit
- Reduces pocket price
- Increases margin leakage
- Can reduce pocket gross profit and pocket margin

### Vendor incentive

- Supplier-side
- Reduces effective cost
- Does not reduce pocket price
- Does not increase margin leakage
- Can increase pocket gross profit and pocket margin

This distinction is central to the workbook.

## Largest customer-facing deduction

The Deal log identifies the largest calculated amount among:

1. Customer discount
2. Promotional discount
3. Freight or service concession
4. Customer rebate

Use this field to identify the first adjustment requiring contextual review.

It does not include vendor incentive and does not establish the root cause.

When values tie, the formula returns the first item in the order above.

## Example

The fictional worked example contains:

| Item | Amount |
| --- | ---: |
| Gross list value | €60,000 |
| Customer discount | €5,000 |
| Promotional discount | €2,000 |
| Freight or service concession | €1,500 |
| Customer rebate | €2,500 |
| Pocket price | €49,000 |
| Margin leakage | €11,000 |
| Leakage percentage | 18.3% |

The largest customer-facing deduction is the customer discount at €5,000.

The same example contains:

| Profitability measure | Result |
| --- | ---: |
| Invoice price | €53,000 |
| Base cost | €38,000 |
| Front-end gross profit | €15,000 |
| Front-end margin | 28.3% |
| Pocket price | €49,000 |
| Effective cost | €36,500 |
| Pocket gross profit | €12,500 |
| Pocket margin | 25.5% |
| Margin delta | −2.8 percentage points |

The €1,500 vendor incentive improves effective cost, but the €4,000 of post-invoice customer-facing deductions still leave pocket margin below front-end margin.

## Interpretation checklist

Before drawing a conclusion, confirm:

- the percentage bases are correct;
- customer and supplier adjustments are separated;
- the entered values use one currency;
- expected rebates and incentives are sufficiently supported for the analysis;
- blank adjustments genuinely mean zero;
- the threshold is the user’s own policy;
- compared deals are sufficiently similar.

## Related documentation

- [Definitions](definitions.md)
- [Methodology](methodology.md)
- [Price-waterfall methodology](price-waterfall-methodology.md)
- [Worked example](worked-example.md)
- [Limitations](limitations.md)
