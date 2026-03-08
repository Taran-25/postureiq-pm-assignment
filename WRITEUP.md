# PostureIQ — 1-Page Write-Up

## Problem Being Solved

Cloud Security Engineers managing 10 or more accounts across AWS, GCP, and Azure spend more time figuring out what to fix than actually fixing it. They open 3 to 5 tools every morning, translate severity labels in their head, and rank issues by gut feel. PostureIQ gives them one place to see everything, already ranked, with context attached.

---

## Proposed Features and Prioritization

| Feature | What it Does | Impact | Effort | Score | Priority |
|---------|-------------|--------|--------|-------|----------|
| Unified dashboard | All accounts, all clouds, severity normalized, ranked by severity and age | 5 | 4 | 1.25 | P0 |
| Persistent filters | Filters save across sessions | 3 | 1 | 3.0 | P0 |
| Detail drawer | Side panel with plain English risk and CLI fix command | 4 | 2 | 2.0 | P1 |
| Trends page | Week over week movement, account health leaderboard | 4 | 3 | 1.33 | P2 |

The unified dashboard scores 1.25 which looks low but it ships first regardless. Every other feature on this list needs it to exist. This is the one case where following the score blindly would be the wrong call.

---

## What I Deliberately Left Out

- **One click assign inside the tool** — a 3 person team already uses Slack. Not worth the build.
- **Snooze and exception tracking** — only useful once daily habit is formed. Adding it before adoption is real means nobody uses it.
- **Auto-verify fix** — most expensive build on the list. Needs reliable two-way sync with every cloud provider. Too much for MVP.

---

## Success Metrics

- **Primary:** Mean time to remediate critical misconfigs. Target 30% reduction in 90 days.
- **Secondary:** Percentage of criticals resolved within 24 hour SLA.
- **Engagement:** Daily active users on the security team. If PostureIQ is Aakash's first tab every morning the product has worked.
- Not measuring total misconfigs detected. That is an input not an outcome.

---

## Dev Action Items

- Ingestion strategy: pull vs push for AWS Config, GCP SCC, Azure Defender with an agreed latency SLA per provider.
- Severity normalization schema versioned and monitored for taxonomy changes from providers.
- RBAC enforced at the data layer not just the UI. If you do not have access the data never reaches your screen.
- Pagination and lazy loading required before launch. A 10 account environment can easily have 5000 or more rows.

---

> Full context — persona, user journey, friction points, and solution scoring — is in [README.md](./README.md)
