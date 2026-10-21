<p align="center"><img src="logo.svg" width="110" alt="PopSeqViz2 logo"></p>

# PopSeqViz2

PopSeqViz2 (formerly TreeViz) is an interactive phylogenetic tree viewer and editor. It shows the tree together with sample metadata and **population allele-frequency data**, all in one offline web page. There is nothing to install and no server.

**Try it:** open `index.html` in Chrome or Edge, or double-click `PopSeqViz2.bat` on Windows. If GitHub Pages is turned on, the same page runs at the repository's Pages URL. Your data files are read inside the browser and are never uploaded.

## Features
- **Tree files:** Newick, NEXUS (with translate tables) and PhyloXML. You can also paste a tree or drag and drop files onto the page.
- **Layouts:** rectangular, slanted, circular and radial (unrooted).
- **Branch lengths:** phylogram or cladogram, log1p/sqrt transform, cap on very long branches, and short-branch boost.
- **Editing (FigTree-style):**
  - **Rooting:** one Reroot panel — on the selected branch (choose the position), at the MRCA of selected tips, on an outgroup typed by name (text or /regex/), or at the midpoint.
  - **Structure:** collapse, flip, mirror, ladderize, prune, keep only selected tips, or make a subtree the root.
  - **Labels and colours:** rename tips and nodes, set branch lengths, colour branches or clades, highlight clades, and add clade labels.
- **Going back:** undo/redo, restore the original tree, auto-saved last session, named checkpoints, and save/open sessions as `.json` files.
- **Metadata (CSV / TSV / XLSX):**
  - **Display:** metadata columns as tip labels, coloured dots, and tip colours.
  - **Numbers:** number columns get a colour gradient, with a log-scale option.
  - **Missing values:** tips with no value can take it from the matching population sample (same Person + week + BodySite).
- **Population frequency table:** this uses the same long format as PopSeqViz.
  - **Columns:** `Sample, node, true_pos, relative_pos, derived_allele, derived_allele_frequency, depth, A, C, G, T, in_lofreq_vcf`, plus optional `row_type` and `summary_*` columns.
  - **Display:** per-position frequency bars on each named branch, value badges, or branches coloured by frequency.
  - **Bar placement:** on the branch where the SNPs arose (`child_node`) or on the parent node (PopSeqViz style); histogram mode for many sites.
  - **Filters:** shared positions, LoFreq support, minimum depth, minimum frequency, include/exclude positions, and hide nodes by parent node or by child node.
  - **Sample table:** one-line filter bar (Person / week / BodySite / type dropdowns + search) that can be minimised after choosing; click a sample name to show just that sample.
- **Layout:** the side options panel can be hidden (☰ button or Ctrl+B), and all its sections expanded/collapsed at once.
- **Colour scales:** Viridis, Turbo (high contrast), Orange–Purple, Plasma, Blues, Reds, Greens, Blue–Green–Red, with no near-white ends so low values stay visible.
- **Export:** SVG, PNG (3×), Newick, FigTree NEXUS with branch colours, the tip table and the frequency rows (CSV).

## Repository layout
| Path | What it is |
|---|---|
| `index.html` / `PopSeqViz2.html` | The complete app (one self-contained file) |
| `PopSeqViz2.bat` | Windows launcher that opens the app in its own Edge/Chrome window |
| `source/` | Source code. `src/` holds the source; `build.py` combines it into `PopSeqViz2.html` |
| `TreeViz.html` | Redirect so old TreeViz links still open the app |
| `streamlit_app/` | Earlier Streamlit version (`pip install -r requirements.txt` then `streamlit run app.py`) |

## Acknowledgements
- The population-frequency display follows the design of [PopSeqViz](https://github.com/tfursten/popseq_viz) by T. Furstenau.
- Excel reading uses [SheetJS Community Edition](https://sheetjs.com) (Apache-2.0), which is bundled inside the HTML file.
