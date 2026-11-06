# AGENTS.md

## Project
Single-page Vietnamese marketing + pricing site for GS.studio (yearbook & graduation photography, HCMC). Static, no build step, no backend — the owner wants to drag-and-drop the folder onto Netlify.

## Architecture
- `index.html` contains everything, in this order: `<head>` meta/SEO → `<script>` with the **`CONFIG` object** (all editable content: contacts, prices, benefits, FAQ, heroAnh, gallery, video, goiYDiaDiem, checklist, tips, process) → `<style>` → markup (SVG sprite incl. redrawn logo `#i-logo`, header, hero, story, `#anhkhach` customer photos + gift video, 3 tab panels, footer, FAB, bottom nav, lightbox) → app IIFE script.
- Panels: `#panel-banggia`, `#panel-chuanbi`, `#panel-datlich` (the Concept/gallery tab was removed on request — studio is new, only real pre-grad/ceremony photos); switched by `showTab(id)` via `[data-tab]` / `[data-goto]` buttons; URL hash mirrors the tab.
- State: single localStorage key `gsstudio_v1` → `{tab, goi, loaiKhach, checklist, form}`; all access wrapped in try/catch.
- Packages: `kieu: "SCG"` (Single/Couple/Group prices, `donVi` "nguoi" or "cap") or `kieu: "tuyChon"` (per-person sub-options; `gia: null` = "Liên hệ tư vấn"). `OPTIONS` flattens them for the booking dropdown; `quote()` computes totals.
- Images go through `cdn()` (Netlify Image CDN, WebP) with `__imgErr` fallback to the raw file, then to a CSS placeholder.

## Conventions
- All user-facing text in Vietnamese with full diacritics; money via `money()` → `499.000đ`.
- LIGHT theme only (cream #FBF7EF / #F5EDDC / white, gold #C9A24B, text #2A2118) — never dark backgrounds, incl. footer & lightbox. Numbers use lining tabular nums. Photos: only real customer photos (no stock/AI), polaroid frame, no dark overlays.
- Colors/tokens are CSS variables in `:root`; keep mobile-first, tap targets ≥44px, no horizontal scroll.
- Keep content in `CONFIG` (with Vietnamese comments) rather than hard-coding in markup.
- Brand voice: warm, casual "tụi mình", mascot nickname "Sót".
