# 04 · Failure handling

The part of the system that took the longest to build and gets written about the least.

---

| What goes wrong | How it is detected | What the system does | Who finds out |
| :--- | :--- | :--- | :--- |
| **Photo read fails or returns nothing** | Provider error or empty result | Score is built from the remaining signals and marked partial | Alert says the score is partial |
| **Public records lookup unavailable** | API error | Retry, then score without it rather than dropping the listing | Alert notes the missing signal |
| **Listing feed goes quiet** | No results across an expected window | Treated as a fault, not as “no good listings” | Alert — silence is suspicious |
| **Same listing appears twice** | Record check | Second occurrence does not re-alert | Nobody — by design |
| **Score sits just under the threshold** | Scoring logic | Logged rather than discarded, so the threshold can be reviewed | Visible in the log, not an alert |

## The three rules behind that table

**1 — Fail closed, not open.** When the system cannot establish that an action is safe, it holds. A held item is a visible problem. An item processed on a guess is an invisible one.

**2 — Nothing disappears.** Anything that cannot be completed is recorded where a human can find it later, not dropped from the run.

**3 — Silence is a fault.** An empty result where results were expected is treated as a possible failure of the source, not as an absence of work. This is the check most automations skip.

---

[← 03 · Architecture](03-architecture.md) · [05 · The stack →](05-stack.md)
