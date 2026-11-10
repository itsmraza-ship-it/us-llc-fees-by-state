# US LLC Fees by State — 2026 Dataset

A free, machine-readable dataset of US LLC formation fees and annual requirements for all 50 states — plus the District of Columbia (51 jurisdictions in total).

Use it to compare where to form, estimate ongoing state costs before you file, or power your own tools, spreadsheets, and calculators.

## Files

| File | Format | Description |
|---|---|---|
| `data/states.json` | JSON | The full dataset, with a `meta` block and one object per jurisdiction |
| `data/states.csv` | CSV | The same data in flat tabular form — one row per jurisdiction |

Dataset compiled: **2026-11-09**.

## Fields

Each record in `states.json` (and each row in `states.csv`) has the following fields:

| Field | Meaning |
|---|---|
| `code` | USPS state code, e.g. `WY`, `DE`, `CA` (`DC` for District of Columbia) |
| `name` | Full state / jurisdiction name |
| `formation_document` | The founding document filed with the state, e.g. *Articles of Organization* or *Certificate of Formation* |
| `formation_fee_usd` | One-time state filing fee for the formation document — standard, non-expedited, online where offered |
| `annual_requirement` | The recurring state requirement, e.g. *Annual Report*, *Periodic Report*, *Annual LLC tax*, or *None — no annual report or annual state fee* where a state has none |
| `annual_fee_usd` | Recurring state charge per filing cycle (report fee or flat annual tax) |
| `annual_cadence` | How often the recurring requirement falls due: `annual`, `biennial`, or `none` |
| `annual_due` | When the recurring requirement is due, e.g. a fixed date, an anniversary month, or *Not applicable* |
| `annual_fee_note` | Important context for the annual fee — waivers, late fees, per-cycle notes, minimums, or what a combined fee includes. May be empty |
| `approval_time` | Typical state approval time for a formation filing, as recorded in the dataset |
| `verified` | Verification status — see **Verification** below |
| `source` | The source(s) the row was checked against |

## Verification — read this honestly

Not every row carries the same level of verification, and this dataset says so plainly:

- **`verified: true`** — the row was checked against the state's own published fee schedule or Epics Deals' own verified state facts (2026-11-08). **7 rows** are verified this way: Arizona (AZ), Colorado (CO), Delaware (DE), Missouri (MO), Montana (MT), New Mexico (NM), and Wyoming (WY).
- **`verified: false`** — the row is **cross-checked**, not directly state-verified. Each such row was cross-checked across at least two established 2026 references that cite Secretary of State data. The `source` field names those references for every row.

Do not present a `verified: false` row as confirmed directly with a state. Check the `source` field, and confirm with the relevant Secretary of State before relying on a figure.

## Usage

### Python

```python
import json

with open("data/states.json") as f:
    data = json.load(f)

# Cheapest formation fees
for state in sorted(data["states"], key=lambda s: s["formation_fee_usd"])[:5]:
    print(state["code"], state["name"], f"${state['formation_fee_usd']}")

# States with no annual report / annual state fee
no_annual = [s["name"] for s in data["states"] if s["annual_cadence"] == "none"]
print("No annual requirement:", no_annual)
```

### jq

```bash
# Formation fee and annual fee for Wyoming
jq '.states[] | select(.code == "WY") | {name, formation_fee_usd, annual_fee_usd, annual_due}' data/states.json

# Every state with an annual fee of $0
jq -r '.states[] | select(.annual_fee_usd == 0) | "\(.code) \(.name) — \(.annual_requirement)"' data/states.json
```

### CSV

Open `data/states.csv` in any spreadsheet, or load it with `pandas.read_csv("data/states.csv")`, your BI tool, or a database import.

## Live MCP server

This dataset also powers the Epics Deals MCP server, so AI assistants can look up state fees directly:

- **Repo:** [epics-deals-mcp](https://github.com/itsmraza-ship-it/epics-deals-mcp)
- **Endpoint:** `https://epics-deals-mcp.epicsdeals.workers.dev/mcp`

## ⚠️ Fees change

State fees change — legislatures raise them, Secretaries of State revise schedules, and notes like waivers and late penalties have conditions. This dataset is a starting point compiled on 2026-11-09, not a quote.

**Epics Deals confirms the exact fee before filing** for every client. Always confirm the current figure with the state (or with us) before you budget or file.

## License

MIT — see [LICENSE](LICENSE).

---
**Free tools by Epics Deals** — [epicsdeals.com](https://epicsdeals.com) · *Your Partner in Global Expansion*
US LLC formation from **$130 + state fee** · EIN · ITIN · US tax filing · compliance
Part of the [Nonresident Founder Toolkit](https://github.com/itsmraza-ship-it/nonresident-founder-toolkit)
