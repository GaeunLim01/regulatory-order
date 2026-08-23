# Reading Regulatory Order

Framework v1.0. A five-layer procedure for reading how regulatory order forms and reaches
the firms standing under it.

Scope is AI-related value chains: semiconductors, computing, cloud, data centers.

Layer A reads conditions, Layer B reads events: two independent classification axes.
Layer C is downstream of both: how A and B actually leave a trace in the record. Layer D
and Layer E work differently again. They do not classify a case at all, they describe
what happens to an order once it exists, regardless of what produced it.

Live at https://gaeunlim01.github.io/regulatory-order/

## Why this

Regulatory systems work by taking hold of a thing: naming it, placing it, timing it,
and assigning someone to answer for it. Where AI is concerned, that grip keeps slipping,
and it slips well before enforcement is ever reached. Rules get drafted against an object
that has already moved, and what arrives at the actors standing under them is not what
the drafters described.

Existing work on how firms handle regulation tends to begin once the demand is already
legible to the firm. What makes it legible is left as background. That step is the subject
here. A regulator that cannot reach an arrangement does not always move its boundary;
sometimes it reaches past the boundary, through what a provider knew, or through a fact it
produces administratively because the world does not supply one. Firms, for their part,
often meet a rule first as a contract clause or a documentation request rather than as
legal text. Both leave marks in the documentary record, and the five layers are the
procedure for reading them.

The procedure was worked out across three working papers, each reading a regulatory
sequence in full:

- [The Cloud Compute Question in U.S. Export Controls, 2009-2026](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=7242040)
- [When Governance Cannot Hold Its Object](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=7035179)
- [How Regulation Becomes Firm-Level Exposure](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=7035280)

The layers are that reading set out on its own, so it can be applied to a case other than
the ones it was built on.

The case library holds worked examples, not a dataset. Five cases are enough to show the
procedure applied and not enough to support a claim about how regulatory orders behave in
general. They sit across object types and event types on purpose.

## Deploying

GitHub Pages builds this with its own Jekyll. No Actions workflow required.

1. Push to `main`.
2. Settings → Pages → Source: **Deploy from a branch**, branch `main`, folder `/ (root)`.

`baseurl` in `_config.yml` is set to `/regulatory-order` and must match the repository
name exactly. Renaming the repo without updating it serves the pages with no stylesheet.
Every internal link goes through `relative_url`, so nothing else needs changing.

## Layout

    _config.yml            site config
    _data/nav.yml          masthead navigation
    _data/schema.yml       controlled vocabulary and validation rules, single source of truth
    _data/cases/           one YAML file per case, nothing else lives here
    docs/case-template.yml blank case to copy into _data/cases/
    _layouts/default.html  page chrome
    assets/css/main.css    design tokens and components
    index.html             overview: methodology entry point, case library entry point
    method.html            Layers A-E and worked examples
    cases/                 case library, waiting on entries

One page carries the whole methodology (Layers A through E as sections, `#layer-b` through
`#layer-e` as anchors), not one page per layer. The landing page carries two things and nothing
else: the methodology, and the case library.

## Adding a case

    cp docs/case-template.yml _data/cases/<slug>.yml

The template lives outside `_data/` on purpose. Jekyll loads every YAML file under
`_data/` recursively, so a template kept alongside the cases would be read as a case
and counted as one. The symptom is a total that is off by one and nothing else.

## Editing the framework

`_data/schema.yml` is authoritative for every enum value. When the framework changes,
change it there first, because the module pages, the case files, and any future validator
all have to agree with it.

Two rules carry the load:

**R3.** Instability conditions are worked through on every case. A blank is allowed but has
to carry a reason, because the reason is what later shows whether the vocabulary is too
narrow. What must never happen is a blank because Layer B says enactment: that would let
Layer B determine Layer A and collapse the two axes into one.

**R6.** An enum value that does not exist yet is flagged, not rejected. Failing the build on
an unknown value would throw away the most useful thing a case can produce. Vocabulary
changes are made in batches once several cases are in, never one case at a time, or the
framework ends up shaped by whichever case came last. Layer C (see below) is what this rule
produced: three cases flagging the same overlap is what justified merging it.

**N1.** No rule may make a Layer A field depend on a Layer B field or the reverse. If a
correlation shows up in the data, that is a finding rather than a constraint. Proof it
holds: the Article 50 watermarking case is a Layer B Enactment, with no dispute
producing the order, and still carries two Layer A conditions.

Where a case does not fit, the case is right and the vocabulary is provisional. Record the
misfit in the `deviations` block on the case file instead of stretching a value to cover it.

## License

Split by intent, not by file extension:

| | |
|---|---|
| Framework content: structure, vocabularies, definitions, method, case library | CC BY 4.0 (`LICENSE-CONTENT`) |
| Site code: stylesheets, layouts, config, scripts | MIT (`LICENSE`) |

Cited source material (rules, gazettes, filings, industry comments) keeps its own terms.
`CITATION.cff` gives GitHub what it needs to render a "Cite this repository" button.

## Design notes

Type is deliberately not coded to any jurisdiction. The framework compares regulatory
orders across national authorities, so setting it in any one government's civic typeface
would put a thumb on the scale. Body is Source Sans 3, chosen for neutrality and for
holding up at small sizes in dense tables; Hangul and CJK fall back to system faces so
entity names in case files render in a matched weight.

The landing page carries exactly two entry points, styled deliberately unlike each other:
Methodology as a plain card matching the rest of the site, Case library as the one
non-white panel on the page. That asymmetry is intentional: the case library is the next
step for most readers, not a fourth peer of the layers, so it gets a different visual
register rather than another spot in a row.

Material kept for completeness but off the main reading path sits in `<details>`:
unexercised vocabulary, dropped fields, secondary caveats. Nothing is deleted for brevity,
only moved one click away.
