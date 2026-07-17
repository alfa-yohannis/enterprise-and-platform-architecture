# TODO / Runbook — ArchiMate layers for the EAPA book

**Purpose.** This file lets an agent (or a future me) continue building the book
**layer by layer** with no extra briefing. Point the agent at this file and say
e.g. *"do the Application layer following TODO.md"* and it should run end-to-end.

Running case study throughout: **Bank Wanua — API Transfer Dana** (real-time 24/7
fund transfer, wraps BI-FAST, complies with SNAP BI).

---

## 1. Status

| ArchiMate layer | Model + views | Figures | Chapter | Slides |
|---|---|---|---|---|
| Motivation | ✅ | `motivation-legend/-transfer/-contoh` | `chapter02.tex` (Bab 3) | `session02` |
| Strategy | ✅ | `strategy-legend/-transfer/-contoh` | `chapter03.tex` (Bab 4) | `session03` |
| **Business** | ✅ | `business-legend/-transfer/-overview/-asis/-tobe/-contoh` | `chapter04.tex` (Bab 5) | `session04` |
| **Data** | ✅ | `data-legend/-transfer/-akses/-asis/-tobe/-contoh` | `chapter05.tex` (Bab 6) | `session05` |
| **Application** | ✅ | `app-legend/-transfer/-stack/-contoh` | `chapter06.tex` (Bab 7) | `session06` |
| **Technology & Physical** | ✅ | `technology-legend/-transfer/-stack/-contoh` | `chapter07.tex` (Bab 8) | `session07` |
| **Implementation & Migration** | ⬜ TODO (next) | — | `chapter08.tex` | `session08` |

> Chapter file numbering is offset by one from the book "Bab" number
> (`chapter02.tex` = Bab 3, so `chapter07.tex` = Bab 8). Data (`chapter05`, Fase C
> Data), Application (`chapter06`, Fase C Application), and Technology
> (`chapter07`, Fase D) are **done**. **The next chapter is Implementation &
> Migration (`chapter08.tex`, Bab 9, TOGAF Fase E/F)** — the bridge at the end of
> `chapter07.tex` points to it (work package / deliverable / plateau / gap turn the
> target architecture into a phased roadmap).

Model now (session-07): Motivation 41, Strategy 27, Business 61, Application 46 (16 DataObjects + 30 application elements), Technology 33 (3 Nodes + Device + 4 SystemSoftware + 3 TechnologyService + 3 Artifact + 2 CommunicationNetwork for Bank Wanua, plus restaurant example + 12 legend exemplars). Implementation folder is empty. Key cross-layer links: **Node → serving → ApplicationComponent** ("menggelar"; Node→Assignment→Component is rejected by Archi), **Artifact → realizes → DataObject** ("mewujudkan"), Node → composition → Device/SystemSoftware, Node → realizes → TechnologyService.

**Per-layer view set delivered for each completed layer** (replicate for the next
layers): a notation **legend** view; a main case-study **transfer** view; for
Business also an **overview**, **as-is (baseline)** and **to-be (target)** view
(the as-is/to-be pair mirrors the TOGAF Phase B baseline→target table — annotate
with `add-note-to-view`); thematic split views; per-element **`Contoh <Layer> -
N. <Type>`** teaching views (focal element + 1–2 neighbours) and a **`Contoh
Komprehensif - <Layer>`** view that shows every element type interacting once.
The `Contoh*` views use a shared **restaurant ("restoran cepat saji")** teaching
example (e.g. `Dapur & Tim Koki`, `Menyajikan Pesanan`, `Pelanggan Restoran`) —
deliberately separate from the Bank Wanua case — so keep extending that same
restaurant example into new layers.

---

## 2. Hard rules

1. **Edit the model ONLY through the `archi` MCP server.** Never edit
   `models/session-07.archimate` directly (it is open in a live Archi instance at
   `http://127.0.0.1:18090/mcp`). Native tools are `mcp__archi__*`; if they are
   not loaded in-session, drive the same server over MCP HTTP/SSE with a tiny
   Python client (see §7).
2. **Keep everything consistent with the running case study** and with the layer
   above (cross-layer traceability — see §5).
3. **Verify visually.** Export each view to PNG and actually look at it; aim for
   `assess-layout` rating *good*/*excellent* before exporting final PDFs.
4. **Compile before declaring done** (book + slides), and check 0 undefined refs.

---

## 3. Repo map & conventions

- `module/chapterNN.tex` — book chapters. Root = `module/enterprise-platform-architecture.tex`
  (`\include`s chapter01..NN). `\graphicspath{{../figures/}}`. Engine: **xelatex**
  via `latexmk -xelatex`.
- `slides/sessionNN/sessionNN.tex` — Beamer, `\usetheme{Pradita}` (theme in
  `slides/theme/`; custom colors `praditagreen`, `blueColor`).
  `\graphicspath{{../theme/}{../../figures/}}`. Weekly dates: session01 = 30 Mei
  2026, +7 days each → session04 = 20 Juni, **session05 = 27 Juni 2026**, etc.
  Slide title style (current): `Lapisan <X>\\ \vspace{8pt} pada ArchiMate`.
- `figures/` — Archi exports, **both** `.pdf` (included by tex) and `.svg`.
  Naming: `<layer>-legend.{pdf,svg}` (notation legend), `<layer>-transfer.{pdf,svg}`
  (primary case-study diagram), `<layer>-contoh.{pdf,svg}` (the `Contoh
  Komprehensif` per-element example), optional `<layer>-overview/-asis/-tobe.{pdf,svg}`.
  `<layer>` ∈ {motivation, strategy, business, application, technology, implementation}.
- `models/session-07.archimate` — the single model (all layers live here).

### View naming convention (match existing)
- `"<Layer> - API Transfer Dana"` — main/overview case-study view.
- `"Legenda Notasi <Layer>"` — notation legend (one element named after each type).
- `"<Layer> - <Theme>"` — thematic split views (the "separate into several views"
  ask). E.g. business used: *Aktor & Peran*, *Proses Transfer Dana*, *Fungsi &
  Layanan*, *Objek Informasi*, *Penyelarasan ke Strategi*.
- Teaching views also exist: `"Contoh <Layer> - N. <ElementType>"`,
  `"Contoh Komprehensif - <Layer>"`, `"Contoh Cross-Layer - ..."` (optional; only
  if the user asks for per-element teaching views).

### Folder ids (re-fetch with `get-folders` to be safe — ids can change)
```
Strategy        id-bcd219967cea4b61b49a1e3e3f684b7c
Business        id-399f62ee9a50424f89be4b1dfe3f7cde
Application     id-ebe6c990642d402eb5e9515cf252a914
Technology      id-45817f853f7b4576989c519fd910bdf4
Implementation  id-40f41ebc1dfd423d8dcc2e4eabfd3edc
Motivation      id-c4956eae965e46c6a884d9a2cd0226d1
Views (diagrams) id-91db20392fa3419896b2d350fe96283f
```
Put new elements in their layer folder via `folderId`.

---

## 4. TOGAF ADM phase per layer (each chapter adds a phase subsection)
- A — Vision → Strategy (`chapter03`, done)
- **B — Business Architecture** → Business (`chapter04`, done)
- **C — Information Systems** → **Data** (`chapter05`, done) + **Application** (`chapter06`, done)
- **D — Technology Architecture** → Technology chapter (`chapter07`, done)
- **E/F — Opportunities & Solutions / Migration Planning** → Implementation chapter (`chapter08`, next)

Each chapter gets a `\subsection{TOGAF ADM Fase <X>: ...}` with a
baseline→target→gap table mapped to Bank Wanua (see `chapter04.tex` Fase B as the
template).

---

## 5. Cross-layer links (keep the model coherent)
Each new layer realizes/derives from the one above. Reuse existing element ids
(find them with `search-elements`, `{"query":"","layer":"Business"}`):
- **Application → Business:** ApplicationService **realizes** BusinessService;
  ApplicationComponent **assigned to** ApplicationService / **serves**
  BusinessProcess; DataObject **realizes** BusinessObject.
- **Technology → Application (canonical deployment — verified against the Open
  Group ArchiMate spec):** Node **assigned to** (deploys) an **Artifact**; the
  **Artifact realizes** the ApplicationComponent *and* **realizes** the DataObject
  (a component is realized by an artifact and, indirectly, by the node that deploys
  it). Node **realizes** its TechnologyService; **TechnologyService serves**
  ApplicationComponent/Function — this is the *only* valid technology→application
  serving. CommunicationNetwork **associated with** Node.
  **Do NOT** use `Node -> Serving -> ApplicationComponent` or `Node -> Assignment ->
  ApplicationComponent` (non-canonical; Archi rejects the assignment) — route
  through an Artifact (deploy) or a TechnologyService (serve) instead.
- **Implementation → all:** WorkPackage **realizes** Plateau/Deliverable;
  Gap; relate to Capabilities/Courses of Action (strategy) and the target architecture.

Anchor business element names you'll likely link to: services *Layanan Transfer
Dana / Penyaringan Kepatuhan / Notifikasi & Status / Rekonsiliasi*; objects
*Instruksi Transfer / Hasil Penyaringan / Catatan Transaksi / Catatan
Rekonsiliasi / Rekening Nasabah / Notifikasi Status*; the 6 processes; the 4
functions. Strategy capabilities: *Pembayaran Real-time 24/7*, *Kepatuhan & AML
Otomatis*, *Manajemen API sebagai Produk*; value stream *Eksekusi Transfer Dana*.

---

## 6. Step-by-step playbook for the NEXT layer

> Align element names with the corresponding chapter first. Read the matching
> chapter's "Studi Kasus" + concept sections (as was done by reading `chapter04`
> before building Business). If the chapter doesn't exist yet, draft the model
> from the case study and the layer above, then write the chapter to match.

1. **Confirm scope** with the user if ambiguous (e.g. Data vs Application split).
2. **Create elements** (idempotent `get-or-create-element`, correct `type` +
   layer `folderId`). Typical Application types: `ApplicationComponent`,
   `ApplicationService`, `ApplicationInterface`, `ApplicationFunction`,
   `ApplicationCollaboration`, `DataObject`. Technology: `Node`, `Device`,
   `SystemSoftware`, `TechnologyService`, `Artifact`, `CommunicationNetwork`,
   `Path`. Implementation: `WorkPackage`, `Deliverable`, `Plateau`, `Gap`.
3. **Create relationships** with a fallback chain per edge (try the precise
   ArchiMate type, then `Association` as a guaranteed-valid fallback). The server
   enforces ArchiMate rules and returns valid alternatives on error. Learned-valid
   patterns: actor→role/role→process = Assignment; process composition/triggering;
   process/function→service = Realization; service→actor = Serving;
   interface→service = Assignment; process→object = Access (set `accessType`
   read/write); product→service/contract = Aggregation; **function→capability and
   process→valuestream = Realization (cross-layer)**.
   *Note:* CourseOfAction→Capability only accepts **Association** (not Realization).
4. **Build several views** (legend + overview + thematic splits). For each view:
   `create-view` → `add-to-view` with explicit x/y/w/h (grid, align connected
   pairs to minimize crossings; nest sub-elements with `parentViewObjectId`) →
   `auto-connect-view` (optionally `relationshipTypes` filter to drop clutter like
   composition when nesting already shows it) → `auto-route-connections` →
   `assess-layout` → `export-view` PNG and **look at it**. Iterate positions until
   tidy. Legend = one element per type named after the type, in a grid (no edges).
5. **Export figures**: `export-view` (format pdf, then svg, `inline:false`,
   `outputDirectory` = `figures/`) and rename to `<layer>-legend/-transfer/-overview.{pdf,svg}`.
6. **Write/extend the chapter** mirroring `chapter02/03/04`:
   - In *Konsep Inti*: `\subsection{Notasi Elemen Lapisan <Layer> di Archi}` →
     legend `\includegraphics` + element table (`tab:<layer>-elements`), then a
     `\subsection{Contoh Interaksi Antar-Elemen <Layer>}` embedding the
     `<layer>-contoh.pdf` comprehensive example (`fig:<layer>-contoh`).
   - A `\subsection{TOGAF ADM Fase <X>: ...}` with a baseline→target→gap table
     (for Business this is Fase B; embed the `-asis`/`-tobe` figures here).
   - In *Studi Kasus*: `\subsection{Model <Layer> ... di Archi}` with the
     diagram(s) + `\subsubsection{Cara Membaca Diagram <Layer>}` walkthrough.
   - Labels: `fig:<layer>-legend/-transfer/-contoh`, `tab:<layer>-elements`,
     `tab:adm-phase-<x>`. Add a learning objective bullet for the ADM phase.
7. **Build the slides** `slides/sessionNN/sessionNN.tex` by copying `session04` as
   the template: same preamble/theme/`\sectionframe`/`\takeaway`, title
   `Lapisan <X>\\ pada ArchiMate`, next weekly date, ~8 sections mirroring the
   chapter, embed `<layer>-legend` + the diagrams. Also include: (a) a full-bleed
   **`<layer>-contoh.pdf`** example frame after the "Elemen" section, and (b) the
   reusable **"Siklus TOGAF ADM"** wheel frame (copy verbatim from `session02`;
   overlay-highlight the current phase node + bold its legend bullet). Full-bleed
   diagram frames: `\includegraphics[width=\textwidth,height=.84\textheight,keepaspectratio]`.
   **Spacing rule (user):** put a blank line after every `\end{tikzpicture}`/
   `scalebox` closing `}` that is followed by text (e.g. `\takeaway`) so the text
   doesn't butt against the figure.
8. **Compile & verify** (see §8). Then update the Status table in this file.

---

## 7. MCP cheatsheet

Native tools are `mcp__archi__<name>` (load schemas via ToolSearch
`select:mcp__archi__get-model-info,...`). Key ones:
`get-model-info, get-folders, get-views, get-view-contents, search-elements,
search-relationships, get-or-create-element, create-element, create-relationship,
create-view, add-to-view, add-note-to-view, auto-connect-view (has
relationshipTypes filter), auto-route-connections, assess-layout, export-view,
clear-view, bulk-mutate (≤150 ops, supports $N.id back-references)`.

`bulk-mutate` is the fastest native path: create elements + relationships + view +
add-to-view + connections in atomic batches using `$N.id` back-references; use
`continueOnError:true` and retry any rejected relationship with a fallback type.

If `mcp__archi__*` are not loaded in the session, recreate a tiny HTTP/SSE client
(this worked well for the Strategy & Business builds). Endpoint
`http://127.0.0.1:18090/mcp`; flow = initialize (capture `mcp-session-id` header)
→ `notifications/initialized` → `tools/call`. Tool results come back as
`result.content[0].text` (a JSON string). A scripted build (create elements →
capture ids → create relationships with fallbacks → build views with positions →
auto-connect/route → export) is the reliable pattern for this scale. (`/tmp`
helper scripts are ephemeral — recreate as needed.)

---

## 8. Verification checklist (run every time)
- Book: `cd module && latexmk -xelatex -interaction=nonstopmode -halt-on-error enterprise-platform-architecture.tex`
  → exit 0; `grep "Graphic file" ...log` shows the new figures; new labels appear
  in `chapterNN.aux`; `grep -c "LaTeX Warning: Reference" ...log` = 0.
- Slides: `cd slides/sessionNN && latexmk -xelatex -interaction=nonstopmode -halt-on-error sessionNN.tex`
  → exit 0; render a couple of pages with `pdftoppm` and eyeball the diagrams fit.
- Model: `assess-layout` good/excellent on each view; `get-model-info` layer counts
  increased as expected.
- Do **not** `git commit` unless the user asks.

---

## 9. Useful references
- Element-type & relationship rules: MCP resources `archimate://reference/archimate-layers`.
- Templates to copy: `module/chapter04.tex` (chapter structure, Fase B table,
  legend table, Cara Membaca), `slides/session04/session04.tex` (deck),
  `figures/business-*.{pdf,svg}` (figure style).
