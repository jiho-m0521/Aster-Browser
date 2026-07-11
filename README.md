# Aster Browser

[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stars][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![License][license-shield]][license-url]

Aster Browser is a Chromium-based browser project maintained by Aster Team.
This repository tracks the Aster branding patch set for Chromium and documents
the current Windows build flow.

## Repository

- Project: [jiho-m0521/Aster-Browser](https://github.com/jiho-m0521/Aster-Browser)
- Maintainer: [Aster Team](https://github.com/jiho-m0521/Aster-Browser)
- Upstream base: [Chromium](https://www.chromium.org/)

## Build Notes

The working Chromium checkout used for this patch is expected at:

```text
C:\chromium\src
```

Generate build files:

```powershell
$env:DEPOT_TOOLS_WIN_TOOLCHAIN = "0"
$env:GYP_MSVS_OVERRIDE_PATH = "C:\Program Files\Microsoft Visual Studio\18\Insiders"
gn gen out\Default
```

Build Aster:

```powershell
autoninja -C out\Default chrome
```

The Windows build target remains `chrome` for Chromium build compatibility, but
the generated browser executable is:

```text
C:\chromium\src\out\Default\aster.exe
```

Run the browser:

```powershell
out\Default\aster.exe --user-data-dir=C:\chromium\test-profile
```

## Logo Assets

The Aster logo is generated and installed by:

```powershell
python tools\prepare_aster_logo.py "C:\path\to\aster-logo.png" --src-root C:\chromium\src
```

The script creates a transparent 1024x1024 master image, PNG assets at
16/24/32/48/64/128/256 pixels, and a real multi-size ICO. It searches the
current Chromium checkout for product logo PNGs and `chromium.ico`, backs up
the originals under `branding\backup\<timestamp>\`, then replaces only matching
logo resources.

The script also prepares Windows shell-facing assets so the Aster logo is used
for the running app, taskbar grouping, Start menu and desktop shortcuts,
document icons, tile images, WebUI SVG logos, and profile shortcut regeneration.

## Aster Identity

The patch set currently applies:

- Product-facing name: `Aster`
- Maintainer/developer identity: `Aster Team`
- Display version in `chrome://version` and Settings About: `1.0.0.0`
- Windows browser executable output: `aster.exe`
- Windows AppUserModelID/install identity: `Aster`
- Startup Google API key warning: disabled for Aster builds
- Settings About logo click animation: disabled
- Default new tab page: replaced with the Aster dashboard from `C:\aster-ntp`
  and packaged as `chrome://new-tab-page` resources

## Verification

After building, open `chrome://version`. The application label should show
`Aster`, the displayed version should be `1.0.0.0`, and the About copyright
resources should resolve to Aster Team.

The latest local build output is:

```text
C:\chromium\src\out\Default\aster.exe
```

## Development

All future Aster Browser changes should be pushed to:

```text
https://github.com/jiho-m0521/Aster-Browser
```

Keep Chromium upstream available separately:

```powershell
git remote add upstream https://chromium.googlesource.com/chromium/src.git
git remote set-url origin https://github.com/jiho-m0521/Aster-Browser.git
```

## License

Aster Browser is based on Chromium and retains Chromium's open-source license
notices. See Chromium's `LICENSE` file in the source checkout for details.

[contributors-shield]: https://img.shields.io/github/contributors/jiho-m0521/Aster-Browser.svg?style=for-the-badge
[contributors-url]: https://github.com/jiho-m0521/Aster-Browser/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/jiho-m0521/Aster-Browser.svg?style=for-the-badge
[forks-url]: https://github.com/jiho-m0521/Aster-Browser/network/members
[stars-shield]: https://img.shields.io/github/stars/jiho-m0521/Aster-Browser.svg?style=for-the-badge
[stars-url]: https://github.com/jiho-m0521/Aster-Browser/stargazers
[issues-shield]: https://img.shields.io/github/issues/jiho-m0521/Aster-Browser.svg?style=for-the-badge
[issues-url]: https://github.com/jiho-m0521/Aster-Browser/issues
[license-shield]: https://img.shields.io/github/license/jiho-m0521/Aster-Browser.svg?style=for-the-badge
[license-url]: https://github.com/jiho-m0521/Aster-Browser/blob/main/LICENSE
