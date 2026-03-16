# Tasks — Industrialized AI Token Platform Journey

Tasks for the unified course repo `rhoai3-journey`. Mark complete with date and notes.

---

## 1. Define playbook and journey map

- [x] Create `antora-playbook.yml` with content sources for all nine repos (eight rhoai3-* + llmops-llmd). **2025-03-10** — Done. Local sibling paths used (`../rhoai3-catalog`, etc.).
- [x] Create journey component: `antora.yml`, `modules/ROOT/nav.adoc`, `modules/ROOT/pages/index.adoc` (Journey Map). **2025-03-10** — Done.
- [x] Course copied into org-template repo (rhoai3-journey); playbook updated to use `./ui-bundle` and `./supplemental-ui`. **2025-03-10** — Done.

---

## 2. Add Phase 1–5 (including 4a, 4b) modules and nav

- [x] Phase 1 (Foundation): `phase1.adoc` with outcome, value, xrefs to storage, registry, catalog. **2025-03-10** — Done.
- [x] Phase 2 (Resource Governance): `phase2.adoc` with xrefs to hwprofiles, gpu-aas. **2025-03-10** — Done.
- [x] Phase 3 (Token Generation): `phase3.adoc` with xrefs to rhoai3-deploy. **2025-03-10** — Done.
- [x] Phase 4a (Distributed Inference): `phase4a.adoc` with xrefs to llmops-llmd. **2025-03-10** — Done.
- [x] Phase 4b (Token Factory — MaaS): `phase4b.adoc` with xrefs to rhoai3-maas. **2025-03-10** — Done.
- [x] Phase 5 (Quality and SLOs): `phase5.adoc` with xrefs to rhoai3-validate. **2025-03-10** — Done.
- [x] ROOT nav lists Journey Map + Phase 1, 2, 3, 4a, 4b, 5. **2025-03-10** — Done.

---

## 3. Configure Antora content sources for all nine repos

- [x] Playbook lists: `./` (journey), rhoai3-storage, rhoai3-registry, rhoai3-catalog, rhoai3-hwprofiles, rhoai3-gpu-aas, rhoai3-deploy, llmops-llmd, rhoai3-maas, rhoai3-validate. **2025-03-10** — Done. Uses local paths; see README for switching to git URLs.

---

## 4. Add outcome checkpoints and optional assessments

- [x] Each phase page includes a "Checkpoint" section (engineering outcome). **2025-03-10** — Done.
- [ ] Optional: Add a short knowledge-check or quiz page in journey component. **Pending.**

---

## 5. Document build and consumption

- [x] README with build instructions (Docker and NPM), prerequisite (clone all repos as siblings), and note on replacing local URLs with git URLs for CI. **2025-03-10** — Done.

---

## 6. Cursor skill: custom-journey-course

- [x] Create Cursor skill to build a customized course from use case and audience using existing rhoai3-* modules. **2025-03-15** — Done. Skill at `.cursor/skills/custom-journey-course/` (SKILL.md + reference.md). Use when user provides use case/audience/outcome; edits playbook and nav to subset modules; supports adding new modules over time.
