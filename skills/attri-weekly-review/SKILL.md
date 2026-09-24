---
name: attri-weekly-review
description: Run a weekly review of an Attri workspace — what moved in traffic and search, which findings are new or resolved, what to do next — and plan the chosen actions. Use on a schedule or when a person asks for a weekly summary.
---

# Attri weekly review

A routine, not a report. The output is three decisions the person can take this week, with the numbers behind them, and the findings marked as planned when they agree.

## Steps

1. **Scope.** `list_workspaces`; run the review per workspace if several are enabled.
2. **What moved.** `get_site_overview` for the last 7 days versus the prior 7 (pass `date_from` and `date_to`). Note visitors, sessions and conversions with the change, and the channel mix. Then `get_search_overview` for the same window: clicks, impressions, position, and Attri's search sessions and conversions.
3. **Why it moved.** `list_search_queries` sorted by clicks with the prior period for the biggest gains and losses; `list_top_pages` and `list_sources` for the site side. Name at most three movers each way.
4. **Findings.** `list_findings` with status `open`; call out `new_this_week`. For anything already `planned`, ask whether it shipped; if it did, it should be marked `done`.
5. **Decide.** Pick three findings in score order, skipping `rising`. For each, `get_finding` and turn the evidence into one sentence and one action, following the attri-search-analyst skill for kind-specific advice.
6. **Plan.** If the person agrees and the connection has `findings:write`, `set_finding_status` to `planned` with a note like "weekly review 2026-09-29: rewrite title, target 'utm builder'". Otherwise list them as proposed.

## Output

Keep it to one screen:

- **Week in numbers:** visitors, sessions, conversions, search clicks, search impressions, with the change against the prior week.
- **Moved:** up to three gains and three losses, each with the query or page and the number.
- **Do next:** three findings, each with title, the number that justifies it, the action, the measure.
- **Watching:** rising queries, one line.
- **Housekeeping:** planned findings awaiting a done, anything resolved on its own.

## Rules

- Same rules as the analyst skill: no invented findings, real numbers, say the range.
- If Search Console is not connected, do the site half and say the search half is unavailable.
- Do not plan more than three findings in one review; the loop only works if the list stays short.
- Never mark anything `done` on your own; only the person knows what shipped.
