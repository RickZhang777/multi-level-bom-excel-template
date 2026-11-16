# BOM cost rollup example

[Download the source workbook](./demo-input.xlsx) · [Download the complete report](./full-report.xlsx)

This synthetic multi-level assembly uses the same Excel exporter as the [BOM Checker & Cost Rollup](https://specrivet.com/tools/bom-checker-and-cost-rollup).

## Reproduce the analysis

Select **BOM** and set the header to row **7**. Map Outline or Level, Part Number, Description, Qty per Parent and Unit Cost to columns **A–E** in order. Set level mode to **Auto**, batch quantity to **10** and currency to **USD**.

| Report sheet | What to check |
| --- | --- |
| `1_Audit_Issues` | Match the source row numbers to the workbook. Row 55 has an invalid quantity and row 71 lacks a part number. |
| `2_Flattened_Purchase_BOM` | Search for part `000123`. Valid rows across six assemblies add to **52** pieces per build. Multiplying by **10** gives **520** pieces. The known line cost is **$5.44 per build**, with partial price coverage. |
| `3_Indented_Cost_Rollup` | Compare source-row extended quantities against the assembly hierarchy. The known cost is **$177.08 per build**, or **$1,770.80 for 10 builds**, with two purchase parts missing a cost. |

To reproduce a purchase quantity, multiply each valid line’s quantity per parent by the quantities along its parent chain and sum by part number. Multiply priced quantities by their source unit costs. Review flagged source rows and missing prices before using the total as a purchasing budget.
