# Insights — Industrialized AI Token Platform Journey

Record of dependency order, design decisions, and discoveries while building the unified journey.

---

## Dependency order

- **Foundation:** storage → registry → catalog (data and model supply chain).
- **Resource governance:** hwprofiles → gpu-aas (profiles first, then GPU sharing strategies).
- **Serving:** deploy (single-model) → **llmops-llmd** (distributed inference) → maas (token factory).
- **Quality:** validate (assumes a deployed model; references rhoai3-deploy).

llm-d is required for MaaS: MaaS content assumes distributed inference concepts and the llm-d stack. Including llmops-llmd in the journey avoids teaching MaaS as a black box.

---

## Rationale for including llmops-llmd

- llmops-llmd is from the llmops series (not rhoai3-*). It is included because:
  - Distributed inference is **required** for MaaS at scale.
  - The course is new enough and explains Gateway, Scheduler, vLLM workers, request lifecycle, and well-lit paths.
  - The Arcade/walkthrough lab gives hands-on deployment.
- Placed as Phase 4a so learners see llm-d before Phase 4b (MaaS).

---

## rhoai3-validate Chapter 3

- Per rhoai3-validate/CONFIDENCE_ASSESSMENT.md, Chapter 3 (Deploying Validation Services) has lower confidence (40–50%) and is marked Advanced/Experimental.
- In the journey, Phase 5 links to Ch3 but frames it as optional / "Advanced/Experimental."

---

## Component names (for xrefs)

- rhoai3-journey, rhoai3-storage, rhoai3-registry, rhoai3-catalog, **rhoai-hwprofiles**, **rhoai-gpu-aas**, rhoai3-deploy, llmops-llmd, rhoai3-maas, rhoai3-validate.
- Note: hwprofiles and gpu-aas use `rhoai-` not `rhoai3-` in antora.yml.

---

## Build and Antora

- **Local content source:** Antora 3 requires local content sources to be git repositories. This repo (from the org template) is already a git repo.
- **UI:** This repo uses the organization template UI (`./ui-bundle/ui-bundle.zip`, `./supplemental-ui`) as configured in the playbook.
- **Start page:** `start_page: rhoai3-journey::index.adoc`. If the site index doesn’t redirect to the Journey Map, open the journey from the generated path (e.g. `rhoai3-journey/1/index.html`).
- **Upstream errors:** AsciiDoc errors (missing images, doctype, xrefs) in rhoai3-* and llmops-llmd are in those repos; the journey repo does not change upstream content.

---

## Repo structure

- This repo is based on the organization course-starter-template. The journey adds: playbook (with nine content sources), antora.yml (ROOT only for journey map), and `modules/ROOT/` (Journey Map + Phase 1–5 overview pages). Template modules (LABENV, chapter1–3, appendix) remain in the repo but are not included in the journey component nav; the playbook aggregates content from the nine external repos.

## Shell pages with include (nav links work on GitHub Pages)

- Nav links must stay **within** the journey component so the URL goes to a real page (e.g. `rhoai3-journey/1/p1-storage-index.html`). Cross-component xref in the nav was producing fragment-only URLs that didn’t load content.
- **Approach:** Each “link” in the combined course is a **shell page** in the journey repo (e.g. `p1-storage-index.adoc`) that contains only a navtitle and an **include** of the source page: `include::rhoai3-storage::chapter1:index.adoc[]`. The nav points to these shell pages (same component), so every click loads a journey page whose content is the included module page. Same pattern as registry’s ROOT index that does `include::chapter1:index.adoc[]`, but cross-component.
- Shell files are named by phase and module (p1-storage-*, p1-registry-*, p2-hw-*, p3-deploy-*, p4a-*, p4b-maas-*, p5-val-*). The playbook must still pull in all nine content sources so the include directive can resolve at build time.

---

## custom-journey-course skill

- Use-case-driven customization is done by **subsetting** content sources in `antora-playbook.yml` and the corresponding branches in `modules/ROOT/nav.adoc`; no new content is created. Two repos use a different Antora component name than repo name (rhoai3-hwprofiles → rhoai-hwprofiles, rhoai3-gpu-aas → rhoai-gpu-aas); the skill documents this so playbook and shell includes stay correct when customizing.
