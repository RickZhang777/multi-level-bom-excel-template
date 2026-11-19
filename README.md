# 7-in-1 Hardware Engineering & Purchasing BOM Excel Template Pack

This free, open-source pack includes seven Excel layouts for bill of materials (BOM) work and supplier quote comparison. It is designed for hardware engineering, purchasing, printed circuit board assembly (PCBA), and small manufacturing teams. Save a copy, keep the column headers, and replace the example rows with your own data.

- **[Material Shortage Calculation & Clear-to-Build Excel Tool](https://specrivet.com/tools/bom-shortage-calculator)** — Net multi-level BOM demand against on-hand stock before kitting.
- **[Supplier Quote Comparison in Excel (MOQ, Reel Multiples & Price Breaks)](https://specrivet.com/tools/supplier-quote-moq-analyzer)** — Catch full-reel MPQ excess and Minimum Order Value cash traps before cutting POs.

| Download | Use case | Worksheets | Key columns and conventions |
| --- | --- | --- | --- |
| [01 · Multi-level BOM cost rollup](./templates/01-multi-level-bom-cost-rollup-template.xlsx?raw=true) | Check an indented assembly and roll up purchase quantities and costs. | `BOM`, headers on row 5. | Store `Item Path` as text with dot-separated paths such as `1`, `1.1`, and `1.1.1`. Keep `Part No` as text to preserve identifiers such as `000123`. `Quantity` is per parent. Enter the unit cost of purchased parts in `Cost Each`. |
| [02 · BOM shortage and kit readiness](./templates/02-bom-shortage-kit-readiness-template.xlsx?raw=true) | Check how many kits one warehouse can supply and what is short for a planned build. | `BOM` and `Inventory`, headers on row 4 of both sheets. | Match `Item No.` to `SKU` using a consistent unit of measure. Use `Qty` per kit, `Available Physical` for net stock, and `Warehouse` for site codes such as `MAIN`. If starting from gross `On Hand`, record any `Safety Stock` reserve in a separate column and account for it when preparing the net available quantity. |
| [03 · ECN BOM revision diff](./templates/03-bom-revision-diff-ecn-template.xlsx?raw=true) | Compare two full BOM snapshots for an engineering change notice (ECN). | `Rev A` and `Rev B`, headers on row 5 of both sheets. | Use `Part Number` as text for IDs like `00047`. Use `Qty per Parent`, `UOM`, and `Reference Designators` such as `R1-R4` or `J1`. The sample is flat. For a multi-level BOM, use `Outline` with dot-separated paths on both revisions. |
| [04 · Multi-level BOM flattener](./templates/04-multi-level-bom-flattener-template.xlsx?raw=true) | Flatten an engineering assembly into a purchasing list and parent-child records. | `Clean BOM`, headers on row 4. | Keep `Level` as an outline such as `1.1.2`. Enter `Qty per Parent` for each immediate parent. |
| [05 · Multi-BOM consolidation and where-used](./templates/05-multi-bom-where-used-template.xlsx?raw=true) | Combine two production BOMs and see which boards use each component. | `Board_A` and `Board_B`, headers on row 1. | Keep `Part Number` and `UOM` consistent across boards. Enter the per-unit BOM quantity in `Qty per Parent` and set each board's build quantity in the tool. |
| [06 · BOM approved vendor list and CM quote](./templates/06-bom-avl-approved-vendor-template.xlsx?raw=true) | Compare a contract manufacturer's quote with your approved vendor list (AVL) and flag unapproved sources. | `Master AVL`, `CM Quote`, and `How_To_Use`. Both data sheets have headers on row 1 and five editable example rows. | Keep `IPN` and MPN columns as text to preserve leading zeros. Map `Qty` on both sheets to compare quantities. Leave `Qty` unmapped for a vendor-only audit. |
| [07 · Supplier RFQ, price breaks, and MOQ](./templates/07-supplier-quote-rfq-comparison-template.xlsx?raw=true) | Compare two supplier quotes and see what minimum order quantities and pack multiples do to the order total. | `RFQ Comparison` and `How_To_Use`. Group headings are on row 2 and column headers on row 3. The sheet includes 15 editable example parts. | Keep `IPN` and `MPN` as text. Enter `Required Qty`, then fill in `MOQ`, `MPQ`, `Price Unit`, and the price-break columns in each supplier group. |

## Reference checks

Run these checks in your browser with the matching SpecRivet tool.

1. **Cost rollup.** Select `BOM`, set `Batch Build Qty` to `10`, and use `USD`. The 32-row sample rolls up to **$510.60 for 10 builds**. Part `000123` requires 24 pieces per build across the three subassemblies. [Multi-Level BOM Checker & Cost Rollup](https://specrivet.com/tools/bom-checker-and-cost-rollup)
2. **Kit readiness.** Select `MAIN`, set the build quantity to `10` and scrap to `0%`, and map `Available Physical` as the net available quantity. The maximum build is **8 kits**. `STD-SCREW` requires 40 pieces for 10 kits, with 35 available in `MAIN` and a shortage of **5 pieces**. Other warehouse quantities stay outside this calculation. [BOM Shortage Calculator](https://specrivet.com/tools/bom-shortage-calculator)
3. **Revision diff.** Map both sheets and compare one finished unit. At position `J1`, **`USB-A` → `USB-C`** removes one `USB-A` and adds one `USB-C` per unit. The 12 reversed `KIT-01` through `KIT-12` rows match by part number and keep their quantities. Part `00047` stays at four per unit as its designators change from `R1-R4` to `R1-R3, R5`. [BOM Diff Checker](https://specrivet.com/tools/bom-diff-checker)
4. **Assembly flattening.** Select `Clean BOM`, use outline levels, and set `Top Batch Qty` to `1`. The purchasing list calls for **7 × `SCR-M3`** and **4 × `IC-01`** across the assembly tree. [Flatten a multi-level BOM](https://specrivet.com/tools/multi-level-bom-flattener)
5. **Multi-BOM consolidation.** Select both board sheets. Set `Board_A` to build `2` and `Board_B` to build `3`. The purchase rollup calls for **16 × `CAP-100N`** and **9 × `RES-10K`**. The where-used matrix shows each board's contribution. [Consolidate multiple BOMs and check where parts are used](https://specrivet.com/tools/bom-where-used-consolidator)
6. **Approved vendor audit.** Upload the workbook and select `Master AVL` and `CM Quote`. With the five example rows on each sheet, the preview reports **1 high-risk item** for an unapproved source channel and **1 item to review** for a conditional approval. [Check a CM quote against your approved vendor list](https://specrivet.com/tools/bom-avl-checker)

7. **Supplier quote comparison.** Upload the workbook under Side-by-side comparison and select `RFQ Comparison`. With the example offers and default settings, the split order covers all **15 demand lines** and saves **$16.00** compared with buying them all from the lowest-cost single supplier. [Compare supplier quotes and MOQs in SpecRivet](https://specrivet.com/tools/supplier-quote-moq-analyzer)

Find all seven browser-based checks on the [SpecRivet home page](https://specrivet.com).

## Complete example reports

Each example includes the synthetic input workbook, the complete SpecRivet Excel export, and the settings and arithmetic to check against the source cells.

| Workflow | Demo input | Full Excel report | Verification notes |
| --- | --- | --- | --- |
| BOM cost rollup | [Input](./evidence-packs/bom-checker-and-cost-rollup/demo-input.xlsx?raw=true) | [Report](./evidence-packs/bom-checker-and-cost-rollup/full-report.xlsx?raw=true) | [Rollup checks](./evidence-packs/bom-checker-and-cost-rollup/README.md) |
| BOM revision diff | [Input](./evidence-packs/bom-diff-checker/demo-input.xlsx?raw=true) | [Report](./evidence-packs/bom-diff-checker/full-report.xlsx?raw=true) | [Revision checks](./evidence-packs/bom-diff-checker/README.md) |
| Supplier quote and MOQ comparison | [Input](./evidence-packs/supplier-quote-moq-analyzer/demo-input.xlsx?raw=true) | [Report](./evidence-packs/supplier-quote-moq-analyzer/full-report.xlsx?raw=true) | [Order cash checks](./evidence-packs/supplier-quote-moq-analyzer/README.md) |

### Clear-to-Build & Material Shortage Sample

Download [clear-to-build-bom-shortage-sample.xlsx](./clear-to-build-bom-shortage-sample.xlsx?raw=true) to work through a 50-unit build of a synthetic desktop audio controller.

- `BOM_Input` lists the finished unit, its two subassembly types, and the purchased parts in 23 BOM rows. Each quantity is per immediate parent.
- `Inventory_Snapshot` shows on-hand stock and work-order allocations by bin. `Available_Qty` subtracts allocated stock from on-hand stock.
- `Clear_to_Build_Summary` rolls up the BOM paths, converts stock to BOM units, and calculates required quantities, shortages, and `Max_Buildable_Kits`. The target, quantities, stock, reel size, and attrition rates are editable.

Check four ways a row-by-row shortage calculation can mislead a buyer.

1. **Shared components.** Each unit needs four capacitors on the control board and three on each of its two channel boards. That is ten capacitors per unit. At 50 units with a 5% feeder-loss allowance, the build needs 525 capacitors. Net stock is 493, leaving 32 short.
2. **Unit-of-measure mismatch.** The net resistor stock of 0.40 reel is 400 pieces at 1,000 pieces per reel. The build needs 357 pieces with the 2% setup-loss allowance. The 25 meters of net wire stock convert to 25,000 millimeters against 15,000 millimeters of demand.
3. **Allocated work-order stock.** The potentiometer bin holds 58 pieces, with 16 reserved for another work order. The 42 free pieces leave an eight-piece shortage for this build.
4. **The limiting part.** The long-lead microcontroller has zero on hand, so the current stock supports zero complete kits. Set its on-hand quantity to 50 to see the capacity rise to 42 kits, limited by potentiometers.

This example uses current on-hand stock. Check scheduled receipts against the kitting date and consider order multiples and price breaks when buying shortages. [Companion Excel shortage walkthrough](https://dev.to/rickzhang/material-shortage-calculation-in-excel-4-silent-math-traps-that-stall-small-batch-hardware-builds-2al6)

For your own BOM and stock snapshot, align part numbers and units before uploading. The online tool offers a free five-row preview. Zero BOM file retention (processed in server memory and discarded immediately). [SpecRivet BOM Shortage Calculator](https://specrivet.com/tools/bom-shortage-calculator)

## License

The templates and README are available under the [MIT License](./LICENSE).

The original 32-row workbook is also available at its [legacy download link](./02_small_clean_trial.xlsx?raw=true).
