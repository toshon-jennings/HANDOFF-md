# Universal Agent Handoff Specification (`HANDOFF.md`)

A platform-agnostic, zero-overhead standard for state persistence and context preservation between AI agent sessions. 

## 🧘♂️ The Philosophy: The Zen of AI Context
When an AI agent experiences a session timeout, token reset, or platform interruption, the human user wastes critical momentum re-explaining the project. The natural instinct is to build complex state-tracking databases or heavy JSON frameworks to solve this. 

We believe that **simple is better than complex**. 

Large language models thrive on raw text that mirrors their training data. Complex syntax introduces token noise; clean markdown eliminates it. This repository establishes a universal `HANDOFF.md` template designed around three core principles:

1. **Beautiful is better than ugly:** High scannability, clear typography, and intentional white space make state transitions seamless for both humans and machines.
2. **Readability counts:** Uses binary visual cues (`- [x]` vs `- [ ]`) that LLMs can parse with near-zero cognitive overhead.
3. **Protect the "Why", not just the "What":** Code changes and file states are easy to scan. This spec fiercely protects human intent, strategic constraints, and documented dead ends so the next agent never loops.

---

## 🛠️ How to Use
Drop the `HANDOFF.md` file into the root directory of any active workspace—whether you are engineering software, analyzing datasets, or writing complex content. Instruct your agent to update it before a session ends, or use it as a "panic drop" file when a context window limits out.

---

## 📄 The Master Specification Template
Below is the standard layout. Keep it pure, minimal, and stripped of unnecessary noise.
