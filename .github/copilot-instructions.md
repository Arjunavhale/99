<!-- .github/copilot-instructions.md -->
# Copilot / AI agent instructions for this repository

Purpose: Help an AI coding agent be immediately productive editing and building this JupyterBook-based portfolio.

High-level (big picture)
- This repo is a Jupyter Book site (MyST) configured for a course portfolio. Key content lives under `Content/` (e.g. `Content/PySim/` notebooks and explanatory markdown).
- Configuration is at the repo root: `myst.yml` (project metadata + extends), `toc.yml` (site table-of-contents), `plugins.yml` (external Jupyter-Book plugins), and `export.yml` (export targets).
- Static assets: `Figures/` (images, favicon, logo) and `css/` (site CSS: `TUD_stylesheet.css`, `custom.css`).
- There is a nested copy of the project under `Project/99/`. Treat the repository root as canonical; do not edit the nested copy unless explicitly requested.

How to build & serve locally (developer workflow)
- Create and activate a Python venv, then install requirements from the repo root:
  - PowerShell example:
    - `python -m venv .venv; .\.venv\Scripts\Activate.ps1; pip install -r requirements.txt`
- Build the site with Jupyter Book from the repository root:
  - `jupyter-book build .`
  - Output HTML is in `_build/html` by default.
- Serve the built site locally (PowerShell):
  - `python -m http.server --directory _build/html 8000`
- To work interactively with notebooks: `jupyter lab` or `jupyter notebook` from the repo root after installing `ipykernel`.

Key files and where to make changes (examples)
- To add or edit pages:
  - Markdown pages: edit `index.md`, `intro.md` or files under `Content/`.
  - Notebooks: edit files under `Content/PySim/` (e.g. `3_recap.ipynb`).
- To change navigation: update `toc.yml`. Example: to add a new PySim notebook, add a `- file: Content/PySim/<name>.ipynb` entry under the `Simulaties` section.
- To change visual style: edit `css/TUD_stylesheet.css` (site uses that file via `myst.yml`).
- To add images or logos: put files under `Figures/` and reference them from markdown or `myst.yml` (logo, favicon are referenced there).

Project-specific patterns & gotchas
- `myst.yml` uses `extends:` to include `plugins.yml`, `toc.yml`, and `export.yml`. Plugins declared in `plugins.yml` are external JS modules fetched at build time — builds require network access (or vendor these resources).
- `export.yml` declares an export format using `typst`. Exporting may require additional tooling (typst or custom templates) beyond Python packages listed in `requirements.txt`.
- There are duplicate `requirements.txt` files (root and `Project/99/requirements.txt`) with the same content. Edit the root file primarily.
- Keep author and repository URL metadata in `myst.yml` up to date (it contains the `github:` and `actions:` links).

Examples (concrete edits an agent might do)
- Add a new notebook to the site:
  1. Place `Content/PySim/5_new_experiment.ipynb` in the folder.
  2. Add `- file: Content/PySim/5_new_experiment.ipynb` to `toc.yml` under `Simulaties`.
  3. Run `jupyter-book build .` and verify the page appears at `_build/html/`.
- Update CSS variables used by the theme: edit `css/TUD_stylesheet.css` and rebuild.

What not to change / edit caution
- Don’t change the `Project/99/` subtree — it's a nested copy and can cause merge confusion.
- Plugins listed in `plugins.yml` are external URLs; removing or changing them may break site features. If replacing, vendor the JS and update `myst.yml` accordingly.

If you need more context
- Read `README.md` at the repo root for the project purpose and licensing.
- Look at `toc.yml` for navigation patterns and `myst.yml` for site-level options (template, style, folders flag).

Feedback request
- If any section is unclear or you want more details (build CI, GitHub Pages publishing steps, or common editorial rules), tell me which area to expand.

-- End of copilot instructions
