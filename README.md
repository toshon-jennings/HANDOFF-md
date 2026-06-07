# Universal Agent Handoff Specification (`HANDOFF.md`)

A platform-agnostic, zero-overhead standard for state persistence and context preservation between AI agent sessions. 

## 🧘♂️ The Philosophy: The Zen of AI Context
When an AI agent experiences a session timeout, token reset, or platform interruption, the human user wastes critical momentum re-explaining the project. The natural instinct is to build complex state-tracking databases or heavy JSON frameworks to solve this. 

We believe that **simple is better than complex**. 

Large language models thrive on raw text that mirrors their training data. Complex syntax introduces token noise; clean markdown eliminates it. This repository establishes a universal `HANDOFF.md` template designed around three core principles:

1. **Beautiful is better than ugly:** High scannability, clear typography, and intentional white space make state transitions seamless for both humans and machines.
2. **Readability counts:** Uses binary visual cues (`- [x]` vs `- [ ]`) that LLMs can parse with near-zero cognitive overhead.
3. **Protect the "Why", not just the "What":** State changes and file layouts are easy to scan. This spec fiercely protects human intent, strategic constraints, and documented dead ends so the next agent never loops.

---

## 🛠️ How to Use
1. Drop the `HANDOFF.md` file into the root directory of your workspace.
2. Copy the contents of the `.agentrules` file into your AI's custom instructions, system prompt, or local workspace configuration. This ensures the agent actively maintains the state without needing manual reminders.

---

## 📄 The Master Specification Template
Below is the standard layout. Keep it pure, minimal, and stripped of unnecessary noise.

```markdown
# AGENT HANDOFF STATE

## 🎯 High-Level Objective
* **Core Goal:** [Clear, single-sentence summary of the ultimate deliverable]
* **Target Domain/Format:** [e.g., Interactive web app, data analysis spreadsheet, market report]
* **Style Constraints:** [e.g., Minimalist prose, strict data validation, specific formatting rules]
* **Key Decisions & Rationale:** [e.g., Chosen architecture, library selections, design patterns]

## 🕒 Session Metadata
* **Last Updated:** [YYYY-MM-DD HH:MM:SS UTC]
* **Previous Agent/Model:** [e.g., Gemini 3.5 Flash]
* **Current Status:** [🟢 Success / 🟡 In-Progress / 🔴 Interrupted / ❌ Blocked]

---

## 📂 Environment & Source Context
* **Active Working Files:** [List of documents, scripts, or directories currently open]
* **Sources/Data Inputs Utilized:**
  * `input_file.ext` -> [Brief note on what data has already been parsed or extracted]
* **Git Branch & Commit:** [e.g., Branch `main`, HEAD at `a1b2c3d`]
* **Running Services/Ports:** [e.g., Vite dev server on localhost:3000]
* **Verification Command:** [e.g., `npm run test` or `go test ./...`]
* **Hard Constraints:** [e.g., Environment limits, word counts, dependency restrictions]

---

## 📊 Progress Ledger

### ✅ Completed Milestones
- [x] Phase 1 baseline established.
- [x] Primary structure and constraints validated.

### ⏳ In-Flight / Interrupted (Pick up here!)
- [ ] Currently executing [Task X]. *(Note: Provide the exact line, section, or logical block where execution halted).*

### 📋 Remaining Backlog
- [ ] Immediate next milestone.
- [ ] Final polishing and verification.

---

## ⚠️ Known Blind Spots & Dead Ends
* **Gaps/Issues:** [Detail failed approaches, rate limits, or missing data to prevent the next agent from looping]
* **Assumptions Made:** [Key logical or architectural choices made implicitly during this session]

---

## 🤖 Instructions for the Next Agent
> "Review the 'In-Flight' section above. Open the active working files, run the verification command to confirm the project status, and immediately resume execution from the interrupted step. Adhere strictly to a philosophy of minimalism: keep solutions simple, precise, and highly readable."
```
