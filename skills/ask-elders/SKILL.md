---
name: ask-elders
description: >
  Surveys how experts, practitioners and earlier builders handled what the
  user is about to do, then returns approach candidates and a recommendation
  fitted to the user's situation. Covers two axes: field practice (what people
  do and why, including adjacent fields that solved the same kind of problem)
  and prior implementations (papers, open source, products and their limits).
  Separates verified evidence from the agent's own judgment and says what it
  could not read. Use when the user asks how others, experts or seniors did
  something, whether anyone has built something like this, or what the common
  or best approach is. Triggers include "how did experts do this", "how did
  others handle this", "has anyone built this", "what's the standard way",
  "고수들은 어떻게 했어", "전문가들은 어떻게 했어", "다른 사람들은 어떻게 했어",
  "이미 만든 사람 있어?". Not for single-fact lookups or for deciding whether
  to adopt a specific tool.
metadata:
  version: "0.1"
---

# Ask Elders

## Contents

- Tools
- Flow
- Evidence labels
- Output
- Boundaries

Find out how people who have done this before did it, and turn that into
candidates and a recommendation for this user. The value is the fit to the
user's situation, not a pile of examples. A good answer works whether the
session already holds rich context or almost none.

## Tools

| Need | Required | Recommended | Fallback |
|---|---|---|---|
| Search and read sources | Web search and a page reader (any one pair) | A clean-text reader for web pages; a code host reader for repositories | Without web access, say so, give only what you know from training, and label every item Judgment. Do not present it as a survey. |
| Parallel collection | None | A sub-agent that only gathers and reports sources | Gather the sources yourself, one axis at a time. |

## Flow

1. **Read the situation.** Take the goal, audience, constraints and what was
   already tried from the conversation, any file or data the user pointed to,
   and the repository. If a missing item would change the answer, ask at most
   one question; if it goes unanswered, continue. Put the assumptions you made
   in the first lines of the answer so the user can correct them in one line.
2. **Size the work.** A question one search settles gets a direct answer and
   this process is skipped. Otherwise use one collector for one axis and at
   most three for a broad question. Set the stop condition before searching,
   for example the question to settle and a cap on searches, and stop when
   the sources start repeating. Do not add collectors to a simple question.
3. **Search two axes.**
   - Practice: what practitioners do, in what order, with what tools, why, and
     where it failed.
   - Prior implementations: papers, open source, products, and their limits.
   - Also look in adjacent fields that solved the same kind of problem, using
     their vocabulary, and extract the principle they share in one line. If the
     user's own field has no precedent, say so before turning to other fields.
   - Prefer primary sources: the practitioner's own writing, talks, code and
     post-mortems. Follow citations from the best sources and vary the search
     terms. Do not call a search complete.
4. **Delegate collection only.** Ask a collector for each claim, its URL,
   whether it read the page or saw only a snippet, and the limit of the claim.
   Treat its notes as routing aids, not as authority. Reopen the source behind
   every claim that carries the recommendation before relying on it.
5. **Fit to the user.** Compare candidates against the user's constraints and
   audience. Flag survivorship bias (only successes are visible), context
   mismatch (the expert's conditions differ), and claims where what people say
   they do differs from what they did.

## Evidence labels

Label each substantive point:

- **Verified**: you read the source page or file yourself.
- **Reported**: a collector summary or a search snippet; not yet read.
- **Judgment**: your own inference or recommendation.

Never invent a source, a person, a quote or a repository. If nothing solid was
found, say so briefly. Separate "the search failed or timed out" from "the
search ran and found nothing".

## Output

1. **Assumptions** (one to three lines).
2. **Shared principle** from the survey, in one line, when there is one.
3. **Candidates**: at most five rows (approach, who did it, why, limits,
   label).
4. **Recommendation**: with rich context, one pick with trade-offs tied to the
   user's constraints. With thin context, branches by condition ("if your data
   is A, this; if B, that") and the criterion that decides between them.
5. **Search log and limits**: sources searched, search date, terms, inclusion
   rule, and a Not verified / Not found list.
6. **One closing line**: say what would narrow the answer, and stop.

Keep it short enough to read in one pass. Offer further depth instead of
dumping it.

## Boundaries

Read-only. Do not edit files, install anything or publish, and do not change
the user's work from this survey unless asked. A survey is evidence for a
decision the user makes.
