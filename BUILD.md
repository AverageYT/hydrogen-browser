# Building Hydrogen (Hydrogen + Spaces fork)

This repository is the **patch source** for the browser: it contains the
patch series (`patches/series` + `patches/`) and the build utilities that
turn Chromium into Hydrogen/Hydrogen. The actual compilation is driven by the
platform wrapper repos:

- macOS: <https://github.com/imputnet/helium-macos> (embeds this repo as the
  `hydrogen-chromium` submodule)
- Linux: <https://github.com/imputnet/helium-linux>
- Windows: <https://github.com/imputnet/helium-windows>

Hydrogen-specific patches added in this fork (all under `patches/`):

- `hydrogen/core/hydrogen-spaces-controller.patch` — Spaces data model, prefs,
  and the memory-saver offload timer (registered in `patches/series`).

## Transferring to a build machine

A full Chromium build needs ~100 GB free disk, 16 GB+ RAM, and a fast CPU;
this repo itself is tiny. Copy it over as-is:

```sh
# on the source machine
cd ~/hydrogen
git bundle create /tmp/hydrogen.bundle --all

# on the build machine (macOS 12+, Xcode 26, Homebrew)
git clone /tmp/hydrogen.bundle hydrogen
```

## Building on macOS (recommended)

1. Install build dependencies:

   ```sh
   brew install python@3.13 ninja wget coreutils readline
   pip3 install --break-system-packages httplib2==0.22.0 requests pillow
   xcodebuild -downloadComponent MetalToolchain
   brew unlink binutils   # use Xcode's binutils
   ```

2. Clone the build wrapper and point its patch submodule at this repo:

   ```sh
   git clone --recurse-submodules https://github.com/imputnet/helium-macos.git
   cd hydrogen-macos
   rm -rf hydrogen-chromium
   git clone /path/to/hydrogen hydrogen-chromium   # the Hydrogen patch source
   ```

   (Alternatively, keep the submodule and swap its remote:
   `cd hydrogen-chromium && git remote set-url origin /path/to/hydrogen && git fetch && git checkout main`)

3. Build:

   ```sh
   ./build.sh          # official one-shot build; .dmg lands in build/
   ```

   For iterative development instead:

   ```sh
   source dev.sh
   he setup            # first time: download source, set up GN, apply patches
   he build
   he run              # run with a dedicated data dir
   ```

## Building on Linux / Windows

Same principle: use the corresponding wrapper repo
(`hydrogen-linux` / `hydrogen-windows`) with the `hydrogen-chromium` submodule
pointed at this Hydrogen repo, then follow that wrapper's `build.sh` /
`dev.sh` instructions.

## Verifying the patches before building (cheap, any machine)

Patch-application validation needs only the Chromium source archive (it is
downloaded by the wrapper anyway):

```sh
./devutils/validate_patches.py -l <path-to-chromium-src> -v
./devutils/check_patch_files.py
./devutils/lint.py
```

These mirror the project's CI checks. A patch that passes
`--dry-run --fuzz=0` here will apply in the real build.

## Troubleshooting

- Build fails while downloading source: remove `build/downloads_cache`, retry.
- Build fails after download: remove `build/src`, retry.
- Patch series rejects a Hydrogen patch: it was authored against
  Chromium `151.0.7922.137`; verify `chromium_version.txt` matches.
