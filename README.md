# Free Excel BOM Templates for Hardware, PCBA, and Small Manufacturers

This open-source pack includes three Excel bill of materials (BOM) layouts for hardware engineering, printed circuit board assembly (PCBA), and small manufacturing teams. Save a copy, keep the column headers, and replace the synthetic data with your own parts.

| Download | Use case | Worksheets | Key columns and conventions |
| --- | --- | --- | --- |
| [01 · Multi-level BOM cost rollup](./templates/01-multi-level-bom-cost-rollup-template.xlsx?raw=true) | Check an indented assembly and roll up purchase quantities and costs. | `BOM`, headers on row 5. | Store `Item Path` as text with dot-separated paths such as `1`, `1.1`, and `1.1.1`. Keep `Part No` as text to preserve identifiers such as `000123`. `Quantity` is per parent. Enter the unit cost of purchased parts in `Cost Each`. |
| [02 · BOM shortage and kit readiness](./templates/02-bom-shortage-kit-readiness-template.xlsx?raw=true) | Check how many kits one warehouse can supply and what is short for a planned build. | `BOM` and `Inventory`, headers on row 4 of both sheets. | Match `Item No.` to `SKU` using a consistent unit of measure. Use `Qty` per kit, `Available Physical` for net stock, and `Warehouse` for site codes such as `MAIN`. If starting from gross `On Hand`, record any `Safety Stock` reserve in a separate column and account for it when preparing the net available quantity. |
| [03 · ECN BOM revision diff](./templates/03-bom-revision-diff-ecn-template.xlsx?raw=true) | Compare two full BOM snapshots for an engineering change notice (ECN). | `Rev A` and `Rev B`, headers on row 5 of both sheets. | Use `Part Number` as text for IDs like `00047`. Use `Qty per Parent`, `UOM`, and `Reference Designators` such as `R1-R4` or `J1`. The sample is flat. For a multi-level BOM, use `Outline` with dot-separated paths on both revisions. |

## Reference checks

Run these checks in your browser with the matching SpecRivet tool.

1. **Cost rollup.** Select `BOM`, set `Batch Build Qty` to `10`, and use `USD`. The 32-row sample rolls up to **$510.60 for 10 builds**. Part `000123` requires 24 pieces per build across the three subassemblies. [Multi-Level BOM Checker & Cost Rollup](https://specrivet.com/tools/bom-checker-and-cost-rollup)
2. **Kit readiness.** Select `MAIN`, set the build quantity to `10` and scrap to `0%`, and map `Available Physical` as the net available quantity. The maximum build is **8 kits**. `STD-SCREW` requires 40 pieces for 10 kits, with 35 available in `MAIN` and a shortage of **5 pieces**. Other warehouse quantities stay outside this calculation. [BOM Shortage Calculator](https://specrivet.com/tools/bom-shortage-calculator)
3. **Revision diff.** Map both sheets and compare one finished unit. At position `J1`, **`USB-A` → `USB-C`** removes one `USB-A` and adds one `USB-C` per unit. The 12 reversed `KIT-01` through `KIT-12` rows match by part number and keep their quantities. Part `00047` stays at four per unit as its designators change from `R1-R4` to `R1-R3, R5`. [BOM Diff Checker](https://specrivet.com/tools/bom-diff-checker)

Find all three browser-based checks on the [SpecRivet home page](https://specrivet.com).

## License

The templates and README are available under the [MIT License](./LICENSE).

The original 32-row workbook is also available at its [legacy download link](./02_small_clean_trial.xlsx?raw=true).
