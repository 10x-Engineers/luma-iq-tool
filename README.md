# luma-iq-tool
Premium integrated IQ analysis workbench for ISP tuning, YAML-native pipeline editing, and automated image quality evaluation
<div align="center">

<img src="https://10xengineers.ai/wp-content/uploads/cropped-square-logo-270x270.png" width="80" alt="10xEngineers Logo"/>

# LumaIQ

### ISP Analysis Platform · Part of the 10xEngineers Imaging Suite

**ISP-Native · HDR-Aware · Pipeline-Integrated**

[![Platform](https://img.shields.io/badge/Platform-Windows%20%7C%20Linux-blue.svg)](#)
[![Built With](https://img.shields.io/badge/Built%20With-PyQt6%20%7C%20NumPy%20%7C%20OpenCV-informational.svg)](#)
[![RAW Formats](https://img.shields.io/badge/RAW%20Formats-13%2B-green.svg)](#format-support)
[![HDR](https://img.shields.io/badge/HDR-Native%20Support-orange.svg)](#hdr-integration)
[![No Cloud](https://img.shields.io/badge/Deployment-Offline%20%7C%20No%20Subscription-lightgrey.svg)](#)
[![Price](https://img.shields.io/badge/Starting%20From-USD%204%2C000-purple.svg)](https://10xengineers.ai/contact-us/)

[🧪 Try with Your RAW Data](https://10xengineers.ai/contact-us/) · [🌐 Website](https://10xengineers.ai/lumaiq/) · [📬 Contact](https://10xengineers.ai/contact-us/)

</div>

---

## Overview

**LumaIQ** is an integrated Image Quality (IQ) analysis workbench built specifically for ISP algorithm engineers. It replaces fragmented scripts, disconnected tools, and manual YAML edits with a single, cohesive environment — cutting tuning loops from hours to minutes.

> _"Every feature exists because an ISP engineer needed it during tuning — not because a product manager needed a checkbox."_

Built on **PyQt6, NumPy, SciPy, and OpenCV**. Runs natively on **Windows and Linux**. No cloud dependency, no subscription lock-in.

---

## ⚡ At a Glance

| | |
|---|---|
| **Platform** | Windows · Linux (native desktop) |
| **Pipeline** | YAML-native · full collapsible per-stage editor |
| **HDR Support** | Native — dual-exposure · LTM · tone mapping |
| **Batch Runs** | GUI + CLI — CSV-driven overnight regression |
| **Reports** | Auto-generated self-contained HTML, base64-embedded charts |
| **Presets** | Tuning Vault — named preset CRUD across sessions |
| **UI Thread** | Never blocked — all processing in background QThreads |
| **ColorChecker** | 24 patches · CIE76 · CIE94 · CIEDE2000 ΔE |
| **RAW Formats** | 13+ formats including headerless sensor dumps |
| **Starting Price** | USD 4,000 |

---

## �� Workflow Diagram

### The Problem: Fragmented Tuning Loop

```
┌─────────────────────────────────────────────────────────────────────┐
│                   CURRENT (FRAGMENTED) WORKFLOW                      │
│                                                                       │
│  ┌──────────────┐     ┌──────────────┐     ┌──────────────────────┐ │
│  │  1. Capture  │     │  2. Edit     │     │  3. Run Python       │ │
│  │  RAW frame   │────▶│  YAML by     │────▶│  ISP script          │ │
│  │  on hardware │     │  hand        │     │  (one person knows   │ │
│  │              │     │  (800 lines) │     │   how it works)      │ │
│  └──────────────┘     └──────────────┘     └──────────┬───────────┘ │
│                                                        │             │
│  ┌──────────────┐     ┌──────────────┐     ┌──────────▼───────────┐ │
│  │  6. Repeat ◀─┼─────┼─ 5. Copy     │◀────┤  4. Export PNG →    │ │
│  │  from step 2 │     │  numbers to  │     │  open Imatest        │ │
│  │              │     │  Excel       │     │  (switch tools,      │ │
│  │  ≈ 3 weeks   │     │  (broken     │     │   lose context)      │ │
│  │  per cycle   │     │   twice/qtr) │     │                      │ │
│  └──────────────┘     └──────────────┘     └──────────────────────┘ │
└─────────────────────────────────────────────────────────────────────┘
```

### The Solution: LumaIQ Integrated Loop

```
┌─────────────────────────────────────────────────────────────────────┐
│                      LUMAIQ — ONE INTEGRATED LOOP                    │
│                                                                       │
│  ┌──────────────┐     ┌──────────────┐     ┌──────────────────────┐ │
│  │  1. Load     │     │  2. Load     │     │  3. Run ISP          │ │
│  │  RAW file    │────▶│  YAML config │────▶│  pipeline            │ │
│  │  .nef .arw   │     │  Collapsible │     │  Background thread   │ │
│  │  .raw .dng   │     │  per-stage   │     │  UI stays responsive │ │
│  └──────────────┘     │  editor      │     └──────────┬───────────┘ │
│                        └──────────────┘               │             │
│  ┌──────────────┐     ┌──────────────┐     ┌──────────▼───────────┐ │
│  │  6. Adjust ◀─┼─────┼─ 5. Share   │◀────┤  4. Analyze output   │ │
│  │  and repeat  │     │  report      │     │  instantly           │ │
│  │  instantly   │     │  One-click   │     │  MTF · SNR · ΔE      │ │
│  │              │     │  HTML export │     │  Dynamic range       │ │
│  │  No waiting  │     │  zero deps   │     │  — same tool         │ │
│  └──────────────┘     └──────────────┘     └──────────────────────┘ │
└─────────────────────────────────────────────────────────────────────┘
```

---

## ��️ HDR Pipeline Architecture

```
┌─────────────────────────────────────────────────────────────────────┐
│                    LUMAIQ HDR PIPELINE VIEW                          │
│                                                                       │
│   Stage                        Owner                                  │
│   ─────────────────────────────────────────────────────────────     │
│   ┌─────────────────────┐                                            │
│   │ Black Level         │  ◀── LumaIQ                               │
│   │ Correction          │                                            │
│   └──────────┬──────────┘                                            │
│              │                                                        │
│   ┌──────────▼──────────┐                                            │
│   │ White Balance       │  ◀── LumaIQ                               │
│   └──────────┬──────────┘                                            │
│              │                                                        │
│   ┌──────────▼──────────┐                                            │
│   │ HDR Exposure        │  ◀── HDR ISP + LumaIQ  [HDR-only]        │
│   │ Selection           │                                            │
│   └──────────┬──────────┘                                            │
│              │                                                        │
│   ┌──────────▼──────────┐                                            │
│   │ Slope Correction    │  ◀── HDR ISP + LumaIQ  [HDR-only]        │
│   └──────────┬──────────┘                                            │
│              │                                                        │
│   ┌──────────▼──────────┐                                            │
│   │ Alpha Blending      │  ◀── HDR ISP + LumaIQ  [HDR-only]        │
│   └──────────┬──────────┘                                            │
│              │                                                        │
│   ┌──────────▼──────────┐                                            │
│   │ Color Correction    │  ◀── LumaIQ                               │
│   │ Matrix              │                                            │
│   └──────────┬──────────┘                                            │
│              │                                                        │
│   ┌──────────▼──────────┐                                            │
│   │ Gamma / Contrast    │  ◀── LumaIQ                               │
│   └──────────┬──────────┘                                            │
│              │                                                        │
│   ┌──────────▼──────────┐                                            │
│   │ HDR Tone Mapping    │  ◀── HDR ISP + LumaIQ  [HDR-only]        │
│   └──────────┬──────────┘                                            │
│              │                                                        │
│   ┌──────────▼──────────┐                                            │
│   │ IQ Analysis &       │  ◀── LumaIQ                               │
│   │ Report              │                                            │
│   └─────────────────────┘                                            │
│                                                                       │
│   Legend:  ◼ LumaIQ stage    ◼ ISP pipeline stage    ◼ HDR-only    │
└─────────────────────────────────────────────────────────────────────┘
```

---

## �� Application Suite

LumaIQ ships as **three integrated desktop applications** sharing a common core — each scoped to a specific phase of the ISP engineering lifecycle.

### �� LumaIQ — Full IQ Analysis Workbench

> The primary tool. Complete tuning + analysis environment.

- YAML pipeline editor with per-stage parameter control
- Full color pipeline — BLC, WB, CCM, Gamma, Contrast, TMO
- Complete analysis suite — MTF, noise, dynamic range, colorimetry
- Tuning Vault preset management and HTML report generation

---

### �� RawIQ — RAW Sensor Workbench *(Add-On)*

> Deep inspection of raw Bayer frames before the ISP touches them.

- 3×3 section-wise histograms on raw Bayer frames
- HDR pair matching and LDR best-exposure selector
- Per-frame sensor statistics dialog
- Format conversion: `.raw` · `.npy` · `.tiff (Bayer)` · `.tiff (RGB)` · `.png`

---

### ⚙️ BatchIQ — Batch ISP Processing *(Add-On)*

> Scale your regression testing across hundreds of frames overnight.

- GUI mode: job setup with real-time progress tracking
- CLI mode: CSV-driven LE/SE pair processing overnight
- Per-row pass/fail/skip status with timing data
- Summary CSV written automatically on completion

---

## �� Analysis Modules

> Every IQ metric that matters. Nothing you don't need.

| Module | Key Metrics | Category |
|---|---|---|
| **Sharpness / MTF** | ISO 12233 slanted-edge SFR · Laplacian variance · Sobel edge strength · per-channel MTF curves | Spatial |
| **Noise & SNR** | Per-channel σ (R/G/B) · CIELAB luma/chroma noise · SNR vs luminance curve · 1D noise power spectrum · spatial noise heatmap | Noise |
| **Dynamic Range** | EV estimate from flat-block SNR analysis · Ansel Adams 5-zone system · zone overlay maps · histogram | Exposure |
| **HDR Tone Mapping** | Reinhard global TMO · Durand bilateral LTM · side-by-side before/after preview · hardware LUT compare with PSNR | HDR |
| **Color Accuracy** | CIE76 · CIE94 · CIEDE2000 ΔE per patch · per-patch severity grading (OK / Warn / Fail) | Color |
| **White Balance** | Per-channel WB calculation · metrics · hue/sat fix · Planckian locus · CCT estimation | Color |
| **Exposure & Sensitivity** | Section-wise histograms on sensor frames · HDR pair detection · LDR best-exposure selector | Exposure |
| **Lens Calibration** | OpenCV chessboard pipeline · corner detection · camera calibration · undistortion map · calibration JSON | Optics |
| **Contrast & Gamma** | Entropy · local contrast · halo score · gamma estimation · live stats bar · LDCI analyze and calculate | Tonal |

---

## ✨ Key Features

<details>
<summary><strong>⚡ ISP Pipeline Integration</strong></summary>

Loads any YAML-based ISP config with a full collapsible per-stage parameter editor. Run the pipeline directly from the UI in a background thread — output captured for downstream analysis.

- YAML-native configuration
- Live in-app editing (no text editor needed)
- Background pipeline execution — UI stays responsive

</details>

<details>
<summary><strong>🌗 HDR / Linear Mode Toggle</strong></summary>

HDR-only stages — exposure selection, alpha blending, slope correction, dual-channel NR, tone mapping — auto-show and hide based on mode. The tool knows your pipeline and surfaces only what's relevant.

- Dual-exposure pair matching
- Auto-stage reveal for HDR mode
- Slope correction and alpha blending support

</details>

<details>
<summary><strong>🎯 Color Accuracy — ColorChecker</strong></summary>

Automatic ColorChecker prompt on image load. Quad-corner boundary selector extracts all 24 patches and computes CIE76, CIE94, and CIEDE2000 ΔE per patch with OK / Warn / Fail severity grading.

- CIEDE2000 ΔE per patch
- All 24 ColorChecker patches
- Severity grad...
