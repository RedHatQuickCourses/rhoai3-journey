# Industrialized AI Token Platform — Unified Journey

Single learning journey that combines nine enablement modules into one course for deploying an **industrialized AI token generation platform** on Red Hat OpenShift AI 3.x. Focus: optimized resources, performance SLOs, model governance, and engineering outcomes.

This repository was created from the [course-starter-template](https://github.com/RedHatQuickCourses/course-starter-template). For first-time setup (clone, course-init, GitHub Pages), see [README-TRAINING.md](./README-TRAINING.md) or the template link above.

---

## Course content: the nine modules

**Repositories pulled in (content stays in those repos; this repo provides the playbook and journey map):**

- **Phase 1:** rhoai3-storage, rhoai3-registry, rhoai3-catalog  
- **Phase 2:** rhoai3-hwprofiles, rhoai3-gpu-aas  
- **Phase 3:** rhoai3-deploy  
- **Phase 4a:** llmops-llmd (distributed inference — required for MaaS)  
- **Phase 4b:** rhoai3-maas  
- **Phase 5:** rhoai3-validate  

---

## Prerequisites for building

- All nine content repos must be **cloned as siblings** of this repo (same parent directory). Example layout:

  ```
  parent/
  ├── rhoai3-journey/     ← you are here
  ├── rhoai3-storage/
  ├── rhoai3-registry/
  ├── rhoai3-catalog/
  ├── rhoai3-hwprofiles/
  ├── rhoai3-gpu-aas/
  ├── rhoai3-deploy/
  ├── llmops-llmd/
  ├── rhoai3-maas/
  └── rhoai3-validate/
  ```

- **Node.js** (for `npx antora`) or **Docker** (for `antora/antora` image).

---

## Build the site

### Option 1: Docker (recommended)

Run from the **parent** directory that contains `rhoai3-journey` and all nine content repos:

```bash
cd /path/to/parent
docker run -u $(id -u) -v $PWD:/workspace:Z --rm -t -w /workspace/rhoai3-journey antora/antora antora-playbook.yml
```

Then open `rhoai3-journey/build/site/index.html`.

### Option 2: Local NPM

```bash
cd rhoai3-journey
npm install
npx antora antora-playbook.yml
```

Then open `build/site/index.html`. Run from inside `rhoai3-journey` with the other repos as siblings.

---

## Why the nav links work (or don't)

The playbook uses **git URLs** for the nine content repos so that the **GitHub Pages build** (and any CI build) fetches and builds all of them. That way the generated site includes every component (e.g. `rhoai3-registry/1/chapter1/section3.html`), and the journey nav xrefs resolve to real pages instead of fragment fallbacks. If the playbook only had `url: ./`, only the journey pages would be built and nav links would change the URL to a `#...` fragment and not load the target page.

For **local** builds with sibling clones, you can temporarily point sources at local paths (e.g. `url: ../rhoai3-storage`) in the playbook to avoid cloning; the same playbook with git URLs also works locally (Antora will clone the repos into its cache).

---

## Repository structure (journey-specific)

- **antora-playbook.yml** — Build config; lists this repo plus nine content sources; uses template UI (`./ui-bundle`, `./supplemental-ui`).
- **antora.yml** — Journey component descriptor (ROOT module only for the journey map).
- **modules/ROOT/** — Journey Map (index.adoc) and Phase 1–5 pages (phase1.adoc … phase5.adoc, phase4a.adoc, phase4b.adoc).
- **TASKS.MD**, **INSIGHTS.MD** — Task log and insights for the unified journey.

Template files (e.g. LABENV, chapter1–3, appendix, images, `.github/workflows`) remain from the starter template; the built site is driven by the playbook and ROOT content above.

---

## Build notes

- **Start page:** The site is configured to open at the Journey Map (`rhoai3-journey::index.adoc`). If it is not found, open `build/site/rhoai3-journey/1/index.html` after a successful build.
- **Errors in other repos:** AsciiDoc errors (missing images, xrefs, doctype) in the upstream rhoai3-* and llmops-llmd repos must be fixed in those repositories.

---

## See also

- [README-TRAINING.md](./README-TRAINING.md) — Template and training repo setup.
- [Development using devspace](./DEVSPACE.md)
- [Guideline for editing content](./USAGEGUIDE.adoc)
