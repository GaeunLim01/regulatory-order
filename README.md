# AI Governance / Regulatory Order

A small research site on how export-control and national-security rules try to
hold a new technology, and where that grip slips. Five cases are read through
the documents they leave behind.

## The axis

When a new technology comes to be treated as a matter of national security, it
sets a body of regulation in motion: export controls, procurement rules, access
restrictions. That regulation was built for things that stay in place, and a new
technology does not. So before it can act, regulation has to decide what it is
even holding: a chip, an act of access, a nationality, a file. The site reads
recent cases for where that grip holds and where it slips.

## Two independent layers of reading

The site reads each case through two layers. They do not nest inside one
another. Each answers a different question, and a case's position in one
layer says nothing about its position in the other.

**The cycle (regulation as subject).** Read in sequence, the cases move
through the same four stages, entered in a different order and at a
different pace each time:

1. Trigger — a technology appears, or comes to be treated as a security matter
2. Focus — regulation draws a line to catch it
3. Friction — the line meets the field and bends
4. Re-response — a new line follows, or the matter is left open

This layer follows the regulation itself, as though it were the thing moving
through time.

**The lenses (actors around the object).** Regardless of where a case sits
in the cycle, three lenses read how the actors around a regulation
(regulators, providers, courts, users) interact with it as a shared object:

- Ordering (upper layer) — who draws the line and what they fix it on
- Manifestation (upper layer) — through what instrument it operates
- Distribution (lower layer) — how the weight moves, and onto whom

Which lens is under the most strain shifts case by case, and can shift within
a single case, independent of which cycle stage that case is in.

## Case library

- 01 Super Micro — servers diverted around export control
- 02 Remote Access Security Act — is remote use of compute an export?
- 03 Anthropic and the Department of War — a contested limit on how a model is used
- 04 Fable / Mythos — who is allowed to access a model
- 05 Claude watermarking — marking AI content under EU rules

Each case page carries a mini path through the four stages, set in its front
matter via a `trace` field (for example: `Focus, Friction*, Re-response`, where
`*` marks a stage the case dwelled in and `!` marks one left open).

## Working papers

The site sits alongside working papers that developed parts of the inquiry:
*When Governance Cannot Hold Its Object*, *The Cloud Compute Question in U.S.
Export Controls*, and *How Regulation Becomes Firm-Level Exposure*.

## Build

A Jekyll site for GitHub Pages. Styles live in `assets/css/main.css`; the case
mini-trace is rendered by `_layouts/case.html` from each case's front matter.
