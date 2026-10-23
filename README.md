# Nexus Benchmark Token Studio

**Version 1.0.1**

Measure training workloads with explicit timing, valid-token counts and evaluation records.

**[Try in your browser](https://rdunbar01.github.io/Nexus-Benchmark-Token-Studio/Nexus_Benchmark_Token_Studio_v1_Browser.html)** · [Download the desktop components](releases/1.0.1/) · [Wiki](https://github.com/RDunbar01/Nexus-Benchmark-Token-Studio/wiki)

Open the trial to inspect the interface and choose **Check WebGPU adapter**. No Python installation is needed. The aim is a quick first look, not a promise that a model will load or finish a workload in seconds.

## What it does

- A disposable browser scratch-model benchmark using synthetic tokens.
- Installed PyTorch tests for supported native workloads.
- Separate reporting of warm-up, training, evaluation and generation measurements.
- Exportable evidence for comparing settings without counting padding as useful tokens.

## Engineering contribution

A reproducible measurement workflow for small-model development. It distinguishes synthetic speed tests from loaded-model and corpus evaluation so that a tokens-per-second figure has a defined workload behind it.

## What the browser trial measures

The trial uses a disposable scratch model and synthetic tokens. It is not a general GGUF inference loader or a loaded-model evaluator. Use the installed application for supported native workload evaluation.

Benchmark Token Studio remains version 1; 1.0.1 is a maintenance update. Internal inherited engine labels are not the product version.

## Why a single HTML file?

The browser edition packages its interface, JavaScript, CSS and WGSL kernels in one HTML file. This makes online trials easy to open, share as a link and inspect without a build step or runtime CDN. The monolithic file is a distribution choice for accessible trials, not a claim that every model or native dependency fits inside it.

Use a compatible WebGPU browser over HTTPS. The trial uses the custom browser engine, not PyTorch. Runtime network requests, native hardware monitoring and local-server bridges are disabled. The scratch fixture is built in; native workloads are separate.

## Full application and Python

**The native PyTorch backend requires the full download.** Get every file in [releases/1.0.1](releases/1.0.1/), keep the numbered data parts beside [Start_Nexus.py](releases/1.0.1/Start_Nexus.py), and run `python Start_Nexus.py`. Review the installation plan before confirming. Do not mix release components.

Use standard **64-bit CPython 3.12** for the launcher. The advertised installer range is 3.11–3.14; actual native compatibility also depends on the selected Python/PyTorch runtime and its probe. The new AMD-runtime installation path checks standard, non-free-threaded x64 CPython 3.11–3.14 and Windows 11 25H2; an existing runtime must pass its probe. See the [runtime and validation notes](docs/TECHNICAL_NOTES.md) and [package guide](releases/1.0.1/README.md) for exact conditions. Python, GPU drivers and compilers are not silently replaced.

Each data part is at most 10,000,000 bytes; each individual distribution file is below 20,000,000 bytes. Reconstructed files, installed files and model weights can be larger.

## Validation

Recorded CPU regressions, frontend checks and package-integrity checks cover the published sources. Browser launch checks establish that the interface opens; they do not establish full-model correctness or physical Windows/Radeon performance. A WebGPU adapter check is only a capability check.

## Use and attribution

Developed by Rich Dunbar / Nexus Emerging Technology. Personal use and internal commercial testing and evaluation are permitted for Nexus-owned material. Distribution, modification, production deployment and other commercial use require express written consent. Third-party licenses and previously granted rights remain unchanged. See the [license](LICENSE) and [evaluation permission](COMMERCIAL_EVALUATION_PERMISSION.md).
