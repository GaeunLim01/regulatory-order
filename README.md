# How Regulatory Order Reaches Actors — Framework v3

A three-module framework for tracing how regulatory order forms and reaches actors
across AI-related value chains: semiconductors, computing, cloud, data centers.

## Deploying

GitHub Pages builds this with its own Jekyll. No Actions workflow is required.

1. Push to `main`.
2. Settings → Pages → Source: **Deploy from a branch**, branch `main`, folder `/ (root)`.

Live at https://gaeunlim01.github.io/regulatory-order/

`baseurl` in `_config.yml` is set to `/regulatory-order` and must match the repository
name exactly. Renaming the repo without updating it serves the pages with no stylesheet.
Every internal link goes through `relative_url`, so nothing else needs changing.

## Layout

    _config.yml            site config
    _data/nav.yml          masthead navigation
    _data/schema.yml       controlled vocabulary + validation rules — single source of truth
    _data/cases/           one YAML file per case — nothing else lives here
    docs/case-template.yml blank case to copy into _data/cases/
    _layouts/              default (chrome) and module (guiding-question band)
    assets/css/main.css    design tokens and components
    index.html             overview — two axes, Module 3 band, independence grid
    module-*.html          the three modules
    method.html            tagging template, the two kinds of blank, constraints
    cases/                 placeholder, waiting on the case library
    changelog.html         what changed from v2 and why

## License

Split by intent, not by file extension:

| | |
|---|---|
| Framework content — structure, vocabularies, definitions, method, case library | CC BY 4.0 (`LICENSE-CONTENT`) |
| Site code — stylesheets, layouts, config, scripts | MIT (`LICENSE`) |

Cited source material (rules, gazettes, filings, industry comments) keeps its own
terms. `CITATION.cff` gives GitHub what it needs to render a "Cite this repository"
button.

## Adding a case

    cp docs/case-template.yml _data/cases/<slug>.yml

The template lives outside `_data/` on purpose. Jekyll loads every YAML file under
`_data/` recursively, so a template kept alongside the cases would be read as a case
and counted as one — a phantom entry that shows up only as a total that is off by one.

## Editing the framework

`_data/schema.yml` is authoritative for every enum value. When the framework changes,
change it there first — the module pages, the case files, and any future validator all
have to agree with it. Rules R1–R8 and non-rules N1–N2 in that file are written to be
read by a validator, but they document intent whether or not one is running.

## Design notes

Type is deliberately not coded to any jurisdiction. The framework compares regulatory
orders across national authorities, so setting it in any one government's civic typeface
would put a thumb on the scale. Body is Source Sans 3, chosen for neutrality and for
holding up at small sizes in dense tables; Hangul and CJK fall back to system faces so
entity names in case files render in a matched weight.

Modules 1 and 2 sit side by side as equal panels; Module 3 runs beneath both as a band.
This is not decoration — the framework holds that 1 and 2 are independent axes and that 3
is different in kind, applying whichever module produced an order. A conventional docs
sidebar would render all three as a nested tree and quietly reassert the hierarchy v3 removed.

Passages explaining what changed between versions carry a left margin rule, the device the
Federal Register and EU consolidated texts use to mark amended text.
