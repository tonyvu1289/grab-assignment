# Grab Vietnam — Analytics Case Study

**Role:** Data scientist - VN
**Debrief:** A 30-minute follow-up session will be scheduled to walk through your submission

---

## What This Assessment Is

We are not testing whether you can write code. We are testing how you think through an ambiguous business problem, how effectively you use AI as a thinking partner, and whether you can translate a messy dataset into a decision a senior leader will act on.

AI tool usage is **expected and evaluated**. Your interaction log with any LLM is a primary submission artefact — it is as important as the analysis itself.

---

## The Situation

Grab Vietnam operates in a fast-paced, highly dynamic market. As the super-app landscape evolves, our Country Analytics team plays a critical role in navigating a complex competitive environment. We leverage large-scale data to optimize market share, drive growth strategies across key metropolitan areas, and ensure our Mobility and Delivery verticals remain the top choice for our users.

In key urban centers, the mobility and delivery sectors are experiencing heightened competition from emerging players.

In response, the Vietnam Growth team launched a **Super-Combo Voucher** — discounting GrabFood orders and GrabBike rides together — piloted **exclusively in HCMC for 6 weeks**.

At the end of the pilot, the Country Head sees a significant GMV jump in HCMC and wants to **immediately roll out the voucher to Hanoi** to replicate the result and pressure the competitor.

The Growth Insights team has 24 hours to respond.

---

## Your Task

> *The Country Head is ready to approve the Hanoi rollout. Should you let him? Build the case — for or against — and be prepared to defend it.*

There is no predetermined correct answer. What we are looking for is how rigorously you interrogate the data before committing to a position.

---

## Dataset

**File:** `grab_vn_case.db` (SQLite)
**Schema reference:** `grab_vn_case_metadata.md`

| Table | Description |
|---|---|
| `transactions` | 182,000+ individual transactions across all cities and services |
| `users` | User profiles — city, payment preference, behavioural segment |
| `weather_daily` | Daily rainfall per city in mm |
| `daily_gmv_summary` | Pre-aggregated view for quick trend queries |

Figures are in **VND thousands**. Divide by 1,000 to get millions.

---

## How to Approach This

Use AI tools to handle the mechanical parts — querying, charting, formatting. Your job is to ask the right questions, pressure-test the outputs, and know when a result looks wrong.

The best submissions are not the most technically elaborate. They are the ones where it is clear the analyst was driving — deciding what to look for, catching where the data or the AI misled them, and ultimately owning the recommendation.

Think beyond the surface numbers. The dataset contains more than one story.

---

## Deliverables

Submit all three of the following:

**1. Analysis artefact**
Your working file — notebook, SQL script, or equivalent. We care about the reasoning trail, not the format.

**2. Executive brief**
A maximum one-page narrative addressed to the Country Head. Write it as if you are sending it before the rollout decision is made. It should state your position clearly and give him the two or three things he must understand before acting.

**3. AI interaction log**
Export the full conversation history from any LLM session used during this assessment (ChatGPT export, Claude conversation, etc.). If you used multiple tools, include all logs. Do not edit or curate the log — we want to see the raw interaction including dead ends and corrections.

---

## Notes

- Any AI tool is permitted: ChatGPT, Claude, Gemini, Copilot, or others
- The debrief will focus on your log: why you prompted the way you did, how you validated outputs, and where you disagreed with the AI
- Schema questions should be answered by `grab_vn_case_metadata.md` before reaching out to your hiring contact

---

## Submission

Send all three deliverables to your hiring contact by the deadline.

Good luck.
