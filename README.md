# How Regulatory Order Reaches Actors, Framework v4

A three-module framework for tracing how regulatory order forms and reaches actors
across AI-related value chains: semiconductors, computing, cloud, data centers.

There are two independent classification axes: Module 1 reads conditions, Module 2 reads
events. Module 3 works differently. It does not classify a case at all, it describes what
happens to an order downstream once that order exists.

Live at https://gaeunlim01.github.io/regulatory-order/

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
    index.html             overview: two axes, Module 3 band, scope
    module-1.html          Instability
    module-2.html          Formation history
    module-3.html          Downstream
    method.html            tagging template and measured fields
    cases/                 case library, waiting on entries

One page per module. The landing page carries the structure and nothing else, so a reader
who stops there still comes away with the 2+1 shape.

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
narrow. What must never happen is a blank because Module 2 says enactment: that would let
Module 2 determine Module 1 and collapse the two axes into one.

**R6.** An enum value that does not exist yet is flagged, not rejected. Failing the build on
an unknown value would throw away the most useful thing a case can produce. Vocabulary
changes are made in batches once several cases are in, never one case at a time, or the
framework ends up shaped by whichever case came last.

**N1.** No rule may make a Module 1 field depend on a Module 2 field or the reverse. If a
correlation shows up in the data, that is a finding rather than a constraint.

Where a case does not fit, the case is right and the vocabulary is provisional. Record the
misfit in the `deviations` block on the case file instead of stretching a value to cover it.

## What changed in v4

| v3 | v4 |
|---|---|
| 1.2 was a typology of *collision*, blank where no collision occurred | **Instability conditions**, worked through on every case. Jurisdictional clash recorded as jurisdictional *overlap*, which is a state rather than an event |
| `collision` named both a Module 1 value list and the Module 2 branch condition | Module 2's reactive value renamed **Dispute**, so the word now appears on one axis only |
| Nine numeric fields across 3.1 / 3.2 / 3.3 | **Three**, defined once in the template. Two moved to narrative, four dropped because they measured how much was reported rather than what happened |
| Enforcement appeared in both 3.1 and 3.2 | Consolidated in 3.2. Enforcement redistributes weight already in place; it does not introduce an order |
| Bearer assumed an identifiable actor | `bearer_type: firm` or `diffuse` |
| Every item carried a plain-language name and a technical name | One name each |
| BIS 2009→2026 sat alongside single incidents as a case | A **reference corpus**. Individual amendments are cut from it and registered as cases |
| Schema rejected unknown values and blank conditions | Both are flagged and recorded. Misfits go in `deviations` and are reviewed in batches |

The EU AI Act watermarking case forced most of this. It is an Enactment with no prior
state, so under v3 it would have carried an object type and nothing else, and the
definitional contest at its centre would never have been written down.

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

Modules 1 and 2 sit side by side as equal panels, with Module 3 running beneath both as a
band. The layout is doing work here: 1 and 2 are independent axes, and 3 is a different
kind of thing. A conventional docs sidebar would render all three as a nested tree and
quietly reassert the hierarchy the three-module structure removed.

Material kept for completeness but off the main reading path sits in `<details>`:
unexercised vocabulary, dropped fields, secondary caveats. Nothing is deleted for brevity,
only moved one click away.
