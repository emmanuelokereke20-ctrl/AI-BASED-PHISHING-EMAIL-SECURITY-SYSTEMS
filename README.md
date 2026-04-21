# EU AI Act Requirements Graph — Interactive Visualisation

## Overview

An interactive, force-directed graph visualisation of the EU AI Act requirements for **providers of High Risk AI Systems**, scoped to **AI-Based Phishing & Email Security Systems** (Proofpoint TAP/VAP — Automation Artefact 4).

The graph maps the relationships between Articles 9–18 and Article 51 of the EU AI Act, exposing how provider obligations (Art. 16), quality management requirements (Art. 17), core Chapter 2 requirements (Arts. 9–15), conformity documentation (Art. 18), and registration (Art. 51) interconnect.

---

## Features

| Feature | Description |
|---|---|
| **Force-directed layout** | Nodes repel/attract via D3 v7 physics simulation |
| **Interactive sidebar** | Click any node to see its Article, CRE reference, outgoing/incoming links, and a direct link to the EU AI Act text |
| **Drag to reposition** | Nodes can be freely repositioned |
| **Zoom & pan** | Scroll/pinch to zoom; drag canvas to pan |
| **Article filter pills** | Show/hide nodes by Article number (9–18, 51) |
| **Relation filter pills** | Show/hide edges by type: `REQUIRES`, `RELATED_TO`, `TO_INCLUDE`, `SEE_ALSO` |
| **Live search** | Find nodes instantly by label or node ID |
| **Reset button** | Restores all filters and zoom to default |

---

## Graph Data

### Node groups

| Colour | Article(s) | Topic |
|---|---|---|
| 🟠 Orange | Art. 16 | Provider obligations |
| 🟢 Green | Art. 17 | Quality management system contents |
| 🟣 Pink | Arts. 9–15 | Core High Risk requirements (Chapter 2) |
| 🟡 Yellow | Art. 13 sub-reqs | Transparency & use-instructions detail |
| 🔴 Red | Art. 18 | Conformity documentation |
| 🔵 Blue | Art. 51 | Registration |

### Edge types

| Type | Meaning |
|---|---|
| `REQUIRES` | Hard obligation — one article mandates another |
| `TO_INCLUDE` | Enumerates required contents of a system/document |
| `RELATED_TO` | Semantic cross-reference |
| `SEE_ALSO` | Informational pointer (dashed line) |

---

## Getting Started

### Option 1 — Google Colab (recommended)

1. Open [Google Colab](https://colab.research.google.com/)
2. Go to **File → Upload notebook** and select `Untitled0.ipynb`
3. Run the single cell (Shift+Enter)
4. The interactive graph renders inline — no installs required

### Option 2 — Local Jupyter

```bash
pip install notebook        # or jupyterlab
jupyter notebook AI-BASED_PHISHING_EMAIL_SECURITY.ipynb
```

Run the cell; the graph renders via `IPython.display.HTML`.

---

## Requirements

All dependencies are either part of the Python standard library or available in the default Google Colab / Jupyter runtime. See `requirements.txt` for details.

The D3.js v7 library is loaded at runtime from the Cloudflare CDN:

```
https://cdnjs.cloudflare.com/ajax/libs/d3/7.8.5/d3.min.js
```

An active internet connection is required for the graph to render.

---

## File Structure

```
.
├── AI-BASED_PHISHING_EMAIL_SECURITY.ipynb    # Main notebook — single self-contained cell
├── README.md          # This file
└── requirements.txt   # Python dependencies
```

---

## Regulatory Context

| Regulation / Standard | Relevance |
|---|---|
| EU AI Act (2024/1689) | Primary legislation — Articles 9–18, 51 |
| ENISA CRE | Node CRE identifiers map to ENISA Common Requirements |
| NHS DSPT / UK GDPR | Deployment context (NHS AI-based email security) |
| Proofpoint TAP/VAP | Example High Risk AI system in scope |

---

## Author Notes

- The notebook is a **Colab-compatible rewrite** of an original `yfiles-jupyter-graphs` notebook, replacing the proprietary yFiles widget with a self-contained D3 v7 implementation requiring no additional installs.
- Graph data (nodes and edges) is embedded directly in the Python cell and serialised to JSON for the D3 rendering layer.
- The visualisation is entirely self-contained within the output HTML — no server, no Flask, no external data files.
