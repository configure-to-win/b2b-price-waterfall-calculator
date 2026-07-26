[Back to README](../README.md) · [Open the Excel workbook](../template/b2b-price-waterfall-calculator-template.xlsx) · [Use the online calculator](https://configure.win/resources/price-waterfall-calculator)

# Definitions

Use these definitions consistently across Calculator inputs, Deal log rows, Quote lines and reporting periods.

## Price and adjustment terms

| Term | Definition | Calculation or entry guidance |
| --- | --- | --- |
| **List price per unit** | The entered list price for one unit before customer-facing deductions. | Multiply by quantity to calculate gross list value. |
| **Quantity** | The number of units included in the deal or quote line. | Use the same unit basis for list price and unit cost. |
| **Gross list value** | The total list value before customer-facing deductions. | List price per unit × quantity. |
| **Customer discount** | A customer-specific or negotiated reduction applied before invoice price. | Enter an amount or a percentage of gross list value. |
| **Promotional discount** | A temporary campaign or deal-specific reduction applied before invoice price. | Enter an amount or a percentage of gross list value. |
| **Invoice price** | The value after customer and promotional discounts but before off-invoice concessions and customer rebates. | Gross list value − customer discount − promotional discount. |
| **Freight or service concession** | Freight absorption, free service, training or another customer-facing concession that reduces realised price. | Enter an amount or a percentage of invoice price. Quote lines use an amount. |
| **Customer rebate** | An expected off-invoice benefit or credit granted to the customer. | Enter an amount or a percentage of invoice price. Quote lines use an amount. |
| **Pocket price** | The realised customer price after discounts, concessions and customer rebates. | Invoice price − concession − customer rebate. |
| **Unit cost before vendor incentive** | The entered product or service cost per unit before supplier-side incentive. | Multiply by quantity to calculate base cost. |
| **Base cost** | The product or service cost before supplier-side incentive. | Unit cost × quantity. |
| **Vendor incentive** | An expected supplier-side commercial benefit that reduces effective cost or improves deal economics. | Enter an amount or a percentage of base cost. Quote lines use an amount. |
| **Effective cost** | Base cost after the expected vendor incentive. | Base cost − vendor incentive. |

## Profit and margin terms

| Term | Definition | Formula |
| --- | --- | --- |
| **Front-end gross profit** | Gross profit visible from invoice price and base cost. | Invoice price − base cost |
| **Front-end margin** | Front-end gross profit as a share of invoice price. | Front-end gross profit ÷ invoice price |
| **Pocket gross profit** | Gross profit after customer-facing deductions and supplier-side incentive. | Pocket price − effective cost |
| **Pocket margin** | Pocket gross profit as a share of pocket price. | Pocket gross profit ÷ pocket price |
| **Margin delta** | The difference between pocket margin and front-end margin. | Pocket margin − front-end margin |

Front-end and pocket margins use different price and cost bases. See [Margin and leakage definitions](margin-and-leakage-definitions.md).

## Leakage terms

| Term | Definition | Formula |
| --- | --- | --- |
| **Margin leakage** | The monetary reduction from gross list value to pocket price. | Gross list value − pocket price |
| **Margin leakage percentage** | Margin leakage as a share of gross list value. | Margin leakage ÷ gross list value |
| **Largest customer-facing deduction** | The largest calculated amount among customer discount, promotional discount, freight or service concession and customer rebate. | Calculated in the Deal log; vendor incentive is excluded. |

The workbook records the size of customer-facing deductions. It does not determine whether a deduction is justified, contracted, strategic or avoidable.

## Threshold and signal terms

| Term | Definition | Guidance |
| --- | --- | --- |
| **Minimum acceptable pocket margin** | A user-entered threshold used to compare with calculated pocket margin. | Leave blank when no threshold should be applied. |
| **No threshold set** | The signal returned when the threshold is blank. | No policy comparison is performed. |
| **Within configured threshold** | The signal returned when pocket margin is equal to or above the entered threshold. | It is based only on the user-entered threshold. |
| **Commercial review required** | The signal returned when pocket margin is below the entered threshold. | It is an illustrative signal, not an approval decision. |
| **Difference in percentage points** | Pocket margin minus minimum acceptable pocket margin. | A negative value indicates that pocket margin is below the threshold. |

## Input-mode terms

| Term | Definition |
| --- | --- |
| **Amount mode** | Uses the entered adjustment value directly as a monetary amount. |
| **Percentage mode** | Multiplies the entered percentage by the adjustment’s defined basis. |
| **Percentage basis** | The value to which a percentage adjustment is applied: gross list value, invoice price or base cost. |

Percentage bases are fixed by the workbook:

- customer discount → gross list value;
- promotional discount → gross list value;
- freight or service concession → invoice price;
- customer rebate → invoice price;
- vendor incentive → base cost.

## Workbook-structure terms

| Term | Definition |
| --- | --- |
| **Aggregated deal** | One calculation representing the total economics of a deal rather than individual lines. |
| **Deal log** | A row-based record of up to 100 deals using the aggregate price-waterfall model. |
| **Quote line** | One product, service or vendor line within a quote. |
| **Selected Quote ID** | The identifier used to determine which Quote lines are included in the selected-quote summary. |
| **Selected-quote summary** | Aggregated monetary results and calculated margins for all line rows matching the selected Quote ID. |
| **Worked example** | A fictional example provided to demonstrate formulas and reconciliation. |

## Currency terms

| Term | Definition |
| --- | --- |
| **Currency selection** | The selected display and interpretation currency for a deal or quote. |
| **Currency conversion** | Conversion of one monetary value into another currency. This workbook does not perform it. |

Supported currency labels are EUR, USD, GBP, CAD, AUD, CHF, DKK, NOK and SEK.

## Scope terms

| Term | Definition |
| --- | --- |
| **Expected commercial value** | A modelled discount, rebate, concession, incentive, price or cost used in the calculation. |
| **Rebate settlement** | The later operational or financial process of determining and paying an actual rebate. The workbook does not perform it. |
| **Financial reconciliation** | Matching calculated or expected values to accounting, settlement or payment records. The workbook does not perform it. |

## Related documentation

- [Methodology](methodology.md)
- [Price-waterfall methodology](price-waterfall-methodology.md)
- [Margin and leakage definitions](margin-and-leakage-definitions.md)
- [Limitations](limitations.md)
