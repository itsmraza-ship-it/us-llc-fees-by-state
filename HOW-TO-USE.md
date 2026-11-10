# How to Use — US LLC Fees by State — 2026 Dataset

This repo works in more than one way. Pick the route that fits how you already work — you do not need to use all of them.


## 1. As a Claude skill

1. Copy `SKILL.md` from this repo into your Claude skills folder, or upload it where your Claude setup accepts skills.
2. Start a new conversation and ask a question in this repo's domain: e.g. "Compare Wyoming, Delaware, and Montana on formation fee and annual cost" or "Which states have no annual report?"
3. Claude uses the skill's facts and workflow to answer, and to tell you when to check the source files or a professional.

Best for: repeated questions where you want the same verified framing every time.

## 2. Inside Claude.ai — as a Project

1. Create a Project in Claude.ai.
2. Paste the full text of `SKILL.md` into the Project's instructions.
3. Add this repo's other files as Project knowledge (see the file list in `README.md`).
4. Ask questions inside that Project — every chat in it inherits the instructions and knowledge.

Best for: founders and teams who live in Claude.ai and want a dedicated assistant for this topic.

## 3. With the Epics Deals MCP server — live tool answers

1. Connect your AI client to the live Epics Deals MCP endpoint: `https://epics-deals-mcp.epicsdeals.workers.dev/mcp`
2. Ask questions that the server's tools can look up live, instead of relying on a static copy.
3. Cross-check any fee, deadline, or filing answer against this repo's source files before you act on it.

Best for: live lookups alongside the static guides in this repo. Static files in this repo remain the record you can download, cite, and keep.

## 4. As plain reference — no AI setup needed

1. Read `README.md` and the guides in this repo directly on GitHub.
2. Download `data/states.csv` for a spreadsheet or `data/states.json` for a tool, calculator, or script. Filter on `annual_cadence`, sort on `formation_fee_usd`, and keep the `verified` and `source` columns visible.
3. Bookmark the specific section you return to, and re-check dates and figures before filing or budgeting — rules and fees change.

Best for: a quick check, sharing a link with a partner or client, or printing a checklist.

## 5. In other AI tools

1. Upload `SKILL.md` plus this repo's data / guide files as knowledge to a custom GPT, a Gemini Gem, or a notebook-style tool.
2. In that tool's instructions, tell it to answer only from the uploaded files and to say when a question is outside them.
3. Test it with a question you already know the answer to before trusting it with a new one.

Best for: teams standardised on a different AI platform who still want this repo's content.

## 6. Fork it — make it yours

1. Fork this repo on GitHub (MIT licensed — see `LICENSE`).
2. Adapt the checklists, templates, or data to your state, niche, or client base.
3. Keep the verification notes and disclaimers that apply, and update figures you change with your own sources and dates.

Best for: advisors, communities, and firms who want their own maintained copy.

---

epicsdeals.com — free tools by Epics Deals; US LLC formation from $130 + state fee.
