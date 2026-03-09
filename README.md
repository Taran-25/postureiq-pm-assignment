# PostureIQ — Cloud Posture Dashboard

---

## Table of Contents
1. [Problem Statement](#1-problem-statement)
2. [User Persona](#2-user-persona)
3. [User Journey](#3-user-journey)
4. [Friction Points](#4-friction-points)
5. [Proposed Solutions](#5-proposed-solutions)
6. [Wireframes](#6-wireframes)
7. [Write-Up](./WRITEUP.md)

---

## 1. Problem Statement

Cloud Security Engineers at mid-size SaaS companies (200 to 1000 employees) are responsible for securing cloud infrastructure across 10 or more accounts on AWS, GCP, or Azure. Their primary job is to identify and fix misconfigurations before they become incidents, but today they are doing this across 3 to 5 disconnected tools that each speak a different severity language. There is no unified, ranked view of risk. The result is they spend more time triaging tool output than fixing actual problems, and the misconfigurations most likely to cause a breach or trigger an outage go unaddressed simply because they were not visible at the right moment.

---

## 2. User Persona

| Field | Detail |
|---|---|
| **Name** | Aakash Sharma, 27 years old |
| **Role** | Cloud Security Engineer, also handles cloud architecture |
| **Company** | High-growth B2C SaaS, around 400 employees, 3 years post Series B |
| **Experience** | 4 years in cloud security, B.Tech from tier 2 college, mostly self-taught through AWS and security certifications |
| **Setup** | Manages 10+ cloud accounts across AWS and GCP, team of 3 people, reports directly to VP Engineering with no CISO above him |
| **Daily Reality** | Opens 4 tabs every morning. AWS Security Hub, Wiz, GCP Security Command Center, and a shared Google Sheet. Spends 45 minutes just building a mental picture before doing any actual work. |
| **Core Frustration** | Cannot quickly tell which misconfiguration will cause a breach, an outage, or land on the VP Engineering desk. Every tool ranks things differently. |

---

## 3. User Journey

**Step 1 — Opens AWS Security Hub**

Aakash starts the morning here. There are 47 findings. Some are critical, some are high. He does not know yet which ones are new, which are old, or which ones actually matter today. He exports to a CSV.

**Step 2 — Switches to Wiz**

Wiz calls things differently. What AWS calls High, Wiz might call Critical. He adds a second column to his spreadsheet and tries to reconcile them. This is not automatic. It is a judgment call every time.

**Step 3 — Opens GCP Security Command Center**

Third tab, third severity language. He pastes more rows into the spreadsheet. Now he has one spreadsheet with 60 to 80 rows, three columns of severity, and no consistent way to rank them.

**Step 4 — Tries to rank 6 to 8 things that are completely different from each other**

A public S3 bucket. An open GCP firewall. An Azure IAM policy too broad. Different clouds, different resource types, different tools. There is no common scale. He makes a call. Sometimes it is right. Sometimes what he pushed down becomes an incident.

**Step 5 — Assigns issues to junior engineers**

Aakash picks the items that need fixing and assigns them to his junior engineers via Slack or Jira. He does not write any context at this step. He just assigns the ticket and moves on.

**Step 6 — Gets pulled back in during fixes**

Junior picks up the ticket, gets stuck, and comes back to Aakash. There is no plain language explanation of why the issue matters. There is no fix guidance. Aakash stops whatever he is doing and writes it all from scratch. 20 to 30 minutes per issue. Happens multiple times a day.

**Step 7 — Manually checks if the fix actually worked**

After a fix, Aakash opens the original tool and checks if the alert cleared. Can take hours for the tool to re-scan. Updates the Google Sheet by hand.

**Step 8 — Builds a weekly report from scratch every Friday**

Exports numbers from 3 tools, pastes into a doc or slide, tries to show a trend to the VP. He can show the number went down. He cannot easily explain what changed or why.

---

## 4. Friction Points

| # | Where in Journey | What is Going Wrong |
|---|---|---|
| F1 | Steps 1, 3, 4 | No single place to see all misconfigs across all accounts and clouds |
| F2 | Step 2 | Severity labels mean different things in each tool so ranking is guesswork |
| F3 | Step 5 | Assigning issues requires switching to Slack or Jira manually with no context attached |
| F4 | Step 6 | Every handoff requires writing context from scratch and juniors get stuck without fix guidance |
| F5 | Step 7 | Confirming a fix worked is fully manual |
| F6 | Step 8 | Weekly reporting means pulling from 3 tools and building a slide by hand |

### Frictions Being Solved

PostureIQ addresses **F1, F2, F4, and F6**.

F3 is real but downstream. Assign workflows only matter once Aakash can see and rank issues clearly, which F1 and F2 solve first. F5 needs reliable ingestion working before auto-verify makes sense. Both come after the core is solid.

---

## 5. Proposed Solutions

### Scoring key

- Impact = how much this actually changes Aakash's day (1 to 5)
- Effort = how hard for engineering to build (1 to 5)
- Score = Impact divided by Effort. Higher means better return on effort.

| # | Solves | What it Does | Impact | Effort | Score |
|---|---|---|---|---|---|
| S1 | F1, F2 | One dashboard showing all accounts and all clouds, severity normalized into one scale, issues ranked by severity and how many days they have been open | 5 | 4 | 1.25 |
| S2 | F1 | Filters save your last selection so Aakash does not reset them every morning | 3 | 1 | 3.0 |
| S3 | F4 | Clicking any row opens a side panel with plain English risk explanation and exact CLI fix command | 4 | 2 | 2.0 |
| S4 | F6 | Trends page showing week over week movement and which accounts are getting worse | 4 | 3 | 1.33 |
| S5 | F1 | Snooze or mark as exception with a reason attached so intentional skips have a record | 3 | 2 | 1.5 |
| S6 | F5 | Auto check if a fix cleared the alert and update status automatically | 3 | 4 | 0.75 |

### Solutions Chosen: S1, S2, S3, S4

**S1** ships first regardless of its score of 1.25. Every other solution needs it to exist. No dashboard means no drawer to open, no data to trend, nothing to rank. This is the one case where following the formula blindly would be the wrong call.

**S2** scores 3.0, the highest on the list, and costs almost nothing to build. Easy yes.

**S3** directly solves F4. Without it, juniors still come back to Aakash because the plain English brief and fix guidance live nowhere.

**S4** goes in as P2. Needs 30 days of data first. Aakash builds his VP sync slide manually every Friday. This replaces that.

---

## 6. Wireframes

**Live prototype:** [PostureIQ on Figma Make](https://www.figma.com/make/nlUZr9QnhU25pLs7sdYXxp/PostureIQ?fullscreen=1&t=iwJDarwlwA5Hc7Pg-1)

Built in Figma Make. Three interactive screens navigable via the top nav. Annotations visible on each screen explain the design decisions inline.

---

### Screen 1 — Unified Dashboard (P0 · Solves F1, F2)

The landing screen. Shows all active misconfigurations across AWS, GCP, and Azure in a single ranked table. Severity is normalized into one scale so Critical always means Critical regardless of which tool flagged it. Issues are sorted by severity first, then by how many days they have been open — so the most dangerous and most neglected items surface at the top.

KPI cards at the top give Aakash an instant read: 47 Critical, 132 High, 89 Medium, 23 resolved this week with a delta chip showing "21 fewer than last week."

Filter bar (All Clouds / All Accounts / All Severities) persists across sessions. Aakash sets it once — it sticks.

---

### Screen 2 — Detail Drawer (P1 · Solves F4)

Opens when Aakash clicks any row in the table. No page navigation — it slides in as a panel over the dashboard.

Shows the exact misconfiguration ARN, severity badge, cloud tag, and compliance tags (PCI-DSS 1.3, SOC2 CC6.1). Below that:

- **Why This Matters** — a plain English paragraph explaining the business risk. No tool jargon. Aakash can forward this directly to his junior without writing anything.
- **How to Fix** — a copy-paste AWS CLI block with the exact commands to remediate. One click copies it to clipboard. Junior pastes it into terminal and runs it.


---

### Screen 3 — Trends and Progress (P2 · Solves F6)

Accessible via the Trends tab in the top nav. Requires 30+ days of historical data to be meaningful — this is why it is P2.

Two sections:

- **Issue Count Over Time** — line chart showing Critical (65→47, declining), High (~133, stable), and Medium (71→89, rising) over the last 30 days. Aakash can see at a glance that Critical is getting fixed while Medium is growing — a signal to re-prioritize.
- **Account Health Leaderboard** — ranks all cloud accounts by total active issues, worst at top. Aakash can identify which account needs attention this week without building a spreadsheet.

This screen replaces the Friday slide Aakash manually builds from 3 tools every week.
