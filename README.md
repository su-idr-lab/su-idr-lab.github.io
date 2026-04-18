# IDR Lab Website

Source for the **Intelligent Design and Robotics Lab (IDR Lab)** website, deployed as the GitHub Pages organization site for [`su-idr-lab`](https://github.com/su-idr-lab).

- **Live site:** <https://su-idr-lab.github.io/>
- **Repository:** [`su-idr-lab/su-idr-lab.github.io`](https://github.com/su-idr-lab/su-idr-lab.github.io)
- **PI:** Prof. Hai-Jun Su, The Ohio State University

The site is a hand-authored static site (HTML + CSS, no build step) served directly by GitHub Pages from the `main` branch.

## Site structure

### Top-level pages

| File | Purpose |
| --- | --- |
| `index.html` | Home — lab intro, research highlights, news |
| `people.html` | Lab members, alumni, collaborators |
| `research.html` | Research overview (landing page for the themes) |
| `publications.html` | Publications by year, plus Recent Publication Figures grid |
| `software.html` | Software packages released by the lab |
| `courses.html` | Courses taught by the PI |
| `join.html` | Prospective-student information |

### Research-theme pages

Each research theme has a dedicated page sharing the `research.html` sidebar layout:

- `research-machine-design-automation.html`
- `research-compliant-soft-robotics.html`
- `research-robot-mechanism-design.html`
- `research-mixed-reality-simulation.html`
- `research-embodied-ai.html`
- `research-computational-kinematics.html`

### Software sub-pages

Individual software packages (linked from the `software.html` sidebar):

- `software-spherical-4r.html`
- `software-camgenius.html`
- `software-das.html`
- `software-magicdna.html`
- `software-vrmds.html`
- `software-synthetica.html`

### Course pages

- `courses-me5751.html`
- `courses-me7751.html`

### Per-paper project pages

Project pages live under `projects/<slug>/` and follow a shared template (title, authors, venue, resource links, figure grid, abstract, results, BibTeX):

- `projects/robot_ik_LLM/` — 2026 *Mechanism and Machine Theory* paper on LLM-assisted analytical inverse kinematics solvers for 6R manipulators.
- `projects/parallelogram_model_comparison/` — 2026 paper (under review at *ASME Journal of Mechanisms and Robotics*) on an open-source hierarchical multi-fidelity modeling stack for compliant mechanisms.

Each project folder contains its own `index.html`, an `images/` subfolder with extracted figures, and (where applicable) the preprint PDF.

### Assets

- `assets/css/style.css` — single site stylesheet (Manrope body, Newsreader display).
- `assets/images/` — shared hero images, research-figure thumbnails, software screenshots.
- `logos/IDRLab_logo2_small_v2.png` — site favicon and header brand mark.

## Local preview

No build step is required. From the repository root:

```bash
python -m http.server 8000
```

then open <http://localhost:8000/>. Any static server works.

## Deployment

Pushes to `main` are published automatically by GitHub Pages (configured to serve from the `main` branch root).

1. Make changes on `main` (or a feature branch merged into `main`).
2. Commit and push.
3. GitHub Pages rebuilds within ~1 minute; verify at <https://su-idr-lab.github.io/>.

## Adding a new publication

1. Add the bibliographic entry under the appropriate year section in `publications.html`, following the `article.publication-entry` pattern (title, authors, venue, resource-link pills).
2. If the paper deserves a dedicated page, create `projects/<slug>/` using an existing project page as a template. Place extracted figures in `projects/<slug>/images/` and (optionally) the preprint PDF in the same folder.
3. Add a "Project page" link to the publication entry in `publications.html`.
4. If the figure should appear in the "Recent Publication Figures" grid on `publications.html`, copy a representative thumbnail into `assets/images/research/` and add a `recent-figure-link` tile pointing at the project page.
5. If the work deserves a home-page callout, add a News bullet to `index.html` (latest on top) and optionally update the Research Highlights card.

## Ignored files

See [`.gitignore`](.gitignore). Local preview/scratch artifacts (`.preview-http.*.log`, `.scholar*.html`, `.omx/`) and editor metadata (`.vscode/`, `.idea/`, OS detritus) are excluded.
