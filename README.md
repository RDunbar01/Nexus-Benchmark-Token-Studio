# Nexus Benchmark Token Studio

## [Try in your browser](<https://rdunbar01.github.io/Nexus-Benchmark-Token-Studio/Nexus_Benchmark_Token_Studio_v1_Browser.html>)

Open the HTTPS launch link above to run the browser trial. The exact [single-file HTML source](./Nexus_Benchmark_Token_Studio_v1_Browser.html) is also available in this repository; GitHub's source viewer does not execute it.

Open the link and choose **Check WebGPU adapter** to inspect the interface and browser capability. The first-10-seconds goal is to reach the UI and check capability, not to download a model, finish training or guarantee inference. Load time depends on your connection and device.

**Browser trial: no Python required. Native PyTorch backend: full download required.** Download every component in [releases/1.0.1](releases/1.0.1/), not just the HTML or installer. The browser does not contain or run Python/PyTorch. See [Python and native runtime requirements](#python-and-native-runtime-requirements).

## Current release licensing

This Nexus release is not offered under Apache License 2.0. Nexus-owned software may be used only for personal, non-commercial purposes. Any other use, including commercial use, modification or redistribution, requires express written consent from the rights holder. Third-party code, models, datasets and separately licensed components retain their own licenses and notices. Previously granted rights and rights that cannot lawfully be restricted remain unchanged.

**Version 1.0.1 · browser source and native installer components · experimental software**

Measure scratch-model training and supported native PyTorch workloads with explicit timing, valid-token counts and evaluation receipts.

The browser edition runs a disposable scratch-model benchmark with synthetic tokens. It is not a general GGUF inference loader or a loaded-model evaluator. Native-only workload evaluation requires the installed application.

The desktop release is packaged with the Nexus AI-style installer: a consolidated change summary, one installation confirmation, determinate progress and reuse of compatible existing dependencies. Only verified completion should trigger app launch and installer closure; Windows launch behavior requires its own acceptance test.

## Browser capabilities and limits

Try the disposable scratch-model benchmark with synthetic tokens. This is not a general GGUF inference loader or a loaded-model evaluator.

Use a compatible WebGPU browser on HTTPS or a supported secure localhost origin. The single file includes its JavaScript, CSS and WGSL kernels without a runtime CDN dependency. Browser GPU work uses the custom JavaScript/WebGPU engine, not PyTorch. Online dataset downloads, server model bridges and native hardware monitoring are unavailable; runtime network requests are blocked. External documentation links open only when selected.

A WebGPU API or adapter check is not a successful arithmetic test, a model-fit result or a performance measurement. Physical Windows 11/Radeon/WebGPU execution remains a separate qualification step.

## Desktop package and installation

The complete desktop component set is in [releases/1.0.1](releases/1.0.1/). Download every file together, preserving the supplied layout. Each data part is at most 10,000,000 bytes and every individual distribution file is below 20,000,000 bytes; reconstructed files, installed files and model weights can be larger.

The package entry point is `Start_Nexus.py`; keep `Nexus_payload.001.nxd`, `Nexus_payload.002.nxd` and all following parts alongside it. Run `python Start_Nexus.py` with the supported Python interpreter. The final package manifest is the authority for hashes and dependencies. Do not run an installer from a different release against these data parts. Read its change summary before confirming installation. Recorded package review and isolated extraction checks do not establish native Windows acceptance.

## Python and native runtime requirements

- **Recommended launcher: standard 64-bit CPython 3.12.** The installer advertises Python **3.11–3.14**, but the bootstrap itself does not enforce that version range. Opening the installer with another version is not evidence that the native backend is compatible.
- **New AMD runtime installation requires standard, non-free-threaded, 64-bit CPython 3.11–3.14** on Windows 11 **25H2**. Existing runtimes are tested before that installation gate and are reused only when the runtime probe passes; their Python must match their installed PyTorch wheels. No wider Python-version compatibility is certified here.
- The packaged native probe expects **PyTorch 2.14.0+rocm10.1.0**, HIP and the configured RX 7900 XT/XTX device, then performs a finite FP32 forward/backward check. Python, AMD drivers and compiler prerequisites are not installed or changed by this package. Check the [official AMD compatibility matrix](https://rocm.docs.amd.com/en/latest/compatibility/compatibility-matrix.html) for the exact OS/GPU/driver combination.

These are installer/runtime conditions, not completed physical Windows, WebView2, Radeon or full-model qualification. A successful probe does not qualify every precision, compilation mode or workload.

## Measurement and validation

Native PyTorch tests distinguish synthetic scratch fixtures from loaded-model/corpus workloads. Timed training, evaluation, warm-up/compilation, prompt processing and autoregressive generation are different measurements. Report valid target tokens, elapsed time, model, context, batch size, precision, backend and hardware alongside throughput; do not count padding as useful tokens or describe a CPU result as GPU performance.

The source handoff passed recorded CPU regression and frontend checks. Browser editions passed static/DOM checks, not physical GPU arithmetic or performance qualification. A clean scoped test run does not prove absence of bugs. No maximum speed, universal model support or Windows driver certification is promised.

## Project and licensing

Developed by Rich Dunbar / Nexus Emerging Technology using AI-assisted coding and an iterative build–measure–learn process. Third-party licenses and notices remain authoritative for their respective components. Model, dataset and upstream-code terms apply separately; this README grants no new reuse rights.

This repository publishes the reviewed Benchmark Token Studio package. Native application source and reproducible tests are included inside the integrity-checked payload; use the full component set to extract them. Benchmark Token Studio remains version 1 as requested; inherited internal engine identifiers are not the product version.

## Extract source and reproduce checks

With all version-matched components in one folder, run `python Start_Nexus.py --extract-only ./benchmark-source`. This verifies and extracts the packaged application/source without launching the app or installing its runtime dependencies. Use a new empty destination; do not overwrite unrelated work.

In the extracted folder, `python RUN_VERIFICATION.py --skip-browser` runs the included fixture-based Python suites using an already prepared compatible Python/PyTorch runtime. Full browser suites also require Node and Playwright/Chromium as described by that script. These checks are not physical Radeon/Windows certification.

The included `installer/package_apps.py --product benchmark` is the packaging entry point (run with Python from the extracted source tree). Its inherited output filename is an internal build identifier, not a new product version. Rebuilding can change archive bytes and must be revalidated; do not label a rebuilt artifact with the published hashes. Modification or redistribution of Nexus-owned material requires express written consent under the license.

## Release history

Native 1.0.1 fixes the runtime observer so it preserves the current application title. Backend and training math are unchanged from the reviewed version-1 baseline. The separately qualified browser trial remains v1. See [release history](CHANGELOG.md) and the [component hash manifest](releases/1.0.1/release_manifest.json).

## Wiki source

[English](wiki/Home.md) · [Français](wiki/Home.fr.md) · [日本語](wiki/Home.ja.md) · [한국어](wiki/Home.ko.md). These are reviewable repository Wiki source files. The GitHub Wiki is maintained separately.
