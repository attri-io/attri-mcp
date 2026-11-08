---
name: attri-content-writer
description: Turn an open Attri finding into the content it calls for — new title and meta description, a page section, or a merge plan — written in the site's own voice, then plan it so Attri measures the result. Use when a person asks to write, draft, fix or act on a finding, or asks "what should I write" for their site.
---

# Attri content writer

Attri finds the gap and measures the outcome. You write what fills the gap, nothing more. Every draft starts from one finding and its evidence; you never write content no finding asked for, and you never pad a page to look busy.

## Steps

1. **Pick the finding.** If the person named one, use it. Otherwise `list_findings` (status `open`) and take the top by score that is not `drop` or `rising`. Say which one and why it is first.
2. **Read the evidence.** `get_finding`. Quote its numbers back in one line: the query, impressions, position, CTR or the pages involved, and the sessions and conversions on the page.
3. **Start from Attri's draft.** If `get_finding` returns a `draft`, that is Attri's own title, description and outline for this finding. Build on it rather than starting over, and say so.
4. **Read the page.** If you can fetch the page, or the site's source is open in this session, read it: current title, description, headings and body. Match its voice, terms and level of detail. If you cannot read it, say so and draft from the evidence and the draft alone.
5. **Draft by kind** (below).
6. **Check the draft** against the quality rules (below) before showing it.
7. **Track any new call to action.** If the draft adds a link to a signup, demo or offer, and the connection has `links:write`, offer `create_link` with UTM parameters so the content's conversions are attributed. Confirm destination and slug first.
8. **Plan it.** If the person accepts and the connection has `findings:write`, `set_finding_status` to `planned` with a note naming the change, e.g. "content writer 2026-10-27: new title leading with 'utm builder'". Tell them to mark it `done` once it is live; that starts Attri's measurement of the finding's `measure`.

## Draft by kind

| Kind | What to write |
|---|---|
| `ctr_gap` | Three title options (50–60 characters) and three meta descriptions (140–155 characters). Lead with the query in natural words; the description gives a reason to click that matches the query's intent. Recommend one pair and say why. |
| `update_page` | The section the page is missing: an H2 phrased as the top query, a direct answer in the first two sentences, then the supporting detail. Add a revised title if the current one does not mention the query. List one or two pages that already rank which should link here, with the anchor text. |
| `question` | An answer block for the top of the page: an H2 worded as the top question, then a direct answer in two or three sentences that also covers the other phrasings in the evidence. If the phrasings ask about different things (price, guarantees, flexibility), add one FAQ entry per distinct question, each answered in one or two sentences. Do not rewrite the rest of the page. |
| `cannibalization` | A plan, not prose: which page should own the query (higher conversions first, then position), what to move from the other page into it, whether to redirect or retarget the other page, and which internal links to change. Draft the moved section only if the person asks. |
| `drop` | No draft. Diagnose first, following the attri-search-analyst skill. |
| `rising` | No draft. It is working; leave it alone. |

## Quality rules

Every draft must pass all of these. If one fails, fix it before showing it.

- **Answer first.** The question the query asks is answered in the first two sentences of the section or page.
- **Question headings.** H2s use the words people search with, taken from the finding's queries where possible.
- **Sourced numbers.** Every number is either from the person's own site or product, or carries a link to its source. No invented statistics.
- **No invented facts.** Never claim features, prices, results or customers the page or the person has not given you. Ask when you need one.
- **Named author.** If the page has an author, keep it. If it has none and it is an article, suggest adding a named author with a short bio line.
- **Their voice.** Use the site's terms and tone, not generic marketing copy.

## Output

- One line: the finding, its number, and what this draft changes.
- The draft, ready to paste, with title and description shown as plain text the person can copy.
- What will measure it (the finding's `measure`) and when to look (about 28 days after it is live).
- Offer to track a link or plan the finding, if not already done.

## Rules

- One finding per draft. If asked to "fix everything", do the top three by score, one after another.
- Never mark a finding `done` yourself; only the person knows when it shipped.
- Never publish or edit the live site unless the person asks and you have access in this session; the default output is a draft to review.
- Same reading rules as the attri-search-analyst skill: no invented findings, quote real numbers, say the date range.
