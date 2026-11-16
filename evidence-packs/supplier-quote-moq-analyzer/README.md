# Supplier quote and MOQ comparison example

[Download the source workbook](./demo-input.xlsx) · [Download the complete report](./full-report.xlsx)

This synthetic RFQ uses the same Excel exporter as the [Supplier Quote & MOQ Analyzer](https://specrivet.com/tools/supplier-quote-moq-analyzer).

## Reproduce the comparison

Use **Separate demand + supplier quotes** with the `Demand` sheet and the `Cut-Tape A`, `Reel B`, `Regional C`, and `Reserve D` quote sheets. Keep the detected columns and use USD with up to **two suppliers**. Use **$35 shipping** and a **$150 minimum order value** for Regional C. The other suppliers have zero freight and minimum order value. The demo uses the same workbook for all five sources.

| Report sheet | What to check |
| --- | --- |
| `Offer_Comparison` | For **D-TRAP**, demand is 120 pieces. Cut-Tape A sells 120 at $0.10 for **$12**. Reel B’s MOQ and MPQ require 4,000 at $0.04 for **$160**, with 3,880 excess pieces. Use the input source sheet and row shown at the right to find each quote. |
| `Awarded_Split_PO_Summary` | The two recommended orders cost **$1,258.038** and **$809.000**, including any listed row fees, freight, and MOV buffers. |
| `Audit_Summary` | All **48** demand lines are covered. Compare **$2,470.038** for the best single supplier with **$2,067.038** for the split. The difference is **$403.00**. |

For a selected price break, round the purchase quantity up to the required pack multiple while meeting demand, MOQ and the break’s minimum. Calculate line cash as buy quantity divided by price basis quantity, times the price, plus the line fee. Add any MOV buffer and freight per supplier. Confirm lead time, quality and payment terms before placing orders.
