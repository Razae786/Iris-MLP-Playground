# Design System: Iris Neural Playground
**Project ID:** iris-mlp-playground-v1
**Design Language:** Scientific Linear-Dark / Google Research Inspired
**Specification Source:** awesome-design-md / VoltAgent

---

## 1. Atmosphere & Spatial Rhythm

### Visual Atmosphere
The interface embodies a **Calm, High-Precision Scientific Instrument** aesthetic. It takes cues from Google's TensorFlow Playground and Linear's dark UI:
* **Background Atmosphere:** Deep space slate (`#090d16` canvas with subtle radial illumination).
* **Card Elevation:** Solid dark obsidian cards (`#111827`) encased in hairline border lines (`#1f293d`) with soft diffusion (`shadow-xl shadow-black/40`).
* **Visual Density:** Information-dense yet breathing, using an 8pt/16pt spatial cadence (`p-4`, `p-6`, `gap-4`, `gap-6`).
* **Border Radii:** Consistent geometry — `rounded-2xl` (16px) for cards, `rounded-xl` (12px) for canvases and control modules, `rounded-full` for status chips and primary action triggers.

---

## 2. Calibrated Color Palette

| Color Token | Hex Value | Natural Language Description | Functional Role |
| :--- | :--- | :--- | :--- |
| **Surface Dark** | `#090d16` | Obsidian Night Canvas | Page-level background |
| **Card Surface** | `#111827` | Deep Graphite Card Base | Primary container background |
| **Card Border** | `#1f293d` | Crisp Slate Hairline | Visual container separation |
| **Primary Accent**| `#38bdf8` | Radiant Electric Cyan | Active controls, excitatory weights, primary labels |
| **Class 0 (Setosa)** | `#14b8a6` | Luminous Mint Teal | Setosa territory, scatter points, probability bar |
| **Class 1 (Versicolor)**| `#f59e0b` | Vibrant Solar Amber | Versicolor territory, inhibitory weights, train loss |
| **Class 2 (Virginica)** | `#a855f7` | Royal Neon Purple | Virginica territory, validation loss |
| **Text Primary** | `#f8fafc` | Pure Alpine White | Primary headers, numeric figures |
| **Text Secondary**| `#94a3b8` | Muted Cool Fog | Labels, metrics descriptions, column tags |
| **Text Monospace**| `#38bdf8` | Terminal Cyan | Numeric weights, activations, epoch counts |

---

## 3. Typographic Hierarchy

* **Hero Display:** `text-xl md:text-2xl font-bold tracking-tight text-slate-100` — Clean product name without academic fluff.
* **Section Headers:** `text-xs uppercase tracking-widest font-semibold text-slate-400` — Terminal-style section labels.
* **KPI Metrics:** `text-2xl font-black font-mono tracking-tight text-slate-100` — Bold empirical figures.
* **Micro Labels:** `text-[11px] font-mono text-slate-400` — Canvas headers, synapse values, axis markers.

---

## 4. Interactive Data Visualization Standards

1. **No Static Illustrations:** All neural weights, activations, and decision borders compute in real time via live backpropagation.
2. **Interactive Hover Tooltips:** Inspecting any synapse reveals exact float values ($w_{ij} \in [-2.5, +2.5]$); inspecting any flower sample displays true sepal/petal measurements.
3. **High-Contrast Boundary Rendering:** Softmax exponentiation with power-weighted alpha prevents muddy gray intersections, generating vivid topological decision zones.
4. **EarlyStopping Telemetry:** A crimson dashed line dynamically indicates the exact validation minimum rollback point ($t_{\text{best}}$).
