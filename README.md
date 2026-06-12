# Enterprise and Platform Architecture

LaTeX book module for **IT30713 — Enterprise & Platform Architecture** (Pradita
University, Bahasa Indonesia), together with its ArchiMate models and exported
figures. This file is the **single handoff document** for the project — read it
fully before continuing the work.

## Repository layout
- [`module/`](module/) — all LaTeX sources (`*.tex`), `references.bib`, fonts,
  and the built PDF. Main file: `module/enterprise-platform-architecture.tex`.
- [`models/`](models/) — ArchiMate model(s), e.g. `models/session-02.archimate`.
- [`figures/`](figures/) — exported vector figures (PDF/SVG) used by the book.
- [`.mcp.json`](.mcp.json) — Archi MCP server config (project scope).

## Build
```bash
cd module
latexmk -lualatex -interaction=nonstopmode enterprise-platform-architecture.tex
```
Output PDF: `module/enterprise-platform-architecture.pdf`. The book uses
`fontspec`, so it must be built with **LuaLaTeX** (or XeLaTeX), not pdfLaTeX.

> **Note on paths below.** Unless a path begins with `models/`, `figures/`, or
> `.mcp.json` (repo root), file names in the sections that follow are relative
> to `module/` — e.g. `chapter02.tex` means `module/chapter02.tex`.

---

## 1. The running case study (authoritative facts)

Bank Wanua = a regional development bank (BPD) that wants to become the leading
**digital financial partner for local UMKM (SMEs)**. It agreed a prioritized
capability portfolio. **The three P1s are defined and agreed (treat as
baseline):**

1. Integrated UMKM customer single-view
2. Digital onboarding / e-KYC
3. **API Transfer / Fund-Movement (the rail)** ← **the chosen target capability the book dissects in depth**

Later priorities (context only, not dissected): P2 payment acceptance API
(QRIS/VA) + API gateway & governance; P3 lending/credit; P4 analytics, partner
portal, personalization.

**Why transfer first (the strategic rationale, used in ch3):** transfer is the
primitive rail all money movement composes on; high usage; relatively low build
(wraps BI-FAST); a quick win. **Transfer before payments.**

Key regulatory/context anchors (all already have BibTeX keys, see §4):
SNAP BI (`snapbi`), BI-FAST (mentioned in prose), UU PDP (`uupdp2022`),
PP 71/2019 (`pp712019`), APU-PPT/AML (prose). Stakeholders: pimpinan/direksi,
unit bisnis UMKM, divisi kepatuhan, tim teknologi/arsitektur, nasabah UMKM +
mitra (koperasi/marketplace/fintech), regulator (Bank Indonesia, OJK).

The case is introduced in `chapter01.tex` (Skenario Pembuka, §"Bank Daerah") and
in `pendahuluan.tex` (new §"Studi Kasus Berjalan" + §"Peta Lapisan Arsitektur").

---

## 2. Chapter → ArchiMate layer mapping (decisions locked with the user)

Decisions taken via clarifying questions:
- **Retitle chapters by layer** (not keep old syllabus titles).
- **Defer** Application/Technology/Physical/Implementation layers — only
  *preview* them in a bridge at the end of ch4 (do NOT create ch5–07; user
  confirmed missing chapters need not be created now).
- **Sharpen case + tables** depth: rewrite the "Studi Kasus Utama" sections and
  update existing tables/value-streams to the Transfer API; reuse existing TikZ,
  minimal new diagrams.

| Chapter file | `\label` key (KEPT STABLE) | New layer & title |
|---|---|---|
| `chapter02.tex` | `ch:strategi-bisnis` | **Lapisan Motivasi** — stakeholders, drivers, assessments, goals/outcomes, requirements, constraints, principles → derive problem/RQ/contribution |
| `chapter03.tex` | `ch:togaf-lite` | **Lapisan Strategi** — resources, capabilities, course of action, roadmap (P1→P4), BMC + operating model (moved here from old ch2), TOGAF-lite Architecture Vision + literature review |
| `chapter04.tex` | `ch:business-architecture` | **Lapisan Bisnis** — business services/processes/roles + capability map + value stream for the transfer rail, **+ bridge previewing App/Tech/Physical/Implementation** |

**IMPORTANT — cross-references:** the `\label` keys above are intentionally kept
unchanged even though they no longer match the titles. This avoids breaking the
many `\ref{ch:strategi-bisnis}` / `\ref{ch:togaf-lite}` / `\ref{ch:business-architecture}`
usages across files. **Do not rename these keys** unless you update every `\ref`.

---

## 3. Status — what is DONE vs REMAINING

### DONE
- [x] `pendahuluan.tex` — added §"Studi Kasus Berjalan: API Transfer Dana Bank
      Wanua" (locks the scope + P1/P2/P3/P4 portfolio), added §"Peta Lapisan
      Arsitektur dan Alur Bab" (new `tab:peta-lapisan`), and retitled session-table
      rows 2–4 (`tab:linimasa-sesi`) to the Motivation/Strategy/Business framing.
- [x] `chapter02.tex` — fully rewritten as **Motivation layer**. Full file Write.
      Motivation case study for the transfer API. Tables: `tab:bank-wanua-bmc`
      (now stakeholder-concern), `tab:bank-wanua-motivasi` (driver/assessment/goal,
      NEW), `tab:rq-baik-buruk`, `tab:artefak-bab2`, `tab:tradeoff-rq`,
      `tab:rubrik-latihan-bab2`. Figure `fig:strategi-ke-rq` recast to
      motivation→RQ flow. **The operating-model figure + BMC question table were
      REMOVED from ch2 and MOVED to ch3** (so `fig:operating-model` now lives in
      ch3).
- [x] `chapter03.tex` — fully rewritten as **Strategy layer**. Full file Write.
      Adds `tab:roadmap-transfer` (NEW, P1→P4), recast `tab:bank-wanua-vision` to
      the transfer rail, moved-in `fig:operating-model`. Kept `fig:adm-lite-ch3`,
      `fig:vision-literature-loop`, `tab:artefak-bab3`, `tab:tradeoff-bab3`,
      `tab:rubrik-bab3`.

- [x] **`chapter04.tex` → Business layer.** Fully rewritten as Business layer for
      the transfer rail: Layanan Transfer Dana, process (inisiasi → validasi &
      otorisasi → penyaringan AML/limit → eksekusi BI-FAST → konfirmasi/notifikasi
      → rekonsiliasi), roles/actors/objects, capability map + value stream
      sharpened to transfer. Kept all `\label` keys. Added §"Pratinjau Lapisan
      Aplikasi, Teknologi, Fisik, dan Implementasi" (`tab:pratinjau-lapisan`,
      NEW) as the bridge for the deferred layers.

- [x] **Compile & fix.** Built clean with
      `latexmk -lualatex enterprise-platform-architecture.tex` (this repo's
      engine is **LuaLaTeX** per the `.fls`; fontspec requires Xe/LuaLaTeX, not
      pdfLaTeX). Result: 86 pages, exit 0, **no undefined refs/citations**. Fixed
      one 40pt running-header overflow by giving ch2's long "Skenario Pembuka"
      section a short `\section[...]{...}` form. Remaining ~20.9pt "while \output
      is active" overfull boxes are **pre-existing** chapter-title running-header
      overflows in this B5 layout (not introduced here).

### REMAINING
- All planned work for this overhaul is complete. Natural next steps if the
  course continues the layer-by-layer treatment: create `chapter05+` for the
  deferred Application/Technology/Physical/Implementation layers of the transfer
  rail (see the bridge `tab:pratinjau-lapisan` in ch4 for the seed content).

---

## 4. Conventions to MATCH (house style)

- **Language:** Bahasa Indonesia, managerial tone, audience = non-IT master's
  students. English ArchiMate terms in `\emph{...}` on first use.
- **Document:** `book` class, B5 paper, `tabularx`, `\scriptsize` tables,
  `fontspec` (TitilliumWeb) → must compile with **XeLaTeX**. Main file:
  `enterprise-platform-architecture.tex` (chapters `\include`d).
- **TikZ palette:** `praditagreen` (RGB 37,113,71) defined in main file;
  fills like `praditagreen!10/20`, `orange!16/18`, `blue!10/12`, `gray!12/16`,
  `red!8`. Reuse existing styles; keep diagrams minimal (user asked).
- **Chapter skeleton (keep all sections):** Tujuan Pembelajaran → Ringkasan Awal
  Bab → Pendahuluan → Skenario Pembuka + Pertanyaan Pemandu → Mengapa Penting →
  Konsep Inti + Glosarium Mini → Kerangka Berpikir (figure) → Konteks Indonesia
  → Studi Kasus Utama (tables/figures) → Langkah Analisis (8 steps) → Integrasi
  ke Makalah → Diskusi Kritis/Trade-off → Latihan Terapan Individual + Rubrik →
  Ringkasan/Refleksi/Jembatan → Bacaan Lanjutan.
- **BibTeX keys available** (`references.bib`): `togaf10`, `parker2016platform`,
  `cusumano2019business`, `evans2016matchmakers`, `ross2006enterprise`,
  `ross2019designed`, `jacobson2011apis`, `medjaoui2018continuous`,
  `newman2021building`, `uupdp2022`, `pp712019`, `satudata`, `snapbi`.
  **Reuse these keys; do not invent new citations** without adding a verified
  entry to `references.bib` (entries there have HTTP-verified URLs/ISBNs).

---

## 5. Out of scope / do not touch
- Do not create `chapter05–07.tex` (deferred per user).
- Do not rewrite `chapter01.tex` (it introduces the case; only ch2–4 + pendahuluan).
- Do not change `\label` keys (see §2).
- `session-transcript.jsonl` in repo root is unrelated to this overhaul.

---

## 6. Follow-on: ArchiMate Motivation model + chapter 02 diagram (DONE)

**Task:** Build the ArchiMate model that backs chapter 02 in
`models/session-02.archimate`, create a **Motivation view** for the
Transfer/Fund-Movement API, embed that view as a (vector) diagram inside
`chapter02.tex`, and add a reference section in ch2 that discusses **every
Motivation-layer element type in Archi, showing each symbol**.

### Environment facts (verified this session)
- `models/session-02.archimate` exists (empty skeleton: layer folders +
  one empty "Default View", model id
  `id-c349a2babc3d499ab609bb44deadbd09`). A `.bak` sits beside it.
- Archi MCP server is configured in `.mcp.json`
  (`http://127.0.0.1:18090/mcp`, HTTP transport) and is **reachable** (returns
  400 without the MCP `initialize` handshake).
- **Gotcha (from prior session):** the MCP server only operates on the model
  **currently open in the Archi GUI**, and a client session binds to the
  load-state at connect time. If you get `MODEL_NOT_LOADED`, the user must open
  `session-02.archimate` in Archi, then you must **open a fresh MCP session**
  (reconnect ≠ restart server). Useful tools seen before: `bulk-mutate`
  (supports `$N.id` back-refs), `add-to-view`, `auto-connect-view`,
  `auto-layout`, `auto-route-connections`, `export-view` (`inline:false` to
  write a file), `search-elements`, `delete-element` (param is `elementId`).
- There is **no save tool** in MCP (GUI action). Saving the `.archimate` file
  is a GUI Ctrl+S, or the user saves.

### Motivation elements to model/discuss (full ArchiMate set)
Stakeholder, Driver, Assessment, Goal, Outcome, Principle, Requirement,
Constraint, Meaning, Value. (ch2 prose already introduces stakeholder, driver,
assessment, goal, outcome, requirement, constraint, principle — the reference
section must additionally cover **Meaning** and **Value** and show all symbols.)

### Diagram approach (decision)
The book is TikZ-heavy and `\usepackage{svg}` is present. Vector options:
(a) draw the motivation view + the element-symbol legend natively in **TikZ**
(self-contained, no external toolchain, matches house style), or
(b) `export-view` from Archi as **SVG** and `\includesvg`. Prefer the approach
that compiles cleanly here; if `inkscape` is unavailable for the `svg` package,
use TikZ. Keep `praditagreen` palette + `\scriptsize`.

### Status
- [x] **Motivation model BUILT in Archi** (`session-02`, model id
      `id-c349a2babc3d499ab609bb44deadbd09`) via MCP over HTTP. 21 elements
      covering **all 10 motivation types** + 21 relationships
      (Association/Influence/Realization) for the Transfer-API case.
- [x] **Motivation view BUILT** — name "Motivasi - API Transfer Dana", view id
      `id-75def7f05aca4a8f81d3f1b1dcb22998`. Laid out RIGHT, auto-connected
      (alignment 90, 2 crossings).
- [x] **Notation legend view BUILT** — name "Legenda Notasi Motivasi", view id
      `id-3eed2857af54482a8ea992d983a4221d`. One element per motivation type in
      a 2×5 grid (purpose: show every Archi symbol).
- [x] **Vector files EXPORTED to `figures/`** (graphicspath already includes
      `figures/`):
      - `motivation-transfer.pdf` + `.svg` — the case model view (tall
        portrait, ~1766×3306). **Embed the `.pdf`** (no Inkscape here, so
        `\includesvg` won't work; LuaLaTeX embeds PDF as vector natively).
      - `motivation-legend.pdf` + `.svg` — the 10-symbol legend.
- [x] **DONE 1 — embed case figure in `chapter02.tex`.** In §"Studi Kasus
      Utama: Model Motivasi...", insert this **immediately before** the
      paragraph starting `Dari kedua tabel terlihat bahwa sasaran transfer`,
      and add a sentence referencing it (e.g. begin that paragraph with
      "Gambar~\ref{fig:motivation-transfer} merangkum keduanya sebagai satu
      model motivasi. Dari kedua tabel..."):
      ```latex
      \begin{figure}[p]
      \centering
      \includegraphics[height=0.78\textheight,keepaspectratio]{motivation-transfer.pdf}
      \caption{Model motivasi (ArchiMate) API Transfer Dana Bank Wanua,
      dibangun dengan Archi: pemangku kepentingan, pendorong, asesmen, sasaran,
      hasil, prinsip, kebutuhan, kendala, makna, dan nilai beserta
      keterhubungannya (pengaruh, realisasi, asosiasi).}
      \label{fig:motivation-transfer}
      \end{figure}
      ```
- [x] **DONE 2 — add the symbol-reference subsection to `chapter02.tex`.**
      Insert **immediately before** `\section{Glosarium Mini}` (end of §"Konsep
      Inti: Lapisan Motivasi ArchiMate"). This satisfies "discuss all Motivation
      element types + display the symbols" (note: prose already covers
      stakeholder/driver/assessment/goal/outcome/principle/requirement/constraint;
      the table below adds **Meaning** and **Value** which were missing):
      ```latex
      \subsection{Notasi Elemen Lapisan Motivasi di Archi}

      Gambar~\ref{fig:motivation-legend} menampilkan sepuluh jenis elemen
      lapisan motivasi ArchiMate beserta notasinya di Archi. Semua elemen
      motivasi memakai bentuk oktagon (sudut terpotong) dan, secara baku,
      berwarna ungu; ikon kecil di pojok kanan atas membedakan jenisnya.

      \begin{figure}[htbp]
      \centering
      \includegraphics[width=0.85\textwidth]{motivation-legend.pdf}
      \caption{Sepuluh jenis elemen lapisan motivasi ArchiMate dan simbolnya
      di Archi.}
      \label{fig:motivation-legend}
      \end{figure}

      \begin{table}[htbp]
      \centering
      \scriptsize
      \caption{Jenis elemen lapisan motivasi ArchiMate dan maknanya.}
      \label{tab:motivation-elements}
      \begin{tabularx}{\textwidth}{@{}p{0.18\textwidth} p{0.24\textwidth} X@{}}
      \hline
      \textbf{Elemen} & \textbf{Simbol (ikon)} & \textbf{Makna} \\
      \hline
      Stakeholder & Penanda peran (lingkaran) & Pihak yang berkepentingan atas hasil arsitektur. \\
      Driver & Roda kemudi & Faktor internal/eksternal yang mendorong perubahan. \\
      Assessment & Kaca pembesar & Hasil analisis kondisi terhadap suatu pendorong. \\
      Goal & Sasaran (\emph{bullseye}) & Keadaan akhir yang ingin dicapai. \\
      Outcome & \emph{Bullseye} berpanah & Hasil konkret yang menandai sasaran tercapai. \\
      Principle & Tanda seru & Aturan umum yang menuntun banyak keputusan arsitektur. \\
      Requirement & Jajaran genjang & Pernyataan yang harus dipenuhi sistem/organisasi. \\
      Constraint & Jajaran genjang ganda & Batas yang tidak dapat dilanggar. \\
      Meaning & Awan & Makna atau interpretasi yang melekat pada suatu elemen. \\
      Value & Elips & Nilai atau manfaat relatif bagi pemangku kepentingan. \\
      \hline
      \end{tabularx}
      \end{table}

      \emph{Meaning} dan \emph{Value} melengkapi delapan elemen sebelumnya:
      \emph{Meaning} menyatakan arti yang disepakati atas sebuah konsep
      (misalnya apa yang dimaksud ``transfer''), sedangkan \emph{Value}
      menyatakan manfaat yang dirasakan pemangku kepentingan (misalnya
      likuiditas dan kepercayaan UMKM).
      ```
- [x] **DONE 3 — recompile.** Built with `cd module && latexmk -lualatex
      -interaction=nonstopmode enterprise-platform-architecture.tex`. The result
      is 88 pages; both new figures appear and there are no undefined refs.
- [x] **DONE 4 — SAVE THE ARCHI MODEL.** The user saved the model in Archi.
      `models/session-02.archimate` now contains the 21 case elements, 10
      legend exemplars, 21 relationships, and both new views.

### How the model was driven (for reproducing/continuing)
- No `mcp__archi__*` tools are exposed to this Claude session, so the server was
  driven directly over **streamable HTTP** at `http://127.0.0.1:18090/mcp`.
- Helper at `/tmp/archi.sh` (`archi.sh <tool> '<json-args>'`); session id in
  `/tmp/archi_session`. If the session expired, re-run the `initialize` +
  `notifications/initialized` handshake (capture `Mcp-Session-Id` response
  header) and confirm load with `get-model-info`. If `MODEL_NOT_LOADED`, have
  the user open `session-02.archimate` in Archi first, then re-handshake.
- Element creation used `bulk-mutate` with `{tool, params}` ops and `$N.id`
  back-references; relationship types are `AssociationRelationship`,
  `InfluenceRelationship`, `RealizationRelationship`. View built with
  `create-view` + `add-to-view`, connected with `auto-connect-view`, laid out
  with `auto-layout-and-route` (`mode:auto, direction:RIGHT`), exported with
  `export-view` (`inline:false, outputDirectory:<abs path>`).

## 7. Follow-on: installation appendix (DONE)
- [x] Added `appendixA.tex` and included it before `\backmatter` in
      `enterprise-platform-architecture.tex`.
- [x] Documented Windows, Ubuntu Linux, and macOS installation steps for
      Python, VS Code, Codex CLI, Claude Code CLI, and Archi.
- [x] Documented Archi MCP Server plug-in installation, Claude Code and Codex
      configuration, connection tests, troubleshooting, and a final checklist.
- [x] Verified the current Archi and CLI installation commands against their
      official documentation on 1 June 2026.
- [x] Recompiled with LuaLaTeX. The generated PDF is 98 pages with no undefined
      references, oversized floats, or new appendix overfull boxes.

### What the appendix contains
- Cross-platform installation instructions for Windows 10/11, Ubuntu Linux,
  and macOS.
- Official download and verification steps for Python, Visual Studio Code,
  Codex CLI, Claude Code CLI, and Archi.
- Archi MCP Server plug-in installation through `Help > Manage Plug-ins >
  Install New...`, followed by `MCP Server > Start MCP Server`.
- Claude Code project configuration in `.mcp.json` and Codex configuration in
  `.codex/config.toml` or `~/.codex/config.toml`.
- Endpoint smoke test, client smoke test, troubleshooting table, and final
  checklist.

### Current setup values
- Archi MCP endpoint: `http://127.0.0.1:18090/mcp`.
- Archi stable release checked on 1 June 2026: `5.9.0`, bundled with Java
  Runtime 21.
- Archi MCP Server release checked on 1 June 2026: `v1.4.0`.
- Archi MCP Server requires Archi `5.7+` and Java `21+`.
- Treat those release numbers as time-sensitive. Check the official download
  and release pages again before changing version-specific prose.

### Official sources used for Appendix A
- Python: <https://www.python.org/downloads/>
- Python on Windows: <https://docs.python.org/3/using/windows.html>
- Visual Studio Code: <https://code.visualstudio.com/download>
- Visual Studio Code on Linux: <https://code.visualstudio.com/docs/setup/linux>
- Codex CLI: <https://developers.openai.com/codex/cli/>
- Codex MCP: <https://developers.openai.com/codex/mcp/>
- Claude Code setup: <https://code.claude.com/docs/en/setup>
- Claude Code MCP: <https://code.claude.com/docs/en/mcp>
- Archi: <https://www.archimatetool.com/download/>
- Archi MCP Server: <https://github.com/fanievh/archi-mcp-server>
- Archi MCP Server releases:
  <https://github.com/fanievh/archi-mcp-server/releases>
- Optional Java 21 fallback:
  <https://adoptium.net/temurin/releases/?version=21>

### Files touched for this follow-on
- `appendixA.tex` — new Appendix A source.
- `enterprise-platform-architecture.tex` — adds `\appendix` and
  `\include{appendixA}` immediately before `\backmatter`.
- `chapter02.tex` — keeps `motivation-transfer.pdf` at
  `height=0.78\textheight`; larger values caused an oversized-float warning.
- `README.md` (repo root) — this single handoff document (the former
  `module/README.md` has been merged here).

### Reproduce the final verification
Run from the repository root:

```bash
cd module
latexmk -lualatex -interaction=nonstopmode enterprise-platform-architecture.tex
cd ..
git diff --check
xmllint --noout models/session-02.archimate
```

For an appendix-only LaTeX warning scan, run from `module/`:

```bash
awk 'index($0, "(./appendixA.tex") { seen=1 } seen && /(Overfull|Float too large|undefined|multiply defined|Rerun to get cross-references right)/ { print }' enterprise-platform-architecture.log
```

Expected result: the scan prints nothing. The full book still contains older
layout warnings in preceding chapters; do not attribute those to Appendix A.

For visual QA, render and inspect Appendix A pages:

```bash
cd module
pdftoppm -f 89 -l 95 -png -r 110 enterprise-platform-architecture.pdf /tmp/epa-appendix
```

### Worktree safety note
The repository was already dirty when this follow-on started. In particular,
`chapter03.tex`, `chapter04.tex`, and `pendahuluan.tex` contain user work that
was not created for Appendix A. Do not revert or overwrite those changes.
The Archi model at `models/session-02.archimate`, `.mcp.json`, and the
motivation figure exports are also intentional project artifacts.

## 8. Follow-on: complete Archi Documentation fields via MCP (SAVE REQUIRED)
The user explicitly requested that model changes be applied through Archi MCP,
not by editing `session-02.archimate` directly. Keep using MCP for subsequent
model mutations.

### Current in-memory Archi state
- [x] Updated the model purpose through `update-model`.
- [x] Sent `update-folder` for all 9 top-level folders.
- [x] Filled Documentation for all 31 Motivation elements through
      `update-element`.
- [x] Filled Documentation for all 21 relationships through
      `update-relationship`.
- [x] Filled Documentation for all 3 views through `update-view`.
- [x] Verified through MCP readback that `31/31` elements, `21/21`
      relationships, and `3/3` views have non-empty Documentation.
- [ ] **SAVE REQUIRED:** press `Ctrl+S` in Archi to persist the in-memory MCP
      changes to `models/session-02.archimate`.

The current plug-in exposes `update-folder`, but `get-folders` did not return a
Documentation field during readback. All 9 folder update operations reported
success; do not claim folder Documentation readback verification unless a
later plug-in version exposes that field.

### MCP workflow used
1. Start the server in Archi with `MCP Server > Start MCP Server`.
2. Initialize a streamable HTTP MCP session at
   `http://127.0.0.1:18090/mcp`, send `notifications/initialized`, and retain
   the `Mcp-Session-Id` response header.
3. Confirm the active model with `get-model-info`; expected model name:
   `session-02`.
4. Use `bulk-mutate` with small batches of `{tool, params}` operations so
   updates become visible progressively in Archi. Each batch is separately
   undoable.
5. Verify with `search-elements` using `query: ""`, `fields: "full"`, and
   `limit: 500`; use the analogous `search-relationships` query and
   `get-views` with `fields: "full"`.
6. Press `Ctrl+S` in Archi. This plug-in version does not expose a
   `save-model` MCP tool.

### Important continuation note
Diagram objects inside a view reference their underlying ArchiMate elements;
they do not have a separate Documentation field in the Archi UI. The view
itself does have Documentation and has been updated. If adding new elements,
relationships, or views later, fill their Documentation through the matching
MCP update tool before saving.

## 9. Follow-on: detailed explanation of the motivation figure (DONE)
- [x] Kept the Archi-exported case figure in `chapter02.tex` as
      `fig:motivation-transfer`.
- [x] Added subsection `Cara Membaca Diagram Motivasi API Transfer Dana`
      immediately after the figure.
- [x] Referenced the figure repeatedly in the prose and explained that it is a
      selective argument map derived from the broader stakeholder and
      motivation tables.
- [x] Explained the three relationship types used in the figure:
      association, influence, and realization.
- [x] Walked through the explicit model chain: stakeholders, assessments,
      four drivers, the central real-time 24/7 goal, three requirements, two
      principles, two constraints, outcomes, value, and meaning.
- [x] Distinguished concepts explicitly visualized in the Archi diagram from
      implementation details derived from the tables, such as idempotency,
      audit trail, personal-data protection, certification, and architecture
      staffing limits.
- [x] Recompiled with LuaLaTeX. The generated PDF remains 98 pages with no
      undefined references, oversized floats, or new overfull boxes from the
      added subsection.

## 10. Follow-on: add examples to Section 3.6 mini glossary (DONE)
- [x] Expanded `chapter02.tex` Section `Glosarium Mini`.
- [x] Added at least two concrete examples for every glossary term.
- [x] Split combined entries so `goal`, `outcome`, `requirement`, `constraint`,
      `rumusan masalah`, `RQ`, and `kontribusi` each have their own definition
      and examples.
- [x] Added `meaning` and `value` entries so the glossary matches the complete
      Motivation-layer notation table.
- [x] Recompiled with LuaLaTeX and visually inspected the glossary on PDF pages
      39--40. The generated PDF remains 98 pages with no undefined references,
      oversized floats, or new glossary overfull boxes.

## 11. Follow-on: tidy Section 3.7 thinking-flow figure (DONE)
- [x] Reviewed Figure `fig:strategi-ke-rq` in `chapter02.tex` for semantic and
      visual consistency with the surrounding text.
- [x] Added `prinsip` to the target-state node so the diagram matches the
      chapter artifacts described in prose.
- [x] Kept both the assessment and target-state direction as inputs to
      `Ketidakselarasan`, then made the final reasoning path explicit:
      `Ketidakselarasan -> Rumusan masalah -> RQ dan kontribusi`.
- [x] Replaced the crossing-arrow layout with a clean two-row snake flow.
- [x] Moved the artifact summary into a light boxed note and shortened the
      follow-up paragraph without changing its meaning.
- [x] Recompiled with LuaLaTeX and visually inspected PDF page 40. The
      generated PDF remains 98 pages with no undefined references, oversized
      floats, or new diagram overflow warnings.

## 12. Follow-on: recheck both Chapter 2 figures (DONE)
- [x] Rechecked Figure `fig:strategi-ke-rq` on PDF page 40. Its two-row flow is
      visually clean and its semantics remain correct:
      `assessment + target direction -> mismatch -> problem statement -> RQ
      and contribution`.
- [x] Rechecked the Archi-exported Figure `fig:motivation-transfer` on PDF page
      43. The caption explicitly states that the ArchiMate model was built with
      Archi.
- [x] Confirmed that subsection `Cara Membaca Diagram Motivasi API Transfer
      Dana` refers to the Archi figure repeatedly and explains it in detail:
      relationship types, stakeholders, assessments, drivers, central goal,
      requirements, principles, constraints, outcomes, value, meaning, derived
      implementation needs, mismatches, problem statement, RQ, and
      contribution.
- [x] Visually inspected the surrounding explanation on PDF pages 42--45.
- [x] Re-ran LuaLaTeX checks. The PDF remains 98 pages with no undefined
      references, oversized floats, or `git diff --check` issues.

## 13. Follow-on: align chapter01 + SVG-derived figure PDFs (DONE)
- [x] **`chapter01.tex` made consistent with ch2 (Motivation) and pendahuluan.**
      Rewrote §"Jembatan ke Bab Berikutnya" so Bab 2 is the **ArchiMate
      motivation layer** for the API Transfer Dana case (was BMC/Operating-Model,
      now in ch3); updated the final §"Ringkasan Bab" paragraph accordingly;
      introduced **ArchiMate** + its layers in the BDAT subsection with a
      cross-ref to `tab:peta-lapisan`; added an **ArchiMate** glossary entry;
      linked the Bank Wanua "Studi Kasus Mini" to the locked running case via
      `\ref{sec:studi-kasus-berjalan}`.
- [x] **Figure PDFs are now generated FROM the SVGs** (SVG = source of truth):
      ```bash
      cd figures
      rsvg-convert -f pdf -o motivation-transfer.pdf motivation-transfer.svg
      rsvg-convert -f pdf -o motivation-legend.pdf   motivation-legend.svg
      ```
      Producer is now cairo/librsvg (vector). **Do not re-export PDFs directly
      from Archi** — re-export the **SVG** from Archi, then convert with
      `rsvg-convert` (Inkscape not installed; `cairosvg` also works). Supersedes
      the "Archi-exported PDF" note in §6.
- [x] Recompiled with LuaLaTeX: **98 pages, no undefined refs/citations**.

## 14. Follow-on: re-layout "Motivasi - API Transfer Dana" view (DONE; SAVE NEEDED)
- [x] Re-laid out the case view (id `id-75def7f05aca4a8f81d3f1b1dcb22998`) via
      MCP `apply-positions` so the **Goal "Transfer Dana Real-time 24/7" sits in
      the centre**, motivators (assessments+meaning, stakeholders, drivers) on
      **top**, and requirements/principles/constraints/outcomes/value on the
      **bottom**; then `auto-route-connections` (orthogonal, crossings 108→19).
- [x] Re-exported `figures/motivation-transfer.svg`, regenerated
      `motivation-transfer.pdf` from it with `rsvg-convert` (vector, 0 raster).
      The figure is now near-square (~642×577 pts) instead of tall portrait.
- [x] Adjusted `chapter02.tex` figure to
      `\includegraphics[width=\textwidth,height=0.85\textheight,keepaspectratio]`
      and float `[tbp]` (was height-only `[p]`, sized for the old portrait).
- [x] Enlarged all element boxes (≈175×84) so every label fits (the 155×60
      boxes were clipping longer labels).
- [x] **FINAL layout was set MANUALLY by the user in Archi** (goal centred,
      motivators on top, requirements/principles/outcomes/constraints/value
      around the bottom and sides). I exported that state — do **not** re-run
      `apply-positions`/`auto-layout` on this view, it would overwrite the
      user's hand-tuned positions. To refresh the figure after any further
      manual tweak: re-export SVG via MCP `export-view`, then
      `rsvg-convert -f pdf -o figures/motivation-transfer.pdf figures/motivation-transfer.svg`.
- [x] Current figure: vector PDF, 812×558 pts (landscape ~1.46:1), 0 raster.
      `chapter02.tex` uses
      `\includegraphics[width=\textwidth,height=0.85\textheight,keepaspectratio]`.
- [x] Recompiled: 98 pages, clean; verified on PDF page 43 (goal centred, all
      labels visible, fits with caption).
- [ ] **SAVE NEEDED:** the manual positions live in Archi's in-memory model;
      press **Ctrl+S** in Archi to persist them to `models/session-02.archimate`
      (no MCP save tool).
