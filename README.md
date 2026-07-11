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

## What This Includes

- Product identity changed from Chromium to Aster.
- Browser-facing settings and About strings updated to Aster.
- Product metadata updated to `Aster Team`.
- About copyright updated to `Copyright 2026 Aster Team. All rights reserved.`
- A maintained patch file at [`patches/0001-rename-branding.patch`](patches/0001-rename-branding.patch).

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

Run the browser:

```powershell
out\Default\chrome.exe --user-data-dir=C:\chromium\test-profile
```

## Verification

After building, open `chrome://version`. The application label should show
`Aster`, and the About copyright resources should resolve to Aster Team.

The latest local build output is:

```text
C:\chromium\src\out\Default\chrome.exe
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
