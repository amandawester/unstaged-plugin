---
name: this-week
description: Tell the couple where their wedding planning stands in UNSTAGED and what to do next. Use when the user asks what to do this week, what is left, what is overdue, what is left to pay and when, what their partner has done lately, or what the two of them still have to decide.
---

Answer from the couple's own planning, and keep it short enough to act on.

## What to do this week

1. `get_guide`: the note UNSTAGED has written for this couple this week, with its suggested actions. Lead with it.
2. `list_todos`: the open to-dos. Pick out what is overdue and what is due in the next two weeks.
3. `get_roadmap` only when they ask what is further ahead.

Give three to five things, most pressing first, each with why now. Do not list every open to-do. Offer to add what is missing with `add_todo`, and to mark things done with `update_todo` when they say they have done them.

## Money

`get_budget` has the total, what is counted, what is paid and what is left, row by row. For "what do we still owe", list the rows with something left to pay, soonest due date first, in the budget's currency. Rows saved as quotes are not commitments; keep them out of the total and say so if there are any waiting for a decision.

## The two of them

- `get_recent_activity` for "what has my partner done". Report it plainly, without grading anyone.
- `list_decisions` shows where the two agree, differ, or have not answered. To record the user's own choice, call `answer_decision` with the option text exactly as listed. It sets only the answer of the person you are talking to; their partner answers for themselves.
- New questions for the two of them go in with `add_decision`, with two to six options.

## The day itself

`get_timeline` for the schedule and the day-of team, `get_seating` for tables and who is not yet seated, `get_shot_list` for the photographer.

## Limits

Some areas may be switched off or read-only for you; the couple chose that when connecting and can change it under Settings in UNSTAGED. If a tool is missing, say which area it belongs to rather than guessing at the content. Membership and billing cannot be reached from here.
