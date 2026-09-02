# AI Governance / Regulatory Order

A small research site on how export-control and national-security rules try to
hold a new technology, and where that grip slips. Five cases are read through
the documents they leave behind.

This set of five is a **sample**, not a rolling case archive: enough to show
the pattern below working across a full range. The cases cluster in the U.S.
and the EU because that is where this friction has been loudest recently, not
because the pattern is scoped to one jurisdiction.

## The premise

When a new technology comes to be treated as a matter of national security, it
sets a body of regulation in motion: export controls, procurement rules, access
restrictions. That regulation was built for things that stay in place, and a new
technology does not. So before it can act, regulation has to decide what it is
even holding: a chip, an act of access, a nationality, a file. The site reads
recent cases for where that grip holds and where it slips.

## How a case is read

Not a shared model with named stages — just what tends to be left once a
case's outcome (a ban, a ruling, a seizure) stops being the interesting part.
Three questions recur, in roughly this order of attention:

1. **Who designed the categories a case rests on, and who only gets to
   interpret them?** Almost every case turns on a split between a body that
   wrote the operative categories in general terms (usually a legislature) and
   a different body that can only rule on whether a new situation fits inside
   them (an agency, a regulator, a company reading its own obligations).
2. **Where did that split leave a gap new enough that nobody had designed for
   it?** New technology tends to sit outside whatever was designed, not from
   oversight, but because designing for something before it exists isn't
   really possible.
3. **What did each actor do into that gap, and where does what they meant to
   do come apart from what actually happened?** This is where a case actually
   lives, and where it earns the most space: an agency races ahead of its own
   authority, a company picks the cheaper global fix over the narrower legal
   one, an individual routes a shipment through the seam between two
   definitions — and almost none of them land the outcome they were aiming
   for. Somebody, every time, ends up holding a difference they didn't sign
   up for.

Each case page opens with four cells — the object held, where it started
to move, where cost arrives first, and the difference carried — then
question 1 (a short structural note plus a small table), folds question 2
into the same section as a plain sentence or two, and gives question 3
the bulk of the page as a "Who meant what, and what happened instead"
table, one row per actor.

## Case library

- 01 Super Micro — the rule was built to see the firm; the difference landed on individuals
- 02 Remote Access Security Act — the line Congress meant to redraw is still not the line in force
- 03 Anthropic and the Department of War — a foreign-adversary label was pointed at a domestic policy refusal
- 04 Fable / Mythos — a nationality line the system could not read took every customer down
- 05 Claude watermarking — a one-market duty became the default everywhere because matching it cost more

## Working papers

The site sits alongside working papers that developed parts of the inquiry:
*When Governance Cannot Hold Its Object*, *The Cloud Compute Question in U.S.
Export Controls*, and *How Regulation Becomes Firm-Level Exposure*.

## Build

A Jekyll site for GitHub Pages. Styles live in `assets/css/main.css`. The
homepage (`index.html`) carries the premise, the three questions, the case
list, and the working papers in one page — there is no separate framework
subpage. Each case page uses `_layouts/case.html` and its own front matter
(`case_id`, `regulatory_subject`, `description`); there is no `trace` field.

