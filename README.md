# Egonomy — Project Page

Static project page for **Egonomy: Scaling and Transferability Laws of Human-Robot Co-training**, modeled on the [WoGNet](https://selen-suyue.github.io/WoGNet/) page (Bulma + carousel + Fancybox).

## Local preview

```bash
cd /Users/bytedance/Desktop/Egonomy_project_page
python3 -m http.server 8765
# then open http://localhost:8765/
```

## File layout

```
.
├── index.html             # the page (single file, edit me)
├── static/
│   ├── css/               # bulma + carousel + slider + fontawesome + index.css
│   └── js/                # bulma-carousel + bulma-slider + index.js + fontawesome
└── img/                   # all PNGs used on the page (converted from paper PDFs)
```

## What to fill in before publishing

1. **Links in the hero buttons.** In `index.html` search for `class="external-link button is-normal is-rounded ego-button"` and replace `href="#"` with the real URLs for `paper`, `arXiv`, `code`, and `data`.
2. **Author homepage links.** Replace `href="#"` on each `<a>` inside the `publication-authors` block.
3. **Add videos (optional).** WoGNet uses a video carousel. To add one, copy the `#results-carousel` block from WoGNet's `index.html` and point `<source src="…">` at MP4s placed under a sibling `video/` folder.
4. **arXiv ID for the BibTeX.** Replace `arXiv preprint` in the `<pre>` block once the paper is on arXiv.
5. **Logos.** `img/seed_logo.png` and `img/hku_logo.png` were copied from the LaTeX project. Add a Zhejiang University logo if desired.

## How figures were generated

PDFs from the paper were rasterized to PNG with PyMuPDF (220 DPI for hero figures, 200 DPI for grid figures). To regenerate after editing the paper figures, re-run `convert_pdfs.py` (kept under `/tmp/convert_pdfs.py` during build).

## Confidentiality cleanup

To respect the company NDA, the page only shows figures that are actually included in the active main text or appendix of the paper. The following figures were **excluded** because they are commented out or never cited in `paper.tex`:

- `data_demos_v2.pdf` (Human Data Spectrum overview — `% \begin{figure} ... \end{figure}` at L237–L242)
- `UMI-based data_v1.pdf` / `egoumi_v0.pdf` / `egoumi_v1.pdf` (UMI rig diagram — commented out at L413–L418, never cited)
- `model_arch_v1.pdf` (model architecture — commented out at L519–L527)
- `long_context_v0.pdf` (history-window ablation — commented out at L1144–L1156)
- `scaling_v1.pdf` (never cited — only `succ_scaling_v1.pdf` and `loss_scaling_v2.pdf` are used)
- `fail.pdf` (never cited)
- `teaser_v0.pdf` / `teaser_draft*.png` / `robotwin_success_rate_shaded.png` (drafts / superseded)

If a figure later gets uncommented in the paper, regenerate the matching PNG and re-add it to `index.html`.

## Style notes

- Title font: `M PLUS Rounded 1c` (chunky rounded display).
- Body font: `Noto Sans` / `Arial`.
- Color tokens (matching WoGNet):
  - `#5E7FA8` — blue, used for technical concepts/highlights and link hover.
  - `#ca6f6f` — warm red, used for the **Egonomy** word, button hover, and the paper's name in body text.
- Carousels: `bulma-carousel` with 2 slides visible, autoplay on, navigation buttons themed to the blue/red palette.
- Image lightbox: `@fancyapps/ui` Fancybox 5 (click any figure to enlarge).
- Easter egg: clicking the 🤖 in the title toggles a tiny rocking animation (no audio, unlike WoGNet's snowboard 🏂 + bgm).
