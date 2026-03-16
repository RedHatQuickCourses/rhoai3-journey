---
name: custom-journey-course
description: Build a customized RHOAI journey course from use case and audience by selecting which rhoai3-* and related modules to include. Use when the user provides a use case, audience, or business outcome and wants a tailored course from existing journey modules.
---

# Custom Journey Course

Build a customized course from the rhoai3-journey map by selecting modules that match the user's use case and audience. All source courses live as sibling repos in the same parent directory (e.g. `Documents/GitHub`) and are named `rhoai3-*` (plus `llmops-llmd` for distributed inference).

## When to use this skill

- User provides a **use case**, **audience**, or **business outcome** and wants a course tailored to it.
- User wants to **subset** the full journey (e.g. "foundation only" or "skip MaaS").
- User wants to **customize the course on the fly** for different audiences without maintaining separate repos.

**Not this skill:** Creating a net-new course from a course design document (use the `generate-course-structure` skill from course-starter-template instead).

## Workflow

### 1. Gather requirements

Ask or infer from context:

- **Use case** (e.g. "stand up model registry and catalog only", "full token factory including MaaS").
- **Audience** (e.g. platform engineers, app developers, security/compliance).
- **Outcome** (e.g. "get to first inference", "production MaaS with validation").

### 2. Map use case to phases and modules

Use the phase → module mapping. Include only phases/modules that support the use case.

| Phase | Focus | Repos (content sources) |
|-------|--------|-------------------------|
| 1 | Foundation (storage, registry, catalog) | rhoai3-storage, rhoai3-registry, rhoai3-catalog |
| 2 | Resource governance (profiles, GPU AaS) | rhoai3-hwprofiles, rhoai3-gpu-aas |
| 3 | Token production (deploy, vLLM, serving) | rhoai3-deploy |
| 4a | Distributed inference (llm-d) | llmops-llmd |
| 4b | MaaS | rhoai3-maas |
| 5 | Quality and SLOs (validation) | rhoai3-validate |

**Dependencies:** Phase 4b (MaaS) assumes 4a (llmops-llmd). Phase 5 (validate) assumes deploy. Include prerequisites when including a phase.

Full catalog (titles, component names, nav patterns): see [reference.md](reference.md).

### 3. Resolve repo path and component names

- **Repo directory:** All rhoai3-* (and llmops-llmd) are expected as sibling clones of rhoai3-journey (e.g. `../rhoai3-storage`).
- **Component names:** Most repos use component name = repo name. Two exceptions (must match antora.yml in each repo):
  - Repo `rhoai3-hwprofiles` → component **rhoai-hwprofiles**
  - Repo `rhoai3-gpu-aas` → component **rhoai-gpu-aas**

Playbook `content.sources` use **repo paths** (or git URLs). Shell pages use **component names** in includes (e.g. `include::rhoai-hwprofiles:chapter1:hwprofiles.adoc[]`).

### 4. Edit the playbook

File: `antora-playbook.yml`.

- Keep the first source: `- url: ./` (journey map and phase overviews).
- Under `content.sources`, keep only the selected repos. Remove any source not in the chosen set.
- **Local build:** Use sibling paths, e.g. `- url: ../rhoai3-storage`.
- **CI/GitHub Pages:** Use git URLs, e.g. `- url: https://github.com/RedHatQuickCourses/rhoai3-storage.git`.

Order: keep the same relative order (Phase 1 → 2 → 3 → 4a → 4b → 5) for sources you include.

### 5. Edit the navigation

File: `modules/ROOT/nav.adoc`.

- Keep: `* xref:index.adoc[Journey Map]`.
- For each **included** phase: keep the phase overview line (e.g. `** xref:phase1.adoc[Overview]`) and all nav entries for that phase's modules (the `**` and `***` items that point to shell pages like `p1-storage-index.adoc`, `p2-hw-placement.adoc`, etc.).
- **Remove** entire sections for excluded phases (overview + all module links). Do not leave orphan xrefs to shell pages for modules whose source was removed from the playbook.

Nav structure mirrors the full journey; only remove branches that correspond to excluded modules. Do not rename or reorder shell pages; they are already named by phase and module (p1-*, p2-*, p3-*, p4a-*, p4b-*, p5-*).

### 6. Verify and remind

- Run a build (e.g. `npx antora antora-playbook.yml` or project's npm script) to ensure no broken includes.
- Remind the user: if using local paths, all listed repos must be cloned as siblings; for CI, switch to git URLs as in the README.

## Adding a new module later

When a new rhoai3-* (or related) repo is added to the ecosystem:

1. Add it to `antora-playbook.yml` under `content.sources` in the appropriate phase order.
2. Create **shell pages** in `modules/ROOT/pages/` that include the new component's pages (one shell file per included page). Naming: follow existing pattern (e.g. `p2-newmodule-index.adoc`, `p2-newmodule-section1.adoc`).
3. Add nav entries in `modules/ROOT/nav.adoc` under the right phase, pointing to these shell pages.
4. Update this skill's reference.md catalog so future customizations can include the new module.

## Important notes

- **Shell pages:** Every nav link in the journey points to a shell page in this repo; each shell page uses `include::component:module:page.adoc[]`. The playbook must include the repo for that component so the include resolves at build time.
- **Subset only:** This skill customizes by **subsetting** existing modules and nav. It does not create new content or new repos; it edits playbook and nav only.
- **Idempotency:** Re-running with the same use case should produce the same playbook and nav; avoid adding duplicates or leaving stale entries.
