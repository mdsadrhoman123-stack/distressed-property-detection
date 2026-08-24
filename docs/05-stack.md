# 05 · The stack

Each choice, and the reason for it.

---

| Component | Why this one |
| :--- | :--- |
| **n8n** | Orchestrates the three signal paths in one workflow |
| **AI vision API** | Listing photos are sent out for a visible-damage read — the provider does the seeing, not a model I trained |
| **AI text API** | Listing descriptions are read for urgent-seller language |
| **Public records API** | Unpaid taxes and foreclosure status |
| **Alerting** | Gets the investor on the phone first |

## What was deliberately not used

- **A hosted automation SaaS.** Client data would transit a third party, and the failure handling would be limited to what that vendor exposes.
- **A bespoke application where automation was enough.** The cheapest system to maintain is the one with the least custom code in it.
- **Anything that could not be redeployed by someone else.** A system only one person can operate is a liability for the client.

---

[← 04 · Failure handling](04-failure-handling.md) · [06 · Results →](06-results.md)
