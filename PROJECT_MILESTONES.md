# Maker Library Project — Running Status & Milestones

This file is the source of truth for the ongoing Maker Library fork of Printventory.

Repository: `thesmokincelt/Printventory`

## Working Agreement

For every meaningful code change:
1. Make the code change on a feature branch.
2. Update this file in the same branch before the work is considered complete.
3. Record:
   - what changed,
   - what was validated,
   - what remains open,
   - what should happen next.
4. Keep pull requests/draft pull requests as checkpoints.
5. Prefer GitHub as project memory so new ChatGPT threads can resume by reading this file plus the relevant branch/PR.

## Product Direction

Goal: evolve Printventory into a unified local-first maker asset library for Windows, covering both 3D-print and laser/CNC-style assets without forcing users to reorganize their source folders.

Core direction:
- preserve Printventory's existing STL/3MF workflows,
- add first-class laser/vector assets,
- keep previews visual and fast,
- support mixed maker projects,
- keep files where they already live,
- make GitHub/project metadata the source of truth for development continuity.

## Current Milestone

### Milestone 1 — SVG / Laser Asset Foundation

Status: **In progress — initial implementation complete, validation active**

Branch:
`feature/laser-svg-support`

Draft PR:
`#1 — Add first-class SVG preview support for laser assets`

Completed:
- Confirmed Printventory already discovers SVG files.
- Confirmed the desktop renderer already uses SVG content as library-card thumbnails.
- Added SVG to the full previewable-file path.
- Added 2D SVG preview behavior instead of forcing SVG through the 3D mesh viewer.
- Added SVG handling to the standalone/headless thumbnail worker.
- Added SVG thumbnail regression coverage.
- Added a fork-safe Maker Library CI workflow.
- Maker Library CI passed.

Important finding:
Printventory already contains architectural hooks for additional maker formats, including SVG, DXF, and G-code. This makes extension preferable to a ground-up rewrite.

Validation:
- Feature branch is based on current `main`.
- Branch is ahead of `main` only by Maker Library changes.
- Maker Library CI: passing.
- Inherited TestDriver.ai workflow may fail on the fork because upstream secrets/configuration are not necessarily available; do not treat that alone as a Maker Library regression.

## Next Milestone

### Milestone 2 — DXF Preview Support

Planned work:
- trace current DXF scan/index behavior,
- choose a lightweight DXF parser/renderer compatible with Electron,
- render DXF geometry to a 2D preview,
- calculate useful bounds/dimensions,
- generate persistent library-card thumbnails,
- add full-preview support,
- add tests,
- avoid breaking existing STL/3MF behavior.

Success criteria:
- a scanned DXF appears visually in the library,
- the user can open a DXF preview without LightBurn,
- dimensions/bounds are available where reliable,
- headless/server thumbnail generation can handle DXF,
- Maker Library CI passes.

## Future Milestones

### Milestone 3 — LightBurn `.lbrn2`
Investigate format structure and add:
- visual preview,
- project bounds,
- layer/color information where reliable,
- direct Open in LightBurn action.

### Milestone 4 — Maker Asset Classification
Introduce broader asset concepts without breaking Printventory's existing model database:
- 3D Print
- Laser
- Artwork/Image
- Document
- Project

### Milestone 5 — Project Grouping
Group related files such as:
- STL / 3MF
- SVG / DXF / LBRN2
- source images
- PDFs/instructions
- finished-project photos

### Milestone 6 — Maker Metadata
Potential fields:
- material,
- machine,
- process,
- source/vendor,
- notes,
- dimensions,
- favorite,
- tested settings.

### Milestone 7 — Windows Packaging / Release
- Windows installer validation,
- upgrade path,
- app identity/name decision,
- release notes,
- versioning strategy.

## Open Product Decisions

Not blocking current work:
- final product name,
- whether to keep the Printventory brand internally or rename the fork,
- exact database schema for maker asset classification,
- sidecar metadata format and filename,
- whether WeCreat project formats are practical to support.

## Resume Instructions for a New ChatGPT Thread

Use a prompt like:

> Continue the Maker Library project in `thesmokincelt/Printventory`. Read `PROJECT_MILESTONES.md`, inspect open PRs and active feature branches, then continue from the documented Next Milestone. Treat the repository as the source of truth and update `PROJECT_MILESTONES.md` with every code change.

The new thread should inspect:
1. `PROJECT_MILESTONES.md`
2. open pull requests
3. active feature branches
4. recent commits

Do not rely on old chat history when the repository provides newer information.

## Update Log

### 2026-10-06
- Created project-thread workflow.
- Added this running milestone/status file.
- Established GitHub as the cross-thread source of truth.
- Current active work remains SVG / laser asset foundation in Draft PR #1.
- Next planned implementation: DXF preview support.
