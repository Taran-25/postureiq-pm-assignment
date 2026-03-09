# PostureIQ — Cloud Posture Dashboard


---

## Table of Contents
1. [Problem Statement](#1-problem-statement)
2. [User Persona](#2-user-persona)
3. [User Journey](#3-user-journey)
4. [Friction Points](#4-friction-points)
5. [Proposed Solutions](#5-proposed-solutions)
6. [Wireframes](#6-wireframes)
7. [Write-Up](#7-write-up)

---

## 1. Problem Statement

Cloud Security Engineers at mid-size SaaS companies (200 to 1000 employees) are responsible for securing cloud infrastructure across 10 or more accounts on AWS, GCP, or Azure. Their primary job is to identify and fix misconfigurations before they become incidents, but today they are doing this across 3 to 5 disconnected tools that each speak a different severity language. There is no unified, ranked view of risk. The result is they spend more time triaging tool output than fixing actual problems, and the misconfigurations most likely to cause a breach or trigger an outage go unaddressed simply because they were not visible at the right moment.

---

## 2. User Persona

| Field | Detail |
|-------|--------|
| **Name** | Aakash Sharma, 27 years old |
| **Role** | Cloud Security Engineer, also handles cloud architecture |
| **Company** | High-growth B2C SaaS, around 400 employees, 3 years post Series B |
| **Experience** | 4 years in cloud security, B.Tech from tier 2 college, mostly self-taught through AWS and security certifications |
| **Setup** | Manages 10+ cloud accounts across AWS and GCP, team of 3 people, reports directly to VP Engineering with no CISO above him |
| **Daily Reality** | Opens 4 tabs every morning. AWS Security Hub, Wiz, GCP Security Command Center, and a shared Google Sheet. Spends 45 minutes just building a mental picture before doing any actual work. |
| **Core Frustration** | Cannot quickly tell which misconfiguration will cause a breach, an outage, or land on the VP desk first. Every tool uses different severity words so he re-scores everything in his head. |
| **Goal** | One place, everything ranked by actual impact, know what needs attention today. |
| **Career Motivation** | Wants to be Cloud Security Lead in 2 years. Every undetected incident is a setback. |

---

## 3. User Journey

What Aakash does every day without PostureIQ.

**Step 1 — Opens 4 tabs just to understand what happened overnight (45 minutes)**

AWS Security Hub. Wiz. GCP Security Command Center. Google Sheet. He goes through each one by one. Nothing talks to each other. He is the only thing connecting them.

**Step 2 — Tries to make sense of severity labels across tools**

AWS says HIGH. Wiz says CRITICAL. GCP says MEDIUM. Same type of issue, three different words. Aakash re-scores everything in his head based on experience. No system, no documentation. Different day, possibly a different score for the same issue.

**Step 3 — Picks a rough shortlist from each tool**

He takes 2 or 3 issues from each tool that feel urgent. No ranking logic behind it. Just pattern recognition from years of doing this. Pastes them into the Google Sheet. Now has 6 to 8 items.

**Step 4 — Tries to rank 6 to 8 things that are completely different from each other**

A public S3 bucket. An open GCP firewall. An Azure IAM policy too broad. Different clouds, different resource types, different tools. There is no common scale. He makes a call. Sometimes it is right. Sometimes what he pushed down becomes an incident.

**Step 5 — Writes up every issue manually before handing it off**

For each item he wants to give to his junior engineers, he writes a Slack message or Jira ticket from scratch. What the issue is. Why it matters. What to do. The tools give no plain language explanation so he writes it himself. 20 to 30 minutes per issue.

**Step 6 — Gets pulled back in during fixes**

Junior picks up a ticket, gets stuck, comes back to Aakash. Aakash stops whatever he is doing and explains again or looks up the fix himself. Happens multiple times a day.

**Step 7 — Manually checks if the fix actually worked**

After a fix, Aakash opens the original tool and checks if the alert cleared. Can take hours for the tool to re-scan. Updates the Google Sheet by hand.

**Step 8 — Builds a weekly report from scratch every Friday**

Exports numbers from 3 tools, pastes into a doc or slide, tries to show a trend to the VP. He can show the number went down. He cannot easily explain what changed or why.

---

## 4. Friction Points

| # | Where in Journey | What is Going Wrong |
|---|-----------------|-------------------|
| F1 | Steps 1, 3, 4 | No single place to see all misconfigs across all accounts and clouds |
| F2 | Step 2 | Severity labels mean different things in each tool so ranking is guesswork |
| F3 | Steps 5, 6 | Every handoff requires writing context from scratch and juniors get stuck without fix guidance |
| F4 | Step 7 | Confirming a fix worked is fully manual |
| F5 | Step 8 | Weekly reporting means pulling from 3 tools and building a slide by hand |

### Frictions Being Solved

PostureIQ addresses **F1, F2, and F3.**

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
|-------|--------|
| **Name** | Aakash Sharma, 27 years old |
| **Role** | Cloud Security Engineer, also handles cloud architecture |
| **Company** | High-growth B2C SaaS, around 400 employees, 3 years post Series B |
| **Experience** | 4 years in cloud security, B.Tech from tier 2 college, mostly self-taught through AWS and security certifications |
| **Setup** | Manages 10+ cloud accounts across AWS and GCP, team of 3 people, reports directly to VP Engineering with no CISO above him |
| **Daily Reality** | Opens 4 tabs every morning. AWS Security Hub, Wiz, GCP Security Command Center, and a shared Google Sheet. Spends 45 minutes just building a mental picture before doing any actual work. |
| **Core Frustration** | Cannot quickly tell which misconfiguration will cause a breach, an outage, or land on the VP desk first. Every tool uses different severity words so he re-scores everything in his head. |
| **Goal** | One place, everything ranked by actual impact, know what needs attention today. |
| **Career Motivation** | Wants to be Cloud Security Lead in 2 years. Every undetected incident is a setback. |

---

## 3. User Journey

What Aakash does every day without PostureIQ.

**Step 1 — Opens 4 tabs just to understand what happened overnight (45 minutes)**

AWS Security Hub. Wiz. GCP Security Command Center. Google Sheet. He goes through each one by one. Nothing talks to each other. He is the only thing connecting them.

**Step 2 — Tries to make sense of severity labels across tools**

AWS says HIGH. Wiz says CRITICAL. GCP says MEDIUM. Same type of issue, three different words. Aakash re-scores everything in his head based on experience. No system, no documentation. Different day, possibly a different score for the same issue.

**Step 3 — Picks a rough shortlist from each tool**

He takes 2 or 3 issues from each tool that feel urgent. No ranking logic behind it. Just pattern recognition from years of doing this. Pastes them into the Google Sheet. Now has 6 to 8 items.

**Step 4 — Tries to rank 6 to 8 things that are completely different from each other**

A public S3 bucket. An open GCP firewall. An Azure IAM policy too broad. Different clouds, different resource types, different tools. There is no common scale. He makes a call. Sometimes it is right. Sometimes what he pushed down becomes an incident.

**Step 5 — Writes up every issue manually before handing it off**

For each item he wants to give to his junior engineers, he writes a Slack message or Jira ticket from scratch. What the issue is. Why it matters. What to do. The tools give no plain language explanation so he writes it himself. 20 to 30 minutes per issue.

**Step 6 — Gets pulled back in during fixes**

Junior picks up a ticket, gets stuck, comes back to Aakash. Aakash stops whatever he is doing and explains again or looks up the fix himself. Happens multiple times a day.

**Step 7 — Manually checks if the fix actually worked**

After a fix, Aakash opens the original tool and checks if the alert cleared. Can take hours for the tool to re-scan. Updates the Google Sheet by hand.

**Step 8 — Builds a weekly report from scratch every Friday**

Exports numbers from 3 tools, pastes into a doc or slide, tries to show a trend to the VP. He can show the number went down. He cannot easily explain what changed or why.

---

## 4. Friction Points

| # | Where in Journey | What is Going Wrong |
|---|-----------------|-------------------|
| F1 | Steps 1, 3, 4 | No single place to see all misconfigs across all accounts and clouds |
| F2 | Step 2 | Severity labels mean different things in each tool so ranking is guesswork |
| F3 | Steps 5, 6 | Every handoff requires writing context from scratch and juniors get stuck without fix guidance |
| F4 | Step 7 | Confirming a fix worked is fully manual |
| F5 | Step 8 | Weekly reporting means pulling from 3 tools and building a slide by hand |

### Frictions Being Solved

PostureIQ addresses **F1, F2, and F3.**

F4 and F5 are real but out of scope right now. F4 needs reliable ingestion working first before auto-verify makes sense. F5 needs 30 days of clean data before a trends view is meaningful. Both come after the core is solid.

---

## 5. Proposed Solutions

**Scoring key**

- Impact = how much this actually changes Aakash's day (1 to 5)
- Effort = how hard for engineering to build (1 to 5)
- Score = Impact divided by Effort. Higher means better return on effort.

| # | Solves | What it Does | Impact | Effort | Score |
|---|--------|-------------|--------|--------|-------|
| S1 | F1, F2 | One dashboard showing all accounts and all clouds, severity normalized into one scale, issues ranked by severity and how many days they have been open | 5 | 4 | 1.25 |
| S2 | F1 | Filters save your last selection so Aakash does not reset them every morning | 3 | 1 | 3.0 |
| S3 | F3 | Clicking any row opens a side panel with plain English risk explanation and exact CLI fix command | 4 | 2 | 2.0 |
| S4 | F3 | One click to assign an issue to a team member, logged with who did it and when | 3 | 2 | 1.5 |
| S5 | F1 | Snooze or mark as exception with a reason attached so intentional skips have a record | 3 | 2 | 1.5 |
| S6 | F5 | Trends page showing week over week movement and which accounts are getting worse | 4 | 3 | 1.33 |
| S7 | F4 | Auto check if a fix cleared the alert and update status automatically | 3 | 4 | 0.75 |

### Solutions Chosen: S1, S2, S3, S6

**S1** ships first regardless of its score of 1.25. Every other solution needs it to exist. No dashboard means no drawer to open, no data to trend, nothing to rank. This is the one case where following the formula blindly would be the wrong call.

**S2** scores 3.0, the highest on the list, and costs almost nothing to build. Easy yes.

**S3** directly solves F3. Without it junior engineers still come back to Aakash because the fix guidance lives nowhere.

**S6** goes in as P2. Needs 30 days of data first. Aakash builds his VP sync slide manually every Friday. This replaces that.

### Solutions Not Chosen: S4, S5, S7

**S4** is not worth building for a 3 person team that already uses Slack.

**S5** only has value once daily habit is formed. Adding it before adoption is real means nobody uses it.

**S7** is the most expensive build on the list for what it returns at MVP stage. Cut completely.

---

## 6. Wireframes

Figma wireframes link coming soon.

3 screens designed:
- **Screen 1:** Dashboard — Entry Point, Daily Use
- **Screen 2:** Misconfiguration Detail Drawer
- **Screen 3:** Trends and Progress

---

> The 1-page write-up is in [WRITEUP.md](./WRITEUP.md)
