---
name: weekly-report-automation
description: Use when the user wants something done for them on a schedule — "every Monday send me a summary of…", "each morning check…", "every 6 hours look for…" — a recurring report, digest, check or research run in Xenition.
---

# Recurring work with automations

`create_automation` runs a goal on a schedule with one of the user's agents.
Each run's result lands in their Xenition workspace.

## 1. Turn the request into a goal

Write the goal as the instruction the agent will receive every time, complete
on its own: what to look at, what to produce, and in what shape. "Summarise
this week's tasks on the Launch board: done, slipped, blocked — as a short
document" is a goal; "the usual report" is not. If the user has agents
(`list_agents`) and one clearly fits, pass its slug; otherwise leave it empty.

## 2. Pick the schedule

- `daily` at a time, e.g. 08:30
- `weekly` on days, e.g. mon,thu at 09:00
- `every` N minutes or hours — 15 minutes is the minimum

A time needs a time zone. If the user has not said one, ask — once — which
time zone they are in. Never assume UTC for a clock time.

## 3. Confirm, then create

Before calling `create_automation`, say in one line what will run and when
("Every Monday at 09:00 London time: a summary of the Launch board"). Create it
after the user agrees, then repeat back the schedule the tool confirms.

## Managing them

`list_automations` shows what exists and whether each is on.
`set_automation_enabled` pauses or resumes one — use the id from the list, and
confirm which one when names are similar.

## Limits — say these plainly

Automations cannot send email, texts or chat messages; results are saved in
Xenition. Each run uses the user's credits like a manual run.
