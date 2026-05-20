# Tramm Help Site — Work Log

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

## 2026-05-27 (Wednesday)

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

## Previous sessions (dates not recorded)

- Edited `how-tramm-works/key-concepts.html` — Orders Used In, Trips Used In, Master Routes reframing (marked Advanced, noted separate app)
- Migrated GitHub repo from personal account to opsisystems org; updated all internal links
- Full homepage redesign — hero with search bar, product cards (Tramm/Mobile/FleetVision), QRC section, How Tramm Works section, What's New section
- Built `tramm/index.html` — 24 apps in 4 categories (Planning, Execution, Customers & Transporters, Data) with filter
- Investigated and resolved Vimeo embed issues — showcase embed URL format, individual video privacy hashes
- Planned What's New section structure (one showcase per release, PDF download cards per feature)
