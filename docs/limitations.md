[Back to README](../README.md) · [Open the Excel workbook](../template/b2b-price-waterfall-calculator-template.xlsx) · [Use the online calculator](https://configure.win/resources/price-waterfall-calculator)

# Limitations

The B2B Price Waterfall Calculator is a practical commercial calculation tool. The following boundaries should be considered when entering, comparing or reporting results.

## No industry benchmark or target

The workbook does not provide:

- an industry-average margin;
- a target pocket margin;
- an acceptable leakage level;
- a recommended discount;
- a recommended approval threshold;
- an approval decision.

Appropriate values vary by industry, product mix, customer, channel and commercial policy.

## Expected values are not settled values

The model uses expected commercial values. It does not perform:

- rebate settlement;
- claim submission;
- accrual accounting;
- vendor-program administration;
- financial reconciliation.

An entered customer rebate or vendor incentive is included in the model because the user entered it. The workbook does not confirm eligibility, settlement or receipt.

## No currency conversion

Currency selections control the displayed or intended currency. They do not convert values.

Before combining or comparing values:

- use one currency within each Calculator or Deal log record;
- use one currency for all lines belonging to a selected quote;
- convert source values outside the workbook when necessary;
- do not aggregate rows with different currencies without a separate conversion method.

## Blank adjustment cells behave as zero

Once a required calculation base exists, Excel arithmetic treats a blank adjustment cell as zero.

A blank adjustment therefore means **no adjustment included in the calculation**, not **unknown adjustment**.

When an adjustment is unknown:

- document the uncertainty in Notes;
- avoid presenting the result as complete;
- update the row when the value becomes available.

## Missing core inputs suppress dependent results

Gross list value requires list price and quantity.

Base cost requires unit cost and quantity.

If a required base is missing, dependent profit and margin fields can remain blank. Margin formulas also return blank when invoice price, pocket price or gross list value is zero.

## Percentage entry requires care

Calculator and Deal log adjustment-value cells use general numeric formatting. Enter 10% as:

```text
10%
```

or:

```text
0.10
```

Entering `10` in Percentage mode represents ten times the calculation base, not 10%.

Quote-line discount columns use percentage formatting, but the same stored-value principle applies.

## Percentage bases are fixed

The workbook applies:

- customer discount to gross list value;
- promotional discount to gross list value;
- concession to invoice price;
- customer rebate to invoice price;
- vendor incentive to base cost.

It does not support an alternative compounding order or another percentage basis without changing the formulas.

## Input models differ by worksheet

Calculator and Deal log allow Amount or Percentage mode for all five adjustments.

Quote lines uses:

- percentage for customer discount;
- percentage for promotional discount;
- amount for freight or service concession;
- amount for customer rebate;
- amount for vendor incentive.

Do not assume that inputs can be copied between worksheets without adapting their form.

## The workbook does not impose commercial caps

The formulas do not automatically prevent:

- discounts that exceed gross list value;
- concessions and rebates that exceed invoice price;
- vendor incentives that exceed base cost;
- negative invoice price;
- negative pocket price;
- negative effective cost.

Review unusual or negative outputs before using them in a commercial decision.

## Margin leakage is a price-realisation measure

Margin leakage is defined as gross list value minus pocket price.

It does not:

- include vendor incentive;
- equal lost profit automatically;
- distinguish required from avoidable deductions;
- determine whether a discount or rebate is commercially justified.

## Front-end and pocket margins use different bases

Front-end margin uses invoice price and base cost.

Pocket margin uses pocket price and effective cost.

Their difference is meaningful within this model, but it is not a direct monetary reconciliation and should not be interpreted without reviewing the underlying price and cost adjustments.

## Largest deduction is not a root-cause diagnosis

The Deal log returns the label of the largest calculated customer-facing deduction.

It does not establish:

- why the deduction was granted;
- whether it is contractual;
- whether it is avoidable;
- whether it caused an approval issue.

When two amounts are equal, the formula returns the first item in this order:

1. Customer discount
2. Promotional discount
3. Freight or service concession
4. Customer rebate

If all four values are zero and a Deal ID is present, the result can show Customer discount. Treat the field as meaningful only when at least one customer-facing deduction is greater than zero.

## Deal comparisons depend on comparability

The Deal log does not automatically classify or normalise differences in:

- product mix;
- quantity;
- customer;
- segment;
- channel;
- currency;
- commercial policy;
- measurement date.

Compare only deals or periods that are sufficiently comparable for the intended analysis.

## Quote-line capacity and selection

The Quote lines worksheet contains 50 calculation rows, from row 9 through row 58.

The selected-quote summary includes rows whose Quote ID matches the selected Quote ID. It does not verify:

- uniqueness of the Quote ID;
- currency consistency;
- completeness of all intended lines;
- consistency of customer or policy fields.

## Quote-level margins are weighted by value

The Quote lines summary calculates margin from aggregated monetary values. It does not average line-level percentages.

This is intentional, but users should not compare its result with a simple arithmetic average of line margins.

## Threshold signal is user-configured

The workbook does not recommend the threshold.

The approval signal is only a comparison between calculated pocket margin and the threshold entered by the user. It is not a governed approval workflow or final decision.

## Worked example boundary

The worked example is fictional and is not:

- customer data;
- benchmark data;
- advice;
- a target;
- a recommended policy.

## User responsibility

The user remains responsible for:

- input accuracy;
- currency consistency;
- classification of deductions and incentives;
- percentage bases;
- treatment of expected values;
- threshold selection;
- interpretation of results;
- suitability for the intended purpose.

For calculation rules, see [Methodology](methodology.md). For a consistent analysis procedure, see [Price-waterfall methodology](price-waterfall-methodology.md).
