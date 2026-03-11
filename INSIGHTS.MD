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

## Unified nav: actual modules inside the journey

- The journey nav (`modules/ROOT/nav.adoc`) lists the **actual course module pages** from the nine source components via cross-component xref (e.g. `xref:rhoai3-storage::chapter1:section1.adoc[Storage — Architecture Deep Dive]`). Learners see one combined table of contents; clicking an entry opens the real page from that repo. Phase overview pages (phase1.adoc … phase5.adoc) are short intros with outcome, value, and checkpoint; they no longer duplicate links in tables.
