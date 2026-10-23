# Benchmark Token Studio release history

## Native 1.0.1

- Preserves the current product title when the native runtime observer updates the interface.
- Updates matching package and installer version metadata.
- Backend and training mathematics are unchanged from the reviewed version-1 baseline.
- Includes the verified installer and all five matching payload parts.

## Browser v1

The browser trial remains version 1 and uses JavaScript/WebGPU, not the native PyTorch backend. The 2026-10-23 browser startup patch keeps its product title stable and excludes the trial-status wrapper from the benchmark-only hide selector, so the gold icon, current licensing notice, adapter check and diagnostic export remain visible. The startup repair changes four title assignments and one CSS selector; native 1.0.1 payload and benchmark mathematics are unchanged. See BROWSER_TRIAL.json for the current browser hash and test scope.

## Qualification boundaries

Recorded CPU, mocked lifecycle, static/DOM, package-integrity, corrupted-part and isolated-extraction checks are not physical Windows 11, WebView2, Radeon or WebGPU performance qualification. No universal compatibility or maximum speed is promised.

## Licensing

The initial release used the Nexus Personal-Use License. The current supplemental permission allows personal use and internal commercial testing and evaluation for Nexus-owned material in native 1.0.1 and browser version 1. Distribution, modification, production deployment and other commercial use require express written consent. Third-party licenses and previously granted rights remain unchanged. See [COMMERCIAL_EVALUATION_PERMISSION.md](COMMERCIAL_EVALUATION_PERMISSION.md). The current browser notice and root licensing documents reflect this additional permission; historical bundled notices and native component bytes are preserved.
