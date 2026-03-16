# Custom Journey Course — Reference

## Module catalog (repo → component → phase)

| Repo (playbook path / git URL) | Component name (antora.yml / includes) | Phase | Topic |
|--------------------------------|----------------------------------------|-------|--------|
| rhoai3-storage | rhoai3-storage | 1 | Storage, data connections |
| rhoai3-registry | rhoai3-registry | 1 | Model registry |
| rhoai3-catalog | rhoai3-catalog | 1 | Model catalog |
| rhoai3-hwprofiles | **rhoai-hwprofiles** | 2 | Hardware profiles, Kueue |
| rhoai3-gpu-aas | **rhoai-gpu-aas** | 2 | GPU as a Service |
| rhoai3-deploy | rhoai3-deploy | 3 | Deploy, vLLM, serving |
| llmops-llmd | llmops-llmd | 4a | Distributed inference (llm-d) |
| rhoai3-maas | rhoai3-maas | 4b | Model as a Service |
| rhoai3-validate | rhoai3-validate | 5 | Validation, SLOs |

Component names in **bold** differ from repo name; use them in shell `include::` directives.

## Playbook snippet (subset: Phase 1 only)

```yaml
content:
  sources:
  - url: ./
  - url: ../rhoai3-storage
  - url: ../rhoai3-registry
  - url: ../rhoai3-catalog
```

For CI, replace with git URLs (e.g. `https://github.com/RedHatQuickCourses/rhoai3-storage.git`).

## Nav snippet (subset: Phase 1 only)

Keep Journey Map and Phase 1 branch; remove Phase 2–5:

```asciidoc
* xref:index.adoc[Journey Map]

* 1: Assembling the Factory
** xref:phase1.adoc[Overview]
** xref:p1-storage-index.adoc[Storage — Home]
*** xref:p1-storage-section1.adoc[Storage — Architecture Deep Dive]
*** xref:p1-storage-section3.adoc[Storage — Data Connection Types]
*** xref:p1-storage-lab.adoc[Storage — Lab Exercises]
*** xref:p1-storage-section5.adoc[Storage — Field Notes]
** xref:p1-registry-home.adoc[Registry — Home]
*** xref:p1-registry-section1.adoc[Registry — Architecture]
*** xref:p1-registry-section2.adoc[Registry — QuickStart Lab]
*** xref:p1-registry-section3.adoc[Registry — Model Catalog]
** xref:p1-catalog-home.adoc[Catalog — Home]
*** xref:p1-catalog-section1.adoc[Catalog — Architecture Deep Dive]
*** xref:p1-catalog-section4.adoc[Catalog — Simulate the Experience]
*** xref:p1-catalog-section2.adoc[Catalog — Customization CLI]
*** xref:p1-catalog-section3.adoc[Catalog — Administration]
```

## Use-case → module suggestions

- **"Registry and catalog only"** → Phase 1: storage, registry, catalog (optionally storage only if they already have storage).
- **"First inference, no MaaS"** → Phases 1, 2, 3 (optionally 5 for validation).
- **"Full token factory with MaaS"** → All phases 1–5 (include llmops-llmd before rhoai3-maas).
- **"Resource governance only"** → Phase 2: rhoai3-hwprofiles, rhoai3-gpu-aas.
- **"Validation and SLOs"** → Phase 5; recommend including rhoai3-deploy (Phase 3) so validation content has context.

## Adding a new module (future)

1. Clone new repo as sibling; add to `antora-playbook.yml` in the correct phase order.
2. Read the repo's `antora.yml` for `name` (component) and its `modules/*/nav.adoc` to list pages.
3. In journey, create one shell page per included page under `modules/ROOT/pages/`, e.g. `p2-newmod-index.adoc` with content: `:navtitle: Title` and `include::component-name:module:page.adoc[]`.
4. Add nav entries in `modules/ROOT/nav.adoc` under the right phase.
5. Add the repo and component to this catalog in reference.md.
