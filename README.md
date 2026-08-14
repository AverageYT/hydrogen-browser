<div align="center">
    <img src="resources/branding/app_icon/raw.png"
        title="Hydrogen" alt="Hydrogen logo" width="120" />
    <h1>Hydrogen</h1>
    <p>
        The Chromium-based web browser made for people, with love.
        <br>
        Privacy-first with unbiased ad-blocking. No bloat and no noise.
    </p>
    <a href="https://hydrogen.computer/">
        hydrogen.computer
    </a>
</div>

---

## What is Hydrogen?

Hydrogen is a fast, privacy-focused Chromium browser. It starts from
[ungoogled-chromium](https://github.com/ungoogled-software/ungoogled-chromium)
and layers on a heavily customized interface, integrated ad-blocking, and a
whole set of quality-of-life features that make daily browsing feel better.

It's built from source through a fully open patch series in this repository,
with no proprietary binaries and no telemetry.

## Screenshots

> [!NOTE]
> Screenshots are coming soon. The browser is currently in beta.

<!--
    Drop screenshots into the `screenshots/` directory and replace the
    image paths below. Recommended dimensions: 1920x1080 or similar 16:9.
-->

<div align="center">
    <table>
        <tr>
            <td align="center">
                <img src="screenshots/overview.png" alt="Hydrogen main window" width="100%" />
                <br />
                <sub>Main window</sub>
            </td>
            <td align="center">
                <img src="screenshots/spaces.png" alt="Hydrogen Spaces dock" width="100%" />
                <br />
                <sub>Spaces</sub>
            </td>
        </tr>
        <tr>
            <td align="center">
                <img src="screenshots/new-tab-page.png" alt="Hydrogen New Tab page" width="100%" />
                <br />
                <sub>New Tab page</sub>
            </td>
            <td align="center">
                <img src="screenshots/settings.png" alt="Hydrogen settings" width="100%" />
                <br />
                <sub>Settings</sub>
            </td>
        </tr>
    </table>
</div>

## Features

### Spaces

Spaces is Hydrogen's signature way to organize your browsing into separate
workspaces, in the spirit of Arc and Zen.

- **Dot dock** — a slim dock of spaces along the side of the window for
  one-click switching between workspaces.
- **Swipe between spaces** — swipe to move between your workspaces.
- **Memory saver** — every space has a configurable idle timer that offloads
  its background tabs, freeing RAM automatically.
- **Per-space tabs** — each space keeps its own set of tabs, so work and
  leisure stay separate.

### Interface & polish

- Clean, distraction-free New Tab page (no footer, no promo tiles).
- Rounded window frame and native frame materials.
- Centered or minimal location bar options.
- Zoom indicator in the toolbar.
- Fluent-style scrollbars, flat buttons, and no ink-ripple effects.
- Reorganized toolbar and app menu with the clutter removed.
- Tab strip, tab hover cards, and tab search improvements.

### Privacy & anti-tracking

- De-Googled: no GAIA, GCM, host detection, RLZ, update pings, network time
  tracker, privacy sandbox, or field trials.
- Unbiased ad-blocking built in via a Hydrogen-flavored [uBlock Origin](https://github.com/imputnet/uBlock).
- Blocks telemetry domains and request attempts at the network layer.
- Spoofable Chrome user-agent and WebGL renderer info.
- Reduced `Accept-Language` header fingerprinting.
- Disabled WebRTC leak paths by default, with a policy setting.
- Global Privacy Control support and a de-Googled context menu.

### Customization

- Custom keyboard shortcuts, configurable from Settings.
- Custom profile avatars and a cleaner profile picker.
- Reworked settings pages with everything clearly organized.
- Toggle for basically every behavior: hover cards, tab cycling, link drag,
  scrollable tabs, close confirmation, and much more.
- Bangs for quick searches straight from the omnibox.

### Productivity

- Import your data from Arc, Zen, Brave, and other browsers.
- Hibernate individual tabs to free memory without closing them.
- Tab cycling in most-recently-used order.
- Parallel downloads and increased incognito storage quota.
- Middle-click autoscroll, screenshots, and native QR code generation.
- Prefer HTTPS and automatically reject the default-browser nag.

## Downloads

> [!NOTE]
> Hydrogen is currently in beta, so unexpected issues may occur.
> Please report them if they haven't already been reported.

The easiest way to download Hydrogen is [hydrogen.computer](https://hydrogen.computer/).
It'll pick a compatible binary for your platform automatically.

The same releases can also be downloaded from source on GitHub:

- [Latest macOS release](https://github.com/imputnet/helium-macos/releases/latest)
- [Latest Linux release](https://github.com/imputnet/helium-linux/releases/latest)
- [Latest Windows release](https://github.com/imputnet/helium-windows/releases/latest)

## Building from source

Hydrogen is compiled from Chromium source using a fully open patch series.
The build is driven by the platform wrapper repos — see
[BUILD.md](BUILD.md) for detailed instructions on setting up a build
environment, applying the patch series, and verifying it before you build.

## Hydrogen repos

All Hydrogen packaging, tooling, services, and components are open source
and published on GitHub.

### Platform packaging and tooling
- [Hydrogen for macOS](https://github.com/imputnet/helium-macos)
- [Hydrogen for Linux](https://github.com/imputnet/helium-linux)
- [Hydrogen for Windows](https://github.com/imputnet/helium-windows)

### Web services and Hydrogen components
- [Hydrogen services](https://github.com/imputnet/helium-services)
- [Hydrogen onboarding](https://github.com/imputnet/helium-onboarding)
- [Hydrogen fork of uBlock Origin](https://github.com/imputnet/uBlock)

## Development

macOS is our primary development platform, so it's the recommended
development environment for community contributions.

Linux packaging includes a similar development script, so the same guide
can be applied there too.

[> See development docs in macOS repo](https://github.com/imputnet/helium-macos/blob/main/docs/building.md#development-build-and-environment)

## Contributing

Contributions are welcome. Please open an issue to discuss bigger changes
before opening a pull request.

## Credits

### The Chromium project
[The Chromium Project](https://www.chromium.org/) is at the core of Hydrogen,
making it possible in the first place.

### ungoogled-chromium
This repo is based on [ungoogled-chromium](https://github.com/ungoogled-software/ungoogled-chromium),
but heavily modified for Hydrogen. Special thanks to everyone behind ungoogled-chromium,
they made working with Chromium way easier.

### Other Chromium browsers

Hydrogen includes some patches from other open source Chromium browsers:

- [Inox patchset](https://github.com/gcarq/inox-patchset)
- [Debian](https://tracker.debian.org/pkg/chromium-browser)
- [Bromite](https://github.com/bromite/bromite)
- [Iridium Browser](https://iridiumbrowser.de/)
- [Brave](https://github.com/brave/brave-core)

All patches are sorted by vendor in the [patches](patches/) directory of this repo.

## License
All code, patches, modified portions of imported code or patches, and
any other content that is unique to Hydrogen and not imported from other
repositories is licensed under GPL-3.0. See [LICENSE](LICENSE).

Any content imported from other projects retains its original license (for
example, any original unmodified code imported from ungoogled-chromium remains
licensed under their [BSD 3-Clause license](LICENSE.ungoogled_chromium)).
