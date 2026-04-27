# RHOAI 3.x Journey Marketing Materials

This directory contains marketing and overview materials for the Red Hat OpenShift AI 3.x Journey—a unified learning path that transforms organizations from ad-hoc AI experimentation to industrialized GenAI platforms.

## Documents

### 1. Executive Brief (`executive-brief.html`)
**Target Audience:** C-level executives, VPs, Directors, Business decision-makers

**Purpose:** Strategic business case for transitioning from "Shadow AI" to platform-based AI infrastructure

**Key Messages:**
- The Shadow AI crisis and organizational risk
- Strategic shift from token consumer to token producer
- Measurable ROI (3-5x GPU utilization, 40-60% cost reduction, 10x faster deployment)
- Compliance and data sovereignty benefits
- Competitive differentiation through infrastructure mastery

**Use Cases:**
- Executive briefings and stakeholder presentations
- Budget justification for AI platform investments
- Strategic planning discussions
- Board presentations on AI strategy

---

### 2. Practitioner's Guide (`practitioners-guide.html`)
**Target Audience:** Platform engineers, ML engineers, DevOps/SRE teams, Technical architects

**Purpose:** Technical value proposition emphasizing accelerated learning and operational readiness

**Key Messages:**
- "Cookbook vs. Dictionary" learning approach
- 70-75% time reduction to production (30-50 hours vs. 120-200 hours)
- Hands-on, outcome-focused learning path
- Real-world skills development (GPU ops, model governance, inference optimization)
- Production-ready architecture patterns

**Use Cases:**
- Technical team onboarding
- Training program justification
- Engineering enablement initiatives
- Community evangelism at technical conferences

---

### 3. Journey Infographic (`journey-infographic.html`)
**Target Audience:** All stakeholders  
**Format:** Single-page visual designed for printing/PDF export

**Purpose:** Quick-reference visual guide showing the complete journey at a glance

**Key Features:**
- Problem/Solution side-by-side comparison
- 4 key ROI statistics (3-5x GPU, 40-60% cost reduction, 10x faster, 70-75% time savings)
- Visual timeline of all 4 phases with time estimates
- 6 value propositions explaining "Why This Approach Works"
- Call-to-action section with summary metrics

**Use Cases:**
- Leave-behind handout for presentations
- Email attachment for quick overview
- Social media sharing (screenshot or PDF)
- Conference booth/poster printing
- Internal marketing campaigns
- First slide of presentation decks

**How to Save as PDF:**
```bash
# Open in browser, then:
# File → Print → Save as PDF (fits on one letter-size page)
```

---

### 4. Condensed Overview (`condensed-overview.html`)
**Target Audience:** All stakeholders  
**Format:** Two-page printable document combining executive and technical messaging

**Purpose:** Comprehensive but compact reference guide suitable for printing and distribution

**Content:**
- **Page 1:** Problem/solution comparison, ROI stats grid, all 4 phases with outcomes, before/after transformation table
- **Page 2:** Cookbook method explanation, what you get in each module, skills matrix, strategic imperatives, audience breakdown, time investment comparison

**Use Cases:**
- Print handouts for workshops and training sessions
- PDF distribution via email
- Attachment for proposal documents
- Quick reference guide for sales/marketing teams
- Conference packet inserts
- Internal executive briefings

**How to Save as PDF:**
```bash
# Open in browser, then:
# File → Print → Save as PDF (2 pages, letter size, portrait)
```

---

### 5. Audio Narrative Script (`audio-narrative-script.md`)
**Target Audience:** All stakeholders  
**Format:** Podcast-style conversation script (8-10 minutes)

**Purpose:** Engaging audio/video content that explains the journey through realistic workplace dialogue

**Content:**
- Conversation between Alex (curious co-worker) and Jordan (journey narrator)
- Covers Shadow AI problem, cookbook approach, all 4 phases, real-world challenges
- Professional tone with AI humor and authentic dialogue
- Addresses real objections and hard parts honestly
- Strong call to action referencing the learner guide for contribution

**Use Cases:**
- Record as podcast episode for internal distribution
- Video content for training kickoff sessions
- Voiceover script for animated explainer videos
- Team meeting presentation with dramatic reading
- YouTube/LinkedIn video content
- Internal communication campaigns
- Sales enablement audio content

**Production Notes:**
- Designed for two-voice recording (or single narrator doing both parts)
- Natural conversational pacing, approximately 8-10 minutes runtime
- Includes detailed production guidance for tone, pacing, and key beats to emphasize
- Can be adapted for video with screen recordings of the journey
- Works well with subtle background music

**To Record:**
- Use two voice actors if possible (makes conversation feel authentic)
- Allow natural overlaps and interruptions
- Don't over-produce—keep it conversational
- Consider using for video walkthroughs with the condensed overview on screen

---

## How to Use These Materials

### Viewing the Documents
Open the HTML files directly in any web browser. They are self-contained with embedded CSS styling.

```bash
# macOS
open executive-brief.html
open practitioners-guide.html
open journey-infographic.html
open condensed-overview.html

# Linux
xdg-open executive-brief.html
xdg-open journey-infographic.html

# Windows
start executive-brief.html
start journey-infographic.html
```

### Converting to PDF

The infographic and condensed overview are specifically designed for PDF export:

**Using Browser Print Function:**
1. Open the HTML file in Chrome, Firefox, Safari, or Edge
2. File → Print (or Cmd+P / Ctrl+P)
3. Select "Save as PDF" as the printer
4. Settings:
   - Paper size: Letter (8.5 x 11 inches)
   - Orientation: Portrait
   - Margins: Default
   - Scale: 100%
5. Save the PDF

**Recommended for:**
- `journey-infographic.html` → Perfect for one-page handouts
- `condensed-overview.html` → Two-page reference guide

### Distribution Options

1. **Direct Sharing**
   - Email the HTML files or PDF exports as attachments
   - Upload to internal knowledge bases or SharePoint
   - Print to PDF for formal presentations
   - Print physical copies for workshops/conferences

2. **Web Publishing**
   - Host on internal web servers
   - Include in documentation sites
   - Link from course registration pages
   - Embed in learning management systems (LMS)

3. **Presentation Integration**
   - Extract key statistics and talking points
   - Use content as basis for slide decks
   - Reference in webinar/workshop descriptions
   - Screenshot the infographic for slide backgrounds

### Customization

The HTML files use inline CSS for easy customization:
- Modify colors to match corporate branding
- Update statistics with organization-specific data
- Add logos or branded headers
- Translate to other languages

Key branding colors used:
- Primary Red: `#cc0000` (Red Hat brand color)
- Primary Blue: `#004153` (dark teal)
- Accent Blue: `#0066cc`
- Success Green: `#28a745`

---

## Key Statistics Referenced

These metrics can be cited when promoting the journey:

**Time Savings:**
- 70-75% reduction in time-to-production
- 30-50 hours (journey) vs. 120-200 hours (learning from scratch)
- Weeks to days for new AI capability deployment

**ROI Metrics:**
- 3-5x increase in GPU utilization
- 40-60% reduction in AI infrastructure costs
- 10x faster time-to-production for new capabilities
- 70-90% reduction in external API spend

**Technical Outcomes:**
- GPU utilization: 70-85% (vs. 20-30% before)
- Complete audit trail for compliance
- Self-service model deployment in minutes (vs. weeks)

---

## Messaging Framework

### The Problem (Shadow AI)
Organizations are already using GenAI, but in unmanaged ways that create:
- Unpredictable costs from external APIs
- Security and compliance risks
- Wasted GPU resources (60-80% idle time)
- Fragmented, non-scalable solutions

### The Solution (RHOAI 3.x Journey)
A structured path to industrialized AI infrastructure that:
- Converts from token consumer to token producer
- Maximizes GPU ROI through sharing and optimization
- Implements governance and compliance frameworks
- Delivers predictable costs and enterprise scale

### The Differentiator (Cookbook Approach)
Unlike traditional training that teaches theory first:
- Deploy working infrastructure in hours
- Learn business value from running systems
- Optimize based on actual metrics
- Build expertise through hands-on iteration

### The Outcome (Strategic Asset)
Organizations gain:
- Data sovereignty and compliance
- Cost predictability and control
- Competitive advantage through faster iteration
- Foundation for autonomous AI systems

---

## Additional Materials to Consider

Future additions to this marketing directory could include:

1. **Email Campaign Templates**
   - Series of 4-5 nurture emails
   - Different tracks for executives vs. practitioners
   - Call-to-action for course registration

2. **Social Media Assets**
   - LinkedIn post templates
   - Twitter/X thread structure
   - Technical blog post outlines

3. **Video Production**
   - Record audio narrative script as actual podcast/video
   - Animated explainer based on infographic
   - Screen recording walkthrough of the journey
   - Customer testimonial interview guide

4. **FAQ Document**
   - Common objections and responses
   - Technical prerequisites clarification
   - ROI calculation methodology

---

## Contact and Feedback

For questions about these marketing materials or suggestions for improvements, contact the RHOAI training content team.

**Content Version:** 1.0  
**Last Updated:** April 2026  
**RHOAI Version Covered:** 3.x (specifically tested with 3.3+)
