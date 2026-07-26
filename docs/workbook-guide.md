[Back to README](../README.md) · [Open the Excel workbook](../template/b2b-price-waterfall-calculator-template.xlsx) · [Use the online calculator](https://configure.win/resources/price-waterfall-calculator)

# Workbook guide

This guide explains how to use the five worksheets in the **B2B Price Waterfall Calculator — Excel Template** and how the three analysis formats relate to each other.

## Choose the appropriate worksheet

| Analysis need | Worksheet | What you enter | What the worksheet returns |
| --- | --- | --- | --- |
| Model one aggregated deal | **Calculator** | Deal setup, five adjustments and an optional pocket-margin threshold | KPI panel, calculation table, price-waterfall chart and approval signal |
| Compare multiple deals | **Deal log** | One deal per row | Price realisation, profitability, leakage, margin delta, largest customer-facing deduction and approval signal |
| Analyse a multi-line or multi-vendor quote | **Quote lines** | One quote line per row | Line economics and a selected-quote summary calculated from aggregated monetary values |
| Apply consistent terminology | **Definitions** | No calculation input | Canonical definitions, formulas, scope notes and workbook information |
| Review a reconciled fictional example | **Worked example** | No input required | Aggregate calculations, three-line reconciliation, margins, leakage and threshold result |

The worksheets use the same commercial definitions, but their input structures are not identical.

- **Calculator** and **Deal log** allow each adjustment to be entered in **Amount** or **Percentage** mode.
- **Quote lines** uses percentage inputs for customer and promotional discounts, and monetary amounts for concessions, customer rebates and vendor incentives.
- **Quote lines** calculates quote-level margins from aggregated monetary values. It does not average line-level percentages.

## Worksheet 1: Calculator

Use **Calculator** for one representative deal or for average inputs from a comparable group of deals.

### Deal setup

Enter:

1. Currency
2. List price per unit
3. Quantity
4. Unit cost before vendor incentive

Supported currency selections are:

- EUR
- USD
- GBP
- CAD
- AUD
- CHF
- DKK
- NOK
- SEK

The currency selection controls presentation. The workbook does not convert monetary values between currencies.

### Price-waterfall adjustments

For each adjustment, select **Amount** or **Percentage** and enter a value.

| Adjustment | Percentage basis | Commercial effect |
| --- | --- | --- |
| Customer discount | Gross list value | Reduces invoice price |
| Promotional discount | Gross list value | Reduces invoice price |
| Freight or service concession | Invoice price | Reduces pocket price |
| Customer rebate | Invoice price | Reduces pocket price |
| Vendor incentive received | Base cost | Reduces effective cost |

When entering a percentage in a general-number input cell, enter it as an Excel percentage such as `10%` or as its decimal equivalent `0.10`. Do not enter `10` to represent 10%.

### Optional threshold

Enter a **Minimum acceptable pocket margin** only when you want the workbook to compare the calculated pocket margin with a user-defined threshold.

The result is one of:

- No threshold set
- Within configured threshold
- Commercial review required

The signal is illustrative. It is not an approval decision or a recommended policy.

### Result areas

The worksheet displays:

- gross list value;
- invoice price;
- pocket price;
- base cost;
- effective cost;
- front-end gross profit and margin;
- pocket gross profit and margin;
- margin leakage and leakage percentage;
- margin delta;
- approval signal.

It also includes:

- a calculation table that moves from gross list value to pocket gross profit;
- a waterfall chart based on the same stages;
- an approval panel showing the threshold, calculated pocket margin and difference.

See [Methodology](methodology.md) for the exact formulas.

## Worksheet 2: Deal log

Use **Deal log** to record up to 100 deals in rows 6–105.

Each row contains:

- deal identification and measurement context;
- core price and cost inputs;
- amount-or-percentage modes for five adjustments;
- an optional pocket-margin threshold;
- derived commercial results;
- notes.

The derived columns calculate:

- gross list value;
- invoice price;
- pocket price;
- base cost;
- effective cost;
- front-end gross profit and margin;
- pocket gross profit and margin;
- margin leakage and leakage percentage;
- margin delta;
- largest customer-facing deduction;
- approval signal.

Use one currency consistently within each row. Convert values before entry when a deal contains monetary source values in different currencies.

For detailed column guidance, see [Deal log guide](deal-log-guide.md).

## Worksheet 3: Quote lines

Use **Quote lines** for a quote containing multiple products, services or vendors.

The worksheet supports 50 quote lines in rows 9–58.

### Quote selection and policy

Enter:

- Selected Quote ID
- Customer
- Quote currency
- Minimum pocket margin

The selected-quote summary includes only rows whose **Quote ID** matches the selected Quote ID.

### Line inputs

For each line, enter:

- Quote ID
- Vendor
- SKU
- Description
- Quantity
- Unit list price
- Customer discount %
- Promotional discount %
- Freight or service concession amount
- Customer rebate amount
- Unit cost
- Vendor incentive amount
- Notes

The worksheet derives all price, cost, profit, margin and leakage values for the line.

### Selected-quote summary

The summary aggregates monetary values for the selected Quote ID and then calculates:

```text
Quote-level front-end margin
= Aggregated front-end gross profit ÷ Aggregated invoice price

Quote-level pocket margin
= Aggregated pocket gross profit ÷ Aggregated pocket price
```

It does not average line-level margins.

The quote currency is descriptive and controls the intended interpretation of the values. The worksheet does not perform line-level currency conversion. All lines included in one selected quote should therefore use the same currency basis.

## Worksheet 4: Definitions

Use **Definitions** as the canonical reference for:

- waterfall terms;
- formulas;
- percentage bases;
- approval-threshold meaning;
- scope limitations;
- workbook version and publisher;
- official Configure to WIN resources.

Use the same definitions when comparing deals, quote lines or measurement periods.

See [Definitions](definitions.md) and [Margin and leakage definitions](margin-and-leakage-definitions.md).

## Worksheet 5: Worked example

The fictional worked example demonstrates:

- aggregate deal inputs;
- the full price and cost waterfall;
- front-end and pocket profitability;
- margin leakage;
- a 27.0% illustrative minimum pocket margin;
- reconciliation to three quote lines;
- the resulting commercial-review signal.

The example is not customer data, benchmark data, advice or a recommended policy.

See [Worked example](worked-example.md) for a step-by-step explanation.

## Recommended operating sequence

1. Define whether the unit of analysis is one deal, several comparable deals or a multi-line quote.
2. Use one consistent currency basis.
3. Confirm list price, quantity and cost inputs.
4. Separate customer-facing deductions from supplier-side incentives.
5. Apply the correct percentage basis to every adjustment.
6. Review price realisation before reviewing margin.
7. Compare front-end and pocket economics.
8. Apply a threshold only when it reflects the user’s own policy.
9. Preserve assumptions and context in Notes.
10. Use the outputs to identify the adjustment or stage that requires further review.

## Related documentation

- [Methodology](methodology.md)
- [Price-waterfall methodology](price-waterfall-methodology.md)
- [Definitions](definitions.md)
- [Margin and leakage definitions](margin-and-leakage-definitions.md)
- [Deal log guide](deal-log-guide.md)
- [Worked example](worked-example.md)
- [Limitations](limitations.md)
