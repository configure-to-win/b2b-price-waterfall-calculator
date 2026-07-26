[Back to README](../README.md) · [Open the Excel workbook](../template/b2b-price-waterfall-calculator-template.xlsx) · [Use the online calculator](https://configure.win/resources/price-waterfall-calculator)

# Worked example

The workbook contains a fictional example that demonstrates the aggregate price waterfall, profitability calculations, threshold signal and reconciliation to three B2B quote lines.

The example is not customer data, benchmark data, advice or a recommended policy.

## Aggregate inputs

| Input | Illustrative value | Entry mode or context |
| --- | ---: | --- |
| Currency | EUR | Selected currency |
| List price per unit | €60,000 | One aggregated deal |
| Quantity | 1 | Illustrative input |
| Unit cost | €38,000 | Before vendor incentive |
| Customer discount | €5,000 | Amount mode |
| Promotional discount | €2,000 | Amount mode |
| Freight or service concession | €1,500 | Amount mode |
| Customer rebate | €2,500 | Amount mode |
| Vendor incentive | €1,500 | Amount mode |
| Minimum pocket margin | 27.0% | Illustrative policy threshold |

## Step 1: Gross list value

```text
Gross list value
= €60,000 × 1
= €60,000
```

## Step 2: Invoice price

```text
Invoice price
= €60,000
− €5,000 customer discount
− €2,000 promotional discount
= €53,000
```

## Step 3: Pocket price

```text
Pocket price
= €53,000
− €1,500 freight or service concession
− €2,500 customer rebate
= €49,000
```

## Step 4: Base and effective cost

```text
Base cost
= €38,000 × 1
= €38,000
```

```text
Effective cost
= €38,000
− €1,500 vendor incentive
= €36,500
```

## Step 5: Front-end profitability

```text
Front-end gross profit
= €53,000 − €38,000
= €15,000
```

```text
Front-end margin
= €15,000 ÷ €53,000
= 28.3%
```

## Step 6: Pocket profitability

```text
Pocket gross profit
= €49,000 − €36,500
= €12,500
```

```text
Pocket margin
= €12,500 ÷ €49,000
= 25.5%
```

## Step 7: Margin leakage

```text
Margin leakage
= €60,000 − €49,000
= €11,000
```

The same amount reconciles to the customer-facing deductions:

```text
€5,000 customer discount
+ €2,000 promotional discount
+ €1,500 concession
+ €2,500 customer rebate
= €11,000
```

```text
Leakage percentage
= €11,000 ÷ €60,000
= 18.3%
```

The largest customer-facing deduction is the **Customer discount** at €5,000.

## Step 8: Margin delta

```text
Margin delta
= 25.5% − 28.3%
= −2.8 percentage points
```

The expected vendor incentive improves effective cost by €1,500, but the post-invoice concession and customer rebate reduce pocket price by €4,000. The resulting pocket margin remains below front-end margin.

## Step 9: Approval signal

```text
Calculated pocket margin = 25.5%
Minimum pocket margin = 27.0%
```

```text
Difference
= 25.5% − 27.0%
= approximately −1.5 percentage points
```

Because pocket margin is below the illustrative threshold, the workbook returns:

```text
Commercial review required
```

This is a user-configured comparison signal, not an approval decision.

## Aggregate calculation summary

| Metric | Result |
| --- | ---: |
| Gross list value | €60,000 |
| Invoice price | €53,000 |
| Pocket price | €49,000 |
| Base cost | €38,000 |
| Effective cost | €36,500 |
| Front-end gross profit | €15,000 |
| Front-end margin | 28.3% |
| Pocket gross profit | €12,500 |
| Pocket margin | 25.5% |
| Margin leakage | €11,000 |
| Leakage percentage | 18.3% |
| Margin delta | −2.8 percentage points |
| Approval signal | Commercial review required |

## Three-line quote allocation

The worked example allocates the aggregate deal across three fictional quote lines.

| Quote line | Gross list value | Customer discount | Promotional discount | Invoice price | Freight/service | Customer rebate | Pocket price | Base cost | Vendor incentive | Effective cost | Front-end GP | Pocket GP | Leakage |
| --- | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| Hardware bundle | €30,000 | €3,000 | €1,000 | €26,000 | €1,000 | €1,000 | €24,000 | €22,000 | €1,000 | €21,000 | €4,000 | €3,000 | €6,000 |
| Annual software subscription | €20,000 | €1,500 | €500 | €18,000 | €0 | €1,500 | €16,500 | €10,000 | €500 | €9,500 | €8,000 | €7,000 | €3,500 |
| Implementation service | €10,000 | €500 | €500 | €9,000 | €500 | €0 | €8,500 | €6,000 | €0 | €6,000 | €3,000 | €2,500 | €1,500 |
| **Total** | **€60,000** | **€5,000** | **€2,000** | **€53,000** | **€1,500** | **€2,500** | **€49,000** | **€38,000** | **€1,500** | **€36,500** | **€15,000** | **€12,500** | **€11,000** |

The workbook confirms that the line allocation reconciles exactly to the aggregate example.

## Why quote-level margins must use aggregated values

The quote-level front-end margin is:

```text
€15,000 aggregate front-end gross profit
÷ €53,000 aggregate invoice price
= 28.3%
```

The quote-level pocket margin is:

```text
€12,500 aggregate pocket gross profit
÷ €49,000 aggregate pocket price
= 25.5%
```

These values should not be replaced by a simple average of the three line-level margin percentages.

## What the example demonstrates

The example shows that:

- invoice price can appear commercially stronger than the full pocket economics;
- customer-facing concessions and rebates reduce realised price after invoice discounts;
- a vendor incentive improves effective cost without changing pocket price;
- front-end margin and pocket margin answer different questions;
- margin leakage measures the reduction from gross list value to pocket price;
- a user-entered threshold can produce a commercial-review signal;
- a multi-line quote can reconcile to the same aggregate waterfall.

## Interpretation boundary

The example does not establish:

- an acceptable margin;
- an acceptable leakage percentage;
- a recommended threshold;
- a universal pricing policy;
- a vendor or customer benchmark.

For the model’s limitations, see [Limitations](limitations.md).
