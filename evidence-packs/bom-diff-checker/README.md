# BOM revision comparison example

[Download the source workbook](./demo-input.xlsx) · [Download the complete report](./full-report.xlsx)

This synthetic two-revision workbook uses the same Excel exporter as the [BOM Diff Checker](https://specrivet.com/tools/bom-diff-checker).

## Reproduce the comparison

Choose **One workbook, two worksheets**. Select **Rev A** and **Rev B**, each with the header at row **5**. Keep the detected columns for Level, RefDes, MPN, Description, Qty, UOM, DNP, Manufacturer, Revision, and Find Number. Use **Auto** level mode for both revisions and an order quantity of **1**.

| Report sheet | What to check |
| --- | --- |
| `1_Summary` | Rev A has **38** detail rows and Rev B has **37**. The report flags six issues and links two swaps. |
| `2_Purchase_Delta` | Search for `RES-10K`. Extended purchase quantity rises from **8** to **12** per finished unit. The net for this one-unit order is **(12 − 8) × 1 = 4 EA**. |
| `3_Structure_And_Review` | Filter for `USB-A` or `USB-C`. The swap evidence links the two sources at reference designator `J1`. Follow the Rev A and Rev B row columns back to the input. |

Use the per-unit quantity delta times the order quantity for material planning. This report compares quantities and revision evidence. Apply your approved unit costs to any purchasing delta when calculating its financial impact.
