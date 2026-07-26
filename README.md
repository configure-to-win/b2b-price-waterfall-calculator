# B2B Price Waterfall Calculator — Excel Template

Model how list price becomes invoice price, pocket price and pocket margin after customer discounts, promotional discounts, concessions, customer rebates, vendor incentives and cost.

This workbook accompanies the [B2B Price Waterfall Calculator by Configure to WIN](https://configure.win/resources/price-waterfall-calculator), where you can model the same deal economics online using an aggregated deal.

## Get the tool

- [Download the latest Excel release](../../releases/latest)
- [Open the Excel workbook](template/b2b-price-waterfall-calculator-template.xlsx)
- [Use the online calculator](https://configure.win/resources/price-waterfall-calculator)
- [Read the calculation methodology](docs/methodology.md)

## What this workbook calculates

The template makes customer-facing deductions, supplier-side incentives and their effect on deal profitability visible in one commercial waterfall.

It calculates:

- **Gross list value** — list price per unit multiplied by quantity before discounts or concessions.
- **Invoice price** — the value after customer and promotional discounts but before off-invoice concessions and customer rebates.
- **Pocket price** — the realised customer price after discounts, concessions and customer rebates.
- **Base cost** — unit cost multiplied by quantity before a supplier-side vendor incentive.
- **Effective cost** — base cost reduced by the expected vendor incentive.
- **Front-end gross profit and margin** — the profitability visible from invoice price and base cost.
- **Pocket gross profit and margin** — the profitability after customer-facing deductions and supplier-side incentives.
- **Margin leakage** — the monetary reduction from gross list value to pocket price.
- **Leakage percentage** — margin leakage as a share of gross list value.
- **Margin delta** — the difference between pocket margin and front-end margin.
- **Largest customer-facing deduction** — the largest calculated amount among customer discount, promotional discount, freight or service concession and customer rebate.
- **Approval signal** — an illustrative comparison between pocket margin and a minimum threshold entered by the user.

The workbook can be used for:

1. one aggregated deal;
2. a log of multiple deals;
3. a multi-line, multi-vendor quote.

## Workbook contents

| Sheet | Purpose |
| --- | --- |
| **Calculator** | Models one aggregated deal with adjustable amount or percentage inputs, KPI outputs, an approval signal, a calculation table and a price-waterfall chart. |
| **Deal log** | Records deal inputs and compares price realisation, profitability, margin leakage, the largest customer-facing deduction and approval signals across at least 100 deals. |
| **Quote lines** | Models a multi-line, multi-vendor quote and calculates quote-level economics from aggregated monetary values. Quote-level margin percentages are calculated from the aggregated amounts, not by averaging line-level percentages. |
| **Definitions** | Provides the standard definitions, formulas, calculation guidance, scope notes, workbook information and links to the official Configure to WIN resources. |
| **Worked example** | Reconciles an aggregate fictional price waterfall to three illustrative B2B quote lines and demonstrates the resulting commercial review signal. |

## How to use the workbook

### Option 1: Calculate one aggregated deal

Use the **Calculator** worksheet when you want to understand the economics of one deal or enter average values for a comparable group of quotes.

1. Select the deal currency.
2. Enter the list price per unit.
3. Enter the quantity.
4. Enter the unit cost before vendor incentive.
5. Choose **Amount** or **Percentage** for each adjustment.
6. Enter the customer discount, promotional discount, freight or service concession, customer rebate and vendor incentive.
7. Optionally enter a minimum acceptable pocket margin.
8. Review the KPI panel, waterfall calculation, chart and approval signal.

The supported currency selections are:

- EUR
- USD
- GBP
- CAD
- AUD
- CHF
- DKK
- NOK
- SEK

The selected currency controls the displayed monetary format. The workbook does not perform currency conversion.

### Option 2: Compare multiple deals

Use the **Deal log** to record and compare individual deals over time.

For each row, enter:

- Deal ID
- Measurement date
- Customer or segment
- Currency
- List price per unit
- Quantity
- Unit cost
- Adjustment mode and value for each waterfall item
- Optional minimum pocket margin
- Notes

The worksheet derives:

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

Use consistent definitions and input conventions when comparing deals or measurement periods. The workbook does not provide a target margin or external benchmark.

### Option 3: Analyse a multi-line, multi-vendor quote

Use **Quote lines** when one quote contains multiple products, services or vendors.

1. Enter the selected Quote ID.
2. Add the customer name or segment.
3. Select the quote currency.
4. Enter an optional minimum pocket margin.
5. Add each quote line with its vendor, SKU, description, quantity, unit list price, discounts, concessions, rebates, unit cost and vendor incentive.
6. Review the selected quote summary.

The worksheet calculates line-level values and then aggregates the monetary results for the selected quote.

Quote-level margins are calculated as:

```text
Aggregated gross profit ÷ aggregated price
```

They are not calculated by averaging the margin percentages of the individual lines.

## Deal inputs and waterfall adjustments

### Deal setup

| Input | Meaning |
| --- | --- |
| **Currency** | The currency used to display the deal values. |
| **List price per unit** | The entered list price for one unit. |
| **Quantity** | The number of units included in the calculation. |
| **Unit cost before vendor incentive** | The entered cost per unit before a supplier-side incentive is applied. |

### Customer discount

A customer-specific or negotiated reduction applied before invoice price.

- Amount mode: use the entered monetary value.
- Percentage mode: calculate the amount as a percentage of gross list value.

### Promotional discount

A temporary campaign or deal-specific discount applied before invoice price.

- Amount mode: use the entered monetary value.
- Percentage mode: calculate the amount as a percentage of gross list value.

### Freight or service concession

Freight absorption, free service, training or another non-price concession that reduces the realised customer price.

- Amount mode: use the entered monetary value.
- Percentage mode: calculate the amount as a percentage of invoice price.

### Customer rebate

An expected off-invoice rebate or credit granted to the customer.

- Amount mode: use the entered monetary value.
- Percentage mode: calculate the amount as a percentage of invoice price.

### Vendor incentive received

An expected supplier-side commercial benefit that reduces effective deal cost or improves the commercial outcome.

- Amount mode: use the entered monetary value.
- Percentage mode: calculate the amount as a percentage of base cost.

A vendor incentive does not reduce pocket price in this model. It reduces effective cost. A customer rebate is a customer-facing deduction and therefore reduces pocket price.

## Calculation methodology

The workbook applies the following calculation sequence.

### Gross list value

```text
Gross list value
= List price per unit × Quantity
```

### Customer and promotional discounts

```text
Customer discount amount
= Entered amount
or Gross list value × Entered percentage

Promotional discount amount
= Entered amount
or Gross list value × Entered percentage
```

### Invoice price

```text
Invoice price
= Gross list value
− Customer discount
− Promotional discount
```

### Concession and customer rebate

```text
Freight or service concession amount
= Entered amount
or Invoice price × Entered percentage

Customer rebate amount
= Entered amount
or Invoice price × Entered percentage
```

### Pocket price

```text
Pocket price
= Invoice price
− Freight or service concession
− Customer rebate
```

### Base and effective cost

```text
Base cost
= Unit cost × Quantity

Vendor incentive amount
= Entered amount
or Base cost × Entered percentage

Effective cost
= Base cost − Vendor incentive
```

### Front-end profitability

```text
Front-end gross profit
= Invoice price − Base cost

Front-end margin
= Front-end gross profit ÷ Invoice price
```

### Pocket profitability

```text
Pocket gross profit
= Pocket price − Effective cost

Pocket margin
= Pocket gross profit ÷ Pocket price
```

### Margin leakage

```text
Margin leakage
= Gross list value − Pocket price

Leakage percentage
= Margin leakage ÷ Gross list value
```

### Margin delta

```text
Margin delta
= Pocket margin − Front-end margin
```

## Optional approval threshold

The minimum acceptable pocket margin is entered by the user.

The workbook returns:

- **No threshold set** when the threshold is blank;
- **Within configured threshold** when pocket margin is equal to or above the entered threshold;
- **Commercial review required** when pocket margin is below the entered threshold.

This is an illustrative commercial signal based only on the threshold entered by the user. It is not an approval decision, an industry benchmark or a recommended pricing policy.

## Interpreting the results

Review the waterfall in sequence rather than relying on one margin percentage.

- A large difference between **gross list value** and **invoice price** indicates that customer and promotional discounts account for a substantial part of the price reduction.
- A large difference between **invoice price** and **pocket price** indicates that concessions and customer rebates further reduce realised customer value.
- The difference between **base cost** and **effective cost** shows the expected contribution of the vendor incentive.
- **Front-end margin** reflects invoice price and base cost.
- **Pocket margin** reflects the full modelled economics after customer-facing deductions and the supplier-side incentive.
- A negative **margin delta** means pocket margin is below front-end margin.
- A positive margin delta means the modelled vendor incentive more than offsets the effect of off-invoice customer-facing deductions.
- **Largest customer-facing deduction** identifies the highest calculated deduction amount, but does not determine whether that deduction is justified or avoidable.

Use the output to identify which commercial adjustment requires further review. The workbook calculates entered values; it does not determine the organisational, contractual or policy reason behind them.

## Worked example

The included worked example uses fictional inputs:

| Input or result | Illustrative value |
| --- | ---: |
| Gross list value | €60,000 |
| Invoice price | €53,000 |
| Pocket price | €49,000 |
| Base cost | €38,000 |
| Vendor incentive | €1,500 |
| Effective cost | €36,500 |
| Front-end gross profit | €15,000 |
| Front-end margin | 28.3% |
| Pocket gross profit | €12,500 |
| Pocket margin | 25.5% |
| Margin leakage | €11,000 |
| Leakage percentage | 18.3% |
| Minimum pocket margin | 27.0% |
| Approval signal | Commercial review required |

The calculated pocket margin is 1.5 percentage points below the illustrative minimum pocket margin.

The example also reconciles the aggregate waterfall to three fictional lines:

- Hardware bundle
- Annual software subscription
- Implementation service

The values are illustrative only. They are not customer data, benchmark data, advice, target values or a recommended policy.

## Calculation guidance

For consistent results:

- **Use stable definitions.** Apply the same definitions across deals, quote lines and measurement periods.
- **Use the correct percentage basis.** Customer and promotional discounts use gross list value; concessions and customer rebates use invoice price; vendor incentives use base cost.
- **Separate customer and supplier economics.** Customer rebates reduce pocket price. Vendor incentives reduce effective cost.
- **Do not average line-level margins.** Calculate quote-level margins from aggregated monetary values.
- **Keep currencies consistent.** The workbook formats the selected currency but does not convert values.
- **Distinguish expected values from settled values.** The model uses expected commercial values.
- **Document assumptions.** Use the notes fields to preserve context needed to interpret the results.
- **Compare comparable deals.** Review differences in product mix, customer, channel and commercial policy before comparing results.

## Limitations and disclaimer

This workbook is a practical commercial calculation tool. It does **not** provide:

- an industry benchmark;
- a recommended margin or leakage level;
- a recommended approval threshold;
- an approval decision;
- currency conversion;
- rebate settlement;
- claim submission;
- accrual accounting;
- vendor-program administration;
- financial reconciliation;
- legal, financial or commercial advice.

Appropriate margins, leakage levels and thresholds vary by industry, product mix, customer, channel and commercial policy.

The user remains responsible for the accuracy of the inputs, the treatment of expected discounts, rebates and incentives, the consistency of the calculation method and the interpretation of the outputs.

## License

This repository is licensed under the terms described in [LICENSE.md](LICENSE.md).

When reusing or adapting the workbook or documentation, follow the attribution and modification requirements stated in that file.

## About Configure to WIN

Configure to WIN develops tools and software for B2B quote control, pricing governance, commercial calculation and approval management.

Learn more at [Configure to WIN](https://configure.win/).
