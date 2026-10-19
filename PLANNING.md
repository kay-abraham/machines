# How I plan a machine

The work machines in this repo each started as a miss I felt first. The rule I work by: the day after the mistake, build the thing that makes it impossible. These are the steps the machines here have in common.

## 1. Start from a miss I felt first

| The miss | The machine |
|---|---|
| Invoices sat twenty-plus days overdue and nobody acted until finance escalated. | [Overdue Monitor](overdue-monitor/) |
| Custom prices expired quietly and the customer got a bill shock. | [Override Watch](override-watch/) |
| Accounts grew quietly and no alarm went off. | [Expansion Engine](engine/) |
| A customer left after an offer repeated terms they'd already refused. | The Engine's refused-terms guard |
| A CRM source went missing for two months and no alert fired. | The Engine's fail-open rule |
| The team's numbers didn't match Finance's. | [Margin rebuild](margin/) |
| Every pricing or usage question became a data request, and a wait. | [SQL library](sql-library/) |
| The desk said who to write to, and the writing still took the afternoon. | [Drafting agent](drafting-agent/) |

## 2. Build the smallest machine that prevents it

The goal is a tool that makes the job smaller, with as few moving parts as the job allows. Some examples:

- Override Watch is one Redash query, one n8n schedule and a Slack message per price.
- The SQL library is ten shared queries with parameters.
- Standard library first: the Engine's only dependency beyond Python's standard library is the Apify SDK.

## 3. Add guards for silent failure

Failures announce themselves. A machine skips a missing feed or token and reports it, and a parser that stops matching raises an alarm.

- The Engine lets a missing feed fail open and says so on the desk.
- The News Intelligence Agent lists the health of each source in every record.
- The Overdue Monitor retries the warehouse query and stays inside Slack's limits.
- Override Watch stretches its Friday window so weekend expiries still get a warning.
- State between runs lives in a named store, so a crash can't double-post or drop a window.

## 4. Roll it out with the people who share the problem

- Override Watch and the Overdue Monitor are co-owned with RevOps.
- The Engine tags every account with its owner, so one instance serves the whole team: desks for 7 Product Advocates.
- The Engine's report tab started as a colleague's request.

## 5. Keep the customer decision with a person

The tools inform and I decide what reaches a customer. The drafting agent writes drafts only. I read, edit and send each one.

## 6. Measure what changed

Each machine page ends with what changed, as a count or a plain fact:

- Margin rebuild: every month matches Finance's report to the cent.
- Override Watch: the account manager hears seven days ahead.
- Overdue Monitor: a daily digest per account manager and a Monday summary for finance ops.
- Expansion Engine: quietly growing accounts now show up on the desk, and 786 tests run every night.
- SQL library: pricing and usage questions take minutes.
