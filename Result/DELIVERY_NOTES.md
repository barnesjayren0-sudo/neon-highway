# Delivery Notes — NeonHighway_Mobile_Godot4.zip

**Status: complete.** The full pipeline from the root `README.md` was executed.

## Deliverable

- **File:** `Result/NeonHighway_Mobile_Godot4.zip` (1.1 MB, 232 entries)
- **SHA-256:** `b97088111e9347cebab7f7edc27c0dfb83496f66f58a9a5f8301748a1fc49eaa`
- **Contents:** one complete Godot 4.3 project folder (`NeonHighway_Mobile_Godot4/`) with
  `project.godot`, `scenes/`, `scripts/`, `assets/`, `localization/`, `addons/gut/`,
  `export_presets.cfg` (Android, mobile) and a project `README.md` documenting the merge.

## Checklist (from root README)

- [x] Downloaded `Combine_these.zip` from the MediaFire link
- [x] Extracted/used the archive via the `you have to combine/` input workspace (see
      `you have to combine/SOURCE_NOTES.md`; the 50 MB archive is intentionally not committed —
      the README says "no GitHub upload needed")
- [x] Combined the archive contents into one working mobile Godot 4 project
- [x] `Result/` contains the final `.zip`
- [x] Confirmed the zip opens as a Godot 4 project aimed at mobile

## What the archive contained and how it was combined

`Combine_these.zip` held two unpacked Godot Android exports:

| Part | What it was | What happened to it |
| --- | --- | --- |
| `neon/` | Complete Godot 4.3 Android export of the game **"Neon Dash"** (`com.neondash.game` v0.2.1, landscape) — compiled scripts/scenes plus `project.binary` | Recovered into full editable sources with GDRE Tools: **104/104 scripts** decompiled, **161/162 resources** converted, `project.godot` restored; launcher icons extracted from the APK resources |
| `stellar/` | Godot 4.7 Android **shell** of a different app ("Stellar Stones", `org.stellarstones.sh`) with **no engine payload or game data** — only Android packaging assets | All mergeable content folded in: `rendering.method=mobile` → project uses the Mobile renderer; adaptive icons + splash converted (WebP → PNG) into `assets/icons/android/stellar/`; its mobile packaging informed the Android export preset (landscape, immersive, ARM architectures) |

## Verification (Godot 4.3-stable, headless)

- Editor import pass: **0 errors** (61 assets imported)
- Boot run (600 frames): **0 errors**
- All 19 scenes load + instantiate: **19/19 OK**
- Scripted gameplay run (Game scene, simulated input ~12 s): score 204, distance 204.3, **0 errors**
- Android export preset parses and resolves (`--export-release "Android"` reaches template/SDK
  checks, which fail only because this sandbox has no Android SDK/templates — expected)

One defect was found by verification and fixed: `PoolManager.acquire()` returned recycled nodes
that were still parented to the pool container, breaking every re-used chunk/obstacle/collectible
with "already has a parent" errors. It now detaches the node from its current parent first.
Full details are in the project `README.md` inside the zip.
