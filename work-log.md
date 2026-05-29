# Tramm Help Site — Work Log

---

## 2026-05-27 (Wednesday)

- Completed `tramm/planner/quick-reference.html` layout fix (HTML updates carried over from previous session):
  - Added `<div class="header-inner">` wrapper around header content
  - Replaced `<p class="eyebrow">` with breadcrumb: OPSI Docs › Tramm › Planner Button Reference
  - Wrapped legend items in `<div class="legend-inner">` — page now matches two-column layout of all other pages
- Improved Attribute Rules example in `tramm/data-manager/vehicle-classes.html`:
  - Replaced slash-separated prose (`Entity Type = product / Attribute Name = ...`) with a compact labeled pill block (field labels + `.av` code pills in a styled `.av-example` container)
  - Rewrote "Conversely" note as two clearly labelled sentences: "What this does:" and "If you leave Attribute Rules empty:" — easier for brand new users to follow
- Built FleetVision Colours & Statuses quick-reference page (`fleet-vision/quick-reference.html`):
  - Sections: Colour Palette (9 swatches with hex codes), Trip Lifecycle (12 statuses, ID 0–120), Trip Display Status (10 calculated labels with callout explaining the distinction), Stop Statuses (6 outcomes with map circle colours), Vehicle Statuses (5 states with icon colours), Delivery Statuses (6 reporting outcomes)
  - All colours and status descriptions verified against `C:\Repos\fleetVision\enumsandglobalvariables.R` and `datasources.R`
  - Sticky sidebar with scroll-spy active link highlighting
- Restructured FleetVision out of Tramm — it is a separate product:
  - Moved `tramm/fleet-vision/` → `fleet-vision/` at site root level (same level as `tramm/`, `whats-new/`)
  - Breadcrumb updated: OPSI Docs › FleetVision Colours & Statuses (Tramm link removed)
  - Built `fleet-vision/index.html` landing page — Quick Reference section (Colours & Statuses card) + Understanding FleetVision section (4 x Coming Soon cards: Live Map, Alerts & Escalations, Trip Monitoring, Analysis & Reports)
  - Home page (`index.html`): activated FleetVision product card (was greyed-out "Coming soon" div, now live `<a>` link to `fleet-vision/index.html`); added FleetVision QRC card to Quick Reference section
- What's New download URLs (task #9) — deferred pending IT/product team decision:
  - SharePoint (`opsi977.sharepoint.com/sites/TrammReleases`) is internal-only; clients cannot access it
  - Recommended options: GitHub Releases (public, stable URLs) or Azure Blob Storage (public container)
  - All download buttons remain `href="#"` placeholders with `⚠ URL pending` label until hosting is confirmed
- Fixed Routing Classes SOP step numbering in both `tramm-help/sops/routing-classes.html` and `SOPs/Route Classes/routing-classes-sop.html`:
  - Root cause: CSS `counter-reset: step` on every `<ol class="steps">` overrides HTML `start` attribute — CSS counters and HTML list numbering are independent
  - Fix: added `style="counter-reset: step N-1;"` inline on each continuation list (Sections 5, 6, 8, 9)
  - Export section: removed single-item `<ol>` wrapper, replaced with plain paragraph — single steps don't need a numbered list
- Added slide 14b (Portable File) to standup presentation (`Documents/Claude/Standup Presentation/presentation.html`):
  - Before/after layout showing standard version (HTML + img/ folder) vs portable version (single self-contained file)
  - Explains the `generate-portable.ps1` script: right-click → Run with PowerShell → done in seconds
  - Inserted between "What's Next" (s14) and "Big Reveal" (s15); slide uses `bg-violet` theme
- Built `tramm/data-manager/trailers.html` — new full documentation page:
  - Sections: intro panels + amber setup-order callout (must set up before Vehicle Classes), What is a Trailer, Trailer Fields (field matrix with Required/Optional badges), Compartments vs Capacity, Attribute Rules (entity type pills, operator pills, worked example), Adding a Trailer (10-step task list), Tips & Common Mistakes (3 tips, 3 mistakes)
  - Bottom nav: ← Data Manager | Vehicle Classes & Vehicles → | OPSI Docs home
  - Verified against codebase: Trailers are passive assets towed by Horse-type vehicles; compartments and simple capacity are mutually exclusive; double-counting capacity warning
- Updated `tramm/data-manager/getting-started.html`:
  - Setup flow expanded from 5 → 6 steps: Trailers added as optional step 2 (dashed blue style)
  - All subsequent step numbers incremented accordingly
  - 3D Visualiser note updated with corrected step numbers and Trailers mention
  - Trailers card added to "Where to Go from Here" section
- Updated `tramm/data-manager/index.html`: added Trailers card to Required Setup section (between Settings and Vehicle Classes)
- Updated `whats-new/index.html`: added `header-inner` wrapper to align header text with page content width
- Updated `whats-new/release-1174.html`: fixed breadcrumb root label "Tramm Help" → "OPSI Docs"
- Full layout audit and alignment pass across all 22 HTML pages:
  - Ran PowerShell audit checking every page for: header-inner wrapper, breadcrumb, back-to-top button, bottom nav, OPSI Docs branding
  - 8 pages had issues; all 8 were fixed:
    - `tramm/data-manager/settings.html` — added back-to-top + bottom nav (with forward link to Vehicle Classes)
    - `chorafeatures.html` — fixed breadcrumb "Tramm Help" → "OPSI Docs"; added back-to-top + bottom nav; fixed footer text
    - `fleet-vision/quick-reference.html` — added bottom nav
    - `how-tramm-works/index.html` — fixed body background; added header-inner CSS + wrapper; breadcrumb root updated; added back-to-top + bottom nav; fixed footer
    - `how-tramm-works/key-concepts.html` — fixed body background; added header-inner CSS + wrapper; breadcrumb root updated; added back-to-top + bottom nav; fixed footer
    - `overview.html` — fixed body background; added header-inner CSS + wrapper; breadcrumb root updated; added back-to-top + bottom nav; fixed footer
  - Remaining exceptions (intentional, not fixed):
    - `index.html` (home page) — hero design, no breadcrumb needed as root page ✓
    - `sops/routing-classes.html` — SOP template with different CSS class names but full navigation present ✓
    - `vimeo-test.html` — scratch/test file, not a documentation page ✓
  - Post-fix audit confirms 20/22 documentation pages fully aligned

---

## 2026-05-28 (Thursday) — standup presentation final session (evening)

All changes to `Documents\Claude\Standup Presentation\presentation.html` and `script.html`:

- **Script slides 3, 6, 8, 9, 10**: updated from Nina's txt files — exact wording, phrasing and cues corrected throughout
- **Slide 9 script**: restructured — bullets point directly at the three on-screen items; adds behaviour change story (hesitant → jumped straight in); closes with "If I can do it, anybody can."
- **Slide 10 script**: encyclopedia/disclaimer story moved here as setup for the Before & After visual; PowerShell punchline broken into three beats
- **Slide 13 script (Portable SOP)**: rewritten in plain language — "we email you one file, you double-click, read, print"; no technical jargon
- **Timeline slides 11 & 12**: stripped descriptive sentences from all 6 entries — bold cue text only; `.vtl-item` spacing increased from 26px → 52px; bold text size increased
- **Timeline entries revised**: honest/factual language throughout — no "launched", "live", "rebuilt", "rebranded"; entries describe what information was added
- **14–18 May entry added** to slide 11: FleetVision training documentation for client training
- **27–28 May entry corrected**: changed from "FleetVision live. Toolbar made interactive." to "Routing Classes SOP." — FleetVision still needs QA
- **Stats slide**: 91 → 99 commits; 15+ → 22 pages
- **What's Next slide**: removed marketing language; split Tramm into two cards (Planner and Transact); added Plato → Tramm transition card (preparation checklists, FAQs, change management guide); now 8 cards
- **Slide 11 script**: added audience/purpose intro (implementers, end users, whole Opsi team) before timeline walkthrough; timeline entries reformatted as date headers + bullet points
- **Slide 12 script**: timeline entries reformatted as date headers + bullet points; updated to match revised slide content
- **What's Next script**: rewritten — factual, no hype; Plato → Tramm card explained as change management guide for clients
- **Demo plan added** to bottom of script: 3-stop, 60-second demo plan (Homepage → Toolbar reference hover demo → Data Manager page)
- **Key Concepts page** (`how-tramm-works/key-concepts.html`): fixed wide layout — `.header-inner` max-width 1400px → 1060px; added `max-width: 1060px; margin: 0 auto` to `.page-layout`

---

## 2026-05-28 (Thursday) — standup presentation polish session

All changes to `Documents\Claude\Standup Presentation\presentation.html` and `script.html`:

- **s6 (Punchline)**: removed "I am watching all of you." from slide HTML; added it to `script.html` slide 6 as a spoken line before the final cue
- **s8 (Proposal) photo**: enlarged photo slot from 300×320 to 420×520; changed `object-fit` from `cover` to `contain` so full photo (face + laptop) is visible; removed dashed border frame
- **bg-orange**: changed from dark brownish gradient to vibrant orange — gradient now peaks at `#cc3800` to match Nina's sleeve colour in the photo
- **bg-split (Before/After)**: replaced flat `#282828` left side with a warm dark charcoal gradient (`#0f0e0c → #231f1a`) giving the left column the same depth as the navy right side
- **Universal rainbow stripes**: added `.slide::before` and `.slide::after` CSS pseudo-elements so every slide gets a rainbow top and bottom border; existing custom-coloured `.stripe` divs (green on s-green, violet on s9/s14b) paint on top and override automatically — no HTML changes needed
- **s14 (What's Next)**: redesigned all 6 cards — row 1 now shows the three products with real scope (Tramm: 24 apps, 5 modules, full app list; FleetVision: 7 apps with names; Tramm Mobile: 5 apps with names; row 2: SOPs, Articulate 360, "Every release documented"); updated `script.html` slide 16 to match
- **s15 (Big Reveal)**: changed "about two hours" → "about four hours" on slide and in script
- **s1 (Opening)**: replaced plain text heading with animated Facebook relationship status card — card slides in, "Single" gets a strikethrough drawn across it, arrow fades in, "Engaged 💍" pops in with spring bounce; updated `script.html` slide 1 cue accordingly

---

## 2026-05-28 (Thursday) — toolbar reference & GitHub setup

- Updated QRC card label on home page: "System-wide" → "Tramm" to match Planner and FleetVision card labels
- Added amber "In progress — individual Planner button screenshots to be added" banner to `tramm/toolbar-reference.html`
- Rebuilt standard toolbar section with full interactive toolbar map:
  - Replaced static `toolbar-context.png` with interactive `toolbar-data-manager.png` strip (333×41px, 8 buttons)
  - Hotspot divs at 12.5% intervals — hover shows tooltip label, click scrolls to and flash-highlights the corresponding table row
  - Added two missing standard buttons: **Set Security Groups** (padlock icon) and **Activate / Deactivate** (power icon)
  - All 8 buttons now have individual icon screenshots: `btn-add`, `btn-duplicate`, `btn-edit`, `btn-security`, `btn-toggle`, `btn-delete`, `btn-import`, `btn-export`
  - Added `id` attributes to all standard table rows for JS scroll targeting
- Added Planner toolbar strip screenshots above Gantt, Jobs, and Trips subsection tables
- Created `tramm/img/` image folder with 13 screenshots (button icons + toolbar strips)
- Set up proper git workflow — no more web uploads:
  - Cloned `OpsiSystems/tramm-help` to `Documents\GitHub\tramm-help`
  - Diagnosed root cause of failed img folder upload: GitHub web had created `tramm/img` as a FILE not a folder (from a malformed "Create img" web commit)
  - Removed malformed file, added real `tramm/img/` folder, committed and pushed 34 files in one clean commit
  - Removed stale root `planner/` folder from GitHub (content had moved to `tramm/planner/` weeks ago)
- Created `Documents\Claude\Scripts\` folder for site-wide PowerShell scripts:
  - `publish-tramm-help-to-github.ps1` — syncs SharePoint → git clone → commits → pushes; right-click → Run with PowerShell
  - Rule established: SOP-specific scripts (like `generate-portable.ps1`) stay next to their SOP; site-wide scripts go in `Scripts\`

---

## 2026-05-27 (Wednesday) — evening session

- Standup presentation — large batch of revisions to `Documents\Claude\Standup Presentation\presentation.html` and `script.html`:
  - **Global font sizes increased** for auditorium visibility: `.t-body`, `.t-small`, `.t-label`, `.ba-item`, `.vtl-content`, `.vtl-date`, `.stat-num`, `.stat-lbl`, `.next-item`, `.gf-line`, `.tag`, `.w-label`, `.ba-col-label`, `.tc-chip` all increased
  - **Before/After slide (s10)**: brightened "before" column from 28% to 72% opacity; lightened left background from #111 to #282828; rewrote 3 before items (documentation history, screenshots caveat, Nicole-at-21:00 message)
  - **About Nina slide (s9)**: fixed label overflow — moved label inside content div so it no longer floats to top edge of screen; reduced margins to prevent overflow
  - **Timeline Part 1 (s11)**: removed "nobody had ever documented"; removed "Repo moved to Opsi org on GitHub"; simplified 13 May entry to What's New only (Chora page removed)
  - **Timeline Part 2 (s12)**: expanded 20–21 May entry with more detail; removed "Not just Tramm — all three products" phrase; tightened 25 May wording
  - **Portable SOP slide (s14b)**: completely redesigned — removed technical file/folder diagrams and PowerShell reference; replaced with 4 icon cards (Email / Teams / Print / Save offline); moved to position 14 (between Timeline Part 2 and Stats)
  - **What's Next slide (s14)**: changed colour scheme from green to teal (`bg-ocean`); redesigned from plain list to 3×2 card grid; FleetVision and Tramm Mobile shown at equal priority
  - **Big Reveal (s15)**: changed from `bg-gold` (brown) to `bg-vivid-rainbow`; "Is not a PowerPoint" now uses `rainbow-text`; rainbow stripes top and bottom
  - **End slide (s16)**: changed from `bg-black` to `bg-vivid-rainbow`; removed gold colour; rainbow stripes added
  - Added two new CSS classes: `.bg-ocean` (teal), `.bg-vivid-rainbow` (dark rainbow)
  - Added `.next-grid` / `.next-card` CSS for the card layout
- Updated `script.html` to match: renumbered slides 7–18, fixed Chora and "nobody had documented" references, updated Green Flags cue to reflect click-controlled fly-in, added Portable SOP script block (slide 14), updated stats/next/reveal/end script blocks, added live site showing cue on slide 13

---

## 2026-05-26 (Tuesday) — evening session

- Built standup presentation for Friday: `Documents\Claude\Standup Presentation\presentation.html`
  - 17-slide HTML presentation with full keyboard/click navigation and rainbow colour scheme
  - Theme: "I Am Not Single Anymore — Engaged to Claude"
  - Slides: dramatic opening → Red Flags (quirky thinking words by category) → Green Flags (fearful-avoidant perspective) → Claude intro → The Proposal → Attachment Theory → Before/After → Timeline → Stats (91 commits) → What's Next → Big Reveal (it's HTML, not PowerPoint)
  - Photo placeholder on slide 8 — auto-loads `nina-photo.jpg` when dropped in the folder
- Created speaker script: `Documents\Claude\Standup Presentation\script.html`
  - Speaker notes for all 17 slides — what to say, what not to say, action cues
  - Readable on phone or second screen during presentation
  - Includes reminder to update commit count before Friday

## 2026-05-26 (Tuesday) — morning/afternoon session

- Fixed layout of `tramm/index.html`: hub sections (User Guides, Quick Reference, Understanding Tramm) had their own inner `max-width: 960px; margin: 0 auto` inside the already-centred page container, making them narrower than the Browse section — removed the inner constraint so all sections fill the same width
- Added subsection heading style to `tramm/toolbar-reference.html`: `.subsection-label` changed from small grey text (visually identical to table column headers) to blue-tinted style with left accent bar — creates clear visual hierarchy: section → subsection → table columns
- Added site-wide bottom navigation bar and "↑ Top" back-to-top button to all content pages:
  - Each page has a "← Back to [parent]" link on the left and "OPSI Docs home" shortcut on the right
  - "↑ Top" fixed button appears in bottom-right corner after scrolling 400px
  - Applied to: tramm/index.html, tramm/toolbar-reference.html, tramm/planner/quick-reference.html, tramm/data-manager/index.html, tramm/data-manager/getting-started.html, tramm/data-manager/vehicle-classes.html, tramm/data-manager/sites.html, tramm/data-manager/products.html, sops/index.html, sops/routing-classes.html, whats-new/index.html, whats-new/release-1174.html
- Restructured front page (`index.html`) and fixed broken links after Planner folder move:
  - Moved `planner/quick-reference.html` → `tramm/planner/quick-reference.html`; deleted old `planner/` folder
  - Fixed 4 broken links caused by the move: 2 in `tramm/planner/quick-reference.html` (toolbar-reference path), 1 in `tramm/index.html`, 1 in `tramm/toolbar-reference.html`
  - Added Quick Reference section to front page (orange accent cards): "What the Buttons in Tramm Do" and "Planner Button Reference"
  - Simplified SOPs section on front page to a single "Browse all SOPs & Procedures →" card (removed individual Routing Classes shortcut — browse page is the right entry point)
- Built SOPs section in the learning portal (top-level, ready for all products):
  - `sops/index.html` — hub page with filter, purple accent, grouped by area; Routing Classes card live
  - `sops/routing-classes.html` — SOP adapted for portal: breadcrumb nav, relative image paths from `sops/img/`, portal dark footer; all 12 screenshots copied with clean filenames
  - `index.html` — added SOPs & Procedures section (purple accent cards) with direct Routing Classes link and "Browse all SOPs" card
- Added sticky sidebar navigation to Routing Classes SOP — TOC moves to permanent left column, active section highlights as you scroll, collapses to inline block on mobile, hidden in print; portable version regenerated (1.3 MB)
- Saved `generate-portable.ps1` to `Documents\Claude\Tramm\` — right-click → Run with PowerShell to regenerate the portable HTML after any source changes
- Created portable and print-ready versions of Routing Classes SOP:
  - Added `@media print` CSS to source file — white background, colour-safe headers, no page breaks mid-step/callout/screenshot, screenshots capped at 72% width
  - Generated `routing-classes-sop-portable.html` (1.3 MB) with all 12 screenshots Base64-embedded — single self-contained file, no external dependencies, safe to email or share via Teams
- Second round of screenshot-driven corrections to Routing Classes SOP:
  - Section 6 (Edit): corrected — use edit icon in Actions column, form title is "Update [name]", button is "Update" not "Save"; added 2 screenshots
  - Section 7 (Delete): corrected — red bin icon directly on each row in Actions column (not via three-dot menu); added screenshot
  - Section 8 (Assign to Vehicle Class): full rewrite — path is waffle icon → Data Manager → Vehicle Classes → Edit icon → Specification → Routing Class tab → Commit; added 4 screenshots
  - Section 9 (Import/Export): added three-dot menu screenshot; clarified menu options are History, Import, Export
  - Footer: removed "Internal" — now reads "Tramm Platform — Implementation Documentation — May 2026"
- First round of screenshot-driven corrections to Routing Classes SOP (`Documents\Claude\Tramm\routing-classes-sop.html`):
  - Fixed CSS bug: `.steps li strong { display: block }` was making all inline bold text render as block elements (broken sentences, stranded full stops) — narrowed selector to `.steps li .step-body > strong:first-child`
  - Simplified Speed & Duration table Default column: "0 (no cap)" → "0", "0 (no limit)" → "0", "Hours + Minutes" → "h / min" to prevent column wrapping
- Created Routing Classes SOP (`Documents\Claude\Tramm\routing-classes-sop.html`) from code research
  - Researched `C:\Repos\Tramm` — routing-classes component, model, validator, TripCalculationService, travel-routing architecture
  - SOP covers: what a Routing Class is, navigation path, create/edit/delete procedures, full field reference, Vehicle Class assignment, import/export column spec, how the routing engine uses the class, configuration tips
  - Prompted by implementer query from client asking how to use and apply Routing Classes

---

## 2026-05-25 (Monday)

- Built Data Manager deep documentation sub-pages:
  - `data-manager/getting-started.html` — Classes/Groups concept, setup sequence flow, 3D Visualiser note, "Where to Next" cards
  - `data-manager/vehicle-classes.html` — full guide: concept, field matrices, override flow diagram, task guides, tips
  - `data-manager/sites.html` — full guide: SiteClass/Site fields, override logic, task guides, tips
  - `data-manager/products.html` — full guide: ProductGroup/Product fields, multi-group concept, task guides, tips
  - `data-manager/index.html` — redesigned as compact nav hub (Required / Optional / Advanced card groups, "Start here" banner)
- Visual overhaul across all Data Manager pages:
  - Section headings: left blue accent bar, larger/darker text (replaces tiny grey underline style)
  - Field tables → scannable matrix format (Field / Description / Req / Opt / Override columns, colour-coded row borders)
  - Removed inheritance diagram (too complex); replaced with "specification sheet" analogy paragraphs tailored per entity
  - Setup sequence redesigned: equal-size boxes, dashed-outline step 5, visible connectors, 3D Visualiser callout below flow; steps 2/3/4 are clickable links
  - Screenshot placeholders removed (to be added back once content is stable)
- Content corrections verified against code:
  - EVehicleType: only Rigid and Horse (removed incorrect "Articulated, Motorcycle" examples)
  - Home Site: confirmed used as both start AND end location (code: StartLocationId = EndLocationId = HomeSiteRef)
  - Routing Class: user-defined config names, not fixed enum values
  - Products: belong to multiple Groups (not a single Class); ProductGroup provides rules, Product provides physical specs
- Text fixes: "Products work slightly differently" → "Products take this one step further"; Overrides section updated to mention "Class or Group" for Products
- Rewrote "Adding a Site Class" task guide (sites.html) to match actual form tab structure:
  - Basic Info → Specification (Entry/Exit Duration, Attributes) → Operating Hours → Attribute Rules → Commit
- Rewrote "Adding a Site" task guide (sites.html) — 15 steps covering all Specification sub-sections:
  - Links (Site Class + Client), Type, Instructions, Location (Auto Allocate To Region + Location Ref), Region Allocation, Linked Vehicle Classes, Durations, Loading Rate, Attributes → Operating Hours → Contact Info → Attribute Rules → Commit
- Added "Linked Vehicle Classes" field to the Site fields matrix in sites.html
- Rewrote "Adding a ProductGroup" task guide (products.html) — 5 steps: Basic Info → Specification (Icon + Attributes + Variance Tolerance note) → Attribute Rules → Commit
- Rewrote "Adding a Product" task guide (products.html) — 7 steps: Basic Info → Specification/Links → Size (Dimension/ValueType/Value table with + button) → Loading Rate (Dimension Name dropdown + seconds) → Stackability (Stacking Disabled checkbox) → Commit
- Added "Icon" field to ProductGroup fields matrix in products.html
- All task guides now match actual form screenshots (tab names, field names, button label "Commit" throughout)

---

## 2026-05-21 (Thursday)

- Restructured toolbar-reference.html into full "What the Buttons in Tramm Do" page:
  - Removed Admin Edit (admin-only, not for standard users)
  - Added full Planner-specific buttons (Gantt controls, Orders, Jobs, Trips, Trip Builder)
  - Two-column layout with sticky left nav and anchor links per section
- Cleaned up planner/quick-reference.html:
  - Removed standard button cards (Add, Edit, Duplicate, Delete, Transition) from Orders and Jobs tabs
  - Added callouts linking to the main buttons page for standard actions
- Updated homepage QRC card label to "What the Buttons in Tramm Do"
- Reviewed and corrected data-manager/index.html based on code research:
  - Routing Classes Used By: corrected to note Planner and routing engine (not just Vehicle Classes)
  - System: set site address as required: clarified as per-user preference, not implementer-only
  - Setup Sequence Step 4 renamed to "Goods" (Products only); Clients, Transporters, Fleets moved to Optional Step 5
  - Step 6 clarified as financial/Transact only
  - Routes section removed from left nav and main content; Master Routes and Route Sets moved to Advanced & Optional
  - Regions description updated to name Lanes and Site allocation as the two uses
  - Orders description updated to note most clients integrate from external systems
  - Master Charges description updated: predefined charge rules, auto-applied, not manual per trip
- Strategic discussion: reframed project as a Help & Documentation site ("OPSI Docs")
- Restructured site navigation hierarchy:
  - Homepage (index.html): stripped to Hero + Products (Tramm, Mobile, FleetVision) + What's New only
  - tramm/index.html rebuilt as Tramm documentation hub: User Guides, Quick Reference, Understanding Tramm, Browse all apps
  - Pattern established for Mobile and FleetVision hubs to follow same structure
- Agreed content priority order: Data Manager → Planner → Execution Manager (PO direction)
- Discussed documentation depth needed: each app needs entity sub-pages, task guides, exception handling — Data Manager alone is ~8–10 pages of work

---

## 2026-05-20 (Wednesday)

- Rebuilt `tramm/data-manager/index.html` with full redesign:
  - Added sticky left-side navigation
  - Fixed paragraph alignment throughout
  - Corrected Movements description (multi-modal/crossdock records, distinct from Trips)
  - Improved Entity Types description (controls type dropdowns AND scopes attribute rules)
  - Moved Routing Classes to optional in the settings table (system uses Default fallback)
  - Moved Operators to their own group with optional callout
  - Added "Advanced & Optional" section (Regions, Lanes, Locations entity, Transport Segments, Transport Units)
  - Master Routes and Route Sets moved to optional Routes group
  - Simplified Setup Sequence to 6 steps
- Built `tramm/toolbar-reference.html` — Standard Toolbar Actions reference (Add, Duplicate, Edit, Admin Edit, Delete, Import, Export, Transition)
- Added Standard Toolbar Actions as a QRC card on the homepage
- Discussed system-wide button reference strategy: each app page references this page for standard buttons, then documents only its own additional actions

---

## 2026-05-13 (Wednesday)

- Built `whats-new/index.html` — release index page with cards for each release
- Built `whats-new/release-1174.html` — January 2026 release page with Vimeo showcase embed and 15 PDF download cards
- Updated homepage What's New card to reference Release 1174 (removed "coming soon")
- Fixed video intro text on release page after reviewing screenshots of actual Vimeo player
- Built `chorafeatures.html` — Chora route optimisation engine page with demo video embed and About section
- Walked through creating `whats-new/pdfs/` folder correctly on GitHub (`.gitkeep` trick)
- Rewrote `chorafeatures.html` with real content from David's file — job types, supported constraints, job controls, current limitations
- Replaced pill-style constraints with checkmark lists (pills implied clickability)
- Fixed Overview paragraph alignment and updated text to reference Solo by name
- Added Chora card to How Tramm Works section on homepage

---

## Previous sessions (dates not recorded)

- Edited `how-tramm-works/key-concepts.html` — Orders Used In, Trips Used In, Master Routes reframing (marked Advanced, noted separate app)
- Migrated GitHub repo from personal account to opsisystems org; updated all internal links
- Full homepage redesign — hero with search bar, product cards (Tramm/Mobile/FleetVision), QRC section, How Tramm Works section, What's New section
- Built `tramm/index.html` — 24 apps in 4 categories (Planning, Execution, Customers & Transporters, Data) with filter
- Investigated and resolved Vimeo embed issues — showcase embed URL format, individual video privacy hashes
- Planned What's New section structure (one showcase per release, PDF download cards per feature)
