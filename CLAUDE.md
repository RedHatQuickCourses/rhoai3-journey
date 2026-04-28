# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Purpose

This is a **unified learning journey repository** that aggregates **10 separate Red Hat OpenShift AI (RHOAI) 3.x training courses** into one comprehensive learning path for deploying an Models as a Service **industrialized AI token generation platform** on Red Hat OpenShift AI 3.x.

**Focus areas:** Optimized resources, performance SLOs, model governance, and engineering outcomes.

**Key distinction:** This is NOT a standalone course. It's a **meta-course** or **journey map** that pulls content from 10 sibling repositories and combines them into one unified site.

## Unique Multi-Repository Architecture

Unlike typical Antora projects, this repository:

1. **Contains minimal content** - Only the journey map (ROOT module) with phase overview pages
2. **Aggregates external content** - Pulls in 10 complete courses via Antora playbook
3. **Requires sibling repos** - All 10 content repositories must be cloned as siblings for local builds
4. **Uses git URLs** - Playbook references GitHub URLs so CI/GitHub Pages can build the full site

## The 10 Content Sources

The unified journey combines these repositories organized by phase:

**Phase 0: Operator Ecosystem**
- `rhoai3-operators` - OpenShift operator installation and configuration

**Phase 1: Assembling the Factory (configure)**
- `rhoai3-storage` - Data storage and PVC configuration
- `rhoai3-registry` - Model registry setup and management
- `rhoai3-catalog` - Model catalog governance
- `rhoai3-hwprofiles` - Hardware profiles and node placement
- `rhoai3-gpu-aas` - GPU as a Service configuration

**Phase 2: Token Production Engine (serve)**
- `rhoai3-deploy` - Model serving deployment with KServe and vLLM

**Phase 3: Scaling the Utility (scale)**
- `rhoai3-llmd` - Distributed inference with llm-d
- `rhoai3-maas` - Models as a Service (MaaS) platform

**Phase 4: Quality and SLOs (validate)** *(currently disabled in navigation)*
- `rhoai3-validate` - Validation services and automated quality checks

## Required Directory Structure

For local builds, all repositories must be cloned as siblings:

```
parent/
├── rhoai3-journey/        ← you are here (journey map)
├── rhoai3-operators/      ← Phase 0
├── rhoai3-storage/        ← Phase 1
├── rhoai3-registry/       ← Phase 1
├── rhoai3-catalog/        ← Phase 1
├── rhoai3-hwprofiles/     ← Phase 1
├── rhoai3-gpu-aas/        ← Phase 1
├── rhoai3-deploy/         ← Phase 2
├── rhoai3-llmd/           ← Phase 3
├── rhoai3-maas/           ← Phase 3
└── rhoai3-validate/       ← Phase 4
```

## Build Commands

### Option 1: Docker (Recommended)

Run from the **parent directory** that contains all 11 repositories:

```bash
cd /path/to/parent
docker run -u $(id -u) -v $PWD:/workspace:Z --rm -t -w /workspace/rhoai3-journey antora/antora antora-playbook.yml
```

Output: `rhoai3-journey/build/site/index.html`

### Option 1: Local NPM (Recommended)

Must run from **inside** `rhoai3-journey` with all sibling repos present:

```bash
cd rhoai3-journey
npm install
npx antora antora-playbook.yml
```

Output: `build/site/index.html`

### Option 2: Docker (Recommended)

Run from the **parent directory** that contains all 11 repositories:

```bash
cd /path/to/parent
docker run -u $(id -u) -v $PWD:/workspace:Z --rm -t -w /workspace/rhoai3-journey antora/antora antora-playbook.yml
```

Output: `rhoai3-journey/build/site/index.html`

### Development Workflow

For local development with auto-rebuild:

```bash
# Terminal 1 - watch for changes
npm run watch:adoc

# Terminal 2 - serve the site
npm run serve
```

Site available at: http://localhost:8080

## Key Files

**Configuration:**
- `antora-playbook.yml` - Build configuration; lists all 10 content sources as git URLs
- `antora.yml` - Component metadata for the journey map (ROOT module only)
- `package.json` - Node.js dependencies and build scripts

**Journey Content (ROOT module):**
- `modules/ROOT/nav2.adoc` - Learner-oriented navigation (currently active)
- `modules/ROOT/nav.adoc` - Alternative navigation structure
- `modules/ROOT/pages/index.adoc` - Journey overview/landing page
- `modules/ROOT/pages/phase*.adoc` - Phase introduction pages
- `modules/ROOT/pages/p*-*.adoc` - Individual section pages that link to external content

**UI Customization:**
- `ui-bundle/` - Custom Antora UI bundle
- `supplemental-ui/` - UI overrides and customizations

## Working with the Playbook

**Git URLs for CI/GitHub Pages:**
The playbook uses git URLs (e.g., `https://github.com/RedHatQuickCourses/rhoai3-storage.git`) so that:
- GitHub Actions can clone and build all content
- Navigation xrefs resolve to actual pages, not fragment fallbacks
- The generated site includes all components

**Local paths for faster development:**
You can temporarily replace git URLs with local paths for faster local builds:

```yaml
# Instead of:
- url: https://github.com/RedHatQuickCourses/rhoai3-storage.git

# Use:
- url: ../rhoai3-storage
```

Revert before committing. Git URLs work locally too (Antora clones to cache).

## Navigation Structure

**Two navigation files:**
- `nav2.adoc` - **Currently active**, learner-oriented labels emphasizing outcomes
- `nav.adoc` - Alternative structure

To switch: Update `antora.yml` nav reference.

## Content Organization

**Journey map pages (this repo):**
- `index.adoc` - Overview of the unified journey
- `phase0.adoc`, `phase1.adoc`, `phase2.adoc`, `phase3.adoc` - Phase introductions
- `p0-*`, `p1-*`, `p2-*`, `p3-*`, `p4a-*`, `p4b-*`, `p5-*` - Section pages

**External content (10 repos):**
All actual course content lives in the 10 sibling repositories. This repo only provides the journey structure and phase organization.

## Build Notes

**Start page:**
- Configured as: `rhoai3-journey::index.adoc`
- Manual path: `build/site/rhoai3-journey/1/index.html`

**AsciiDoc errors:**
Errors in the 10 content repositories must be fixed in their respective repos, not here.

**Missing sibling repos:**
If any of the 10 content repos are missing, the build will fail or navigation links will not resolve.

## GitHub Pages Publishing

Pushes to `main` branch trigger `.github/workflows/main.yml` which:
1. Clones all 10 content repos (via git URLs in playbook)
2. Builds the unified Antora site
3. Publishes to GitHub Pages

Site URL: `https://<org>.github.io/rhoai3-journey/`

## Common Development Tasks

**Add a new phase or section:**
1. Create the page in `modules/ROOT/pages/`
2. Add xref to `modules/ROOT/nav2.adoc` in the appropriate phase
3. Build and verify navigation works

**Update content from a specific course:**
1. Navigate to the sibling repo (e.g., `cd ../rhoai3-storage`)
2. Make changes in that repo
3. Return to `rhoai3-journey` and rebuild to see changes

**Troubleshoot missing content:**
1. Verify all 10 sibling repos are cloned
2. Check `antora-playbook.yml` content sources are correct
3. Review build output for AsciiDoc errors
4. Verify xrefs use correct component names (e.g., `rhoai3-storage::index.adoc`)

## Important Notes

- **Never edit content from the 10 courses in this repo** - Changes must be made in their source repositories
- **Journey map only** - This repo provides the overview, navigation, and phase structure
- **Sibling dependencies** - Local builds require all 10 repos to be cloned as siblings
- **Git URLs for CI** - Keep git URLs in the playbook for GitHub Actions/Pages builds
- **Two nav files** - Check `antora.yml` to see which navigation file is active
