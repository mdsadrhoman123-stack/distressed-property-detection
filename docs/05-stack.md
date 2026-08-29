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

## The decisions behind that table

### Why three signals collapse into one score

**What it does.** A damage read from the photos, urgent-seller language in the listing text, and public records for tax and foreclosure status — combined into a single 0–100 number.

**What was turned down.** Any one signal on its own. Each is cheap and each is noisy: a badly lit photo is not distress, and urgent wording is sometimes just marketing.

**What that costs.** Public records coverage varies by county. Where the lookup is thin the score leans on the other two signals, and the alert says so rather than hiding it.

### Why the seeing is bought rather than trained

**What it does.** Listing photos go to a vision provider. The provider does the seeing; there is no model here that I trained.

**What was turned down.** Training a damage model. Better fit in principle — and it needs a labelled dataset that does not exist, plus someone to keep it labelled as the market changes.

**What that costs.** A cost per image and a dependency on someone else's model. And a photo read tells you what is visible in a photo: it is a signal for prioritising a call, not a survey.

### Why the qualifying threshold is configuration

**What it does.** The score that triggers an alert is a set value, meant to be reviewed against the history the system has logged.

**What was turned down.** A fixed number in the build. One less thing to manage — and it silently stops matching reality as a market moves, while continuing to look authoritative.

**What that costs.** Somebody has to review it. A threshold nobody revisits is a threshold that is quietly wrong.

## The rule that applies to all of them

**Nothing that only one person can operate.** A system that depends on the engineer who built it is a liability for the client, however well it runs on the day it is handed over. Every choice above had to survive that test before the technical merits mattered at all.

---

[← 04 · Failure handling](04-failure-handling.md) · [06 · Results →](06-results.md)
