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

## Using git URLs instead of local paths

For CI or when the content repos are not local siblings, replace the `content.sources` in `antora-playbook.yml` with git URLs (e.g. `https://github.com/YOUR_ORG/rhoai3-storage.git` with `branches: [main]`). See the playbook comments and adjust `YOUR_ORG` and branch/tag as needed.

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
