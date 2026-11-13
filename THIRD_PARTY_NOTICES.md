# Third-party notices

This is the register of what a MediaHub build ships or talks to. Versions are the pinned ones in `pyproject.toml`.

## Shipped in a build

| Component | Version | License | Obligation |
|---|---|---|---|
| PySide6-Essentials, shiboken6 (Qt for Python) | 6.12.0 | LGPL-3.0-only (chosen from LGPL-3.0, GPL-2.0, GPL-3.0) | Keep Qt as separate, replaceable libraries; ship the LGPL text and this notice; say where to get the Qt source. Do not statically link it or bundle it into a single-file build. |
| RapidFuzz | 3.14 | MIT | Keep the copyright notice. |
| watchdog | 6 | Apache-2.0 | Keep the license and any NOTICE file. |
| Python runtime | 3.11 | PSF-2.0 | Keep the license. |

## Used only to build or test

PyInstaller (GPL-2.0-or-later with an exception that allows distributing built programs), pytest, ruff and mypy. None of these ship as a library, apart from PyInstaller's bootloader, which the exception covers.

## Not shipped

- **Fonts.** Vazirmatn 33.0.3 (variable weight) is bundled in `src/mediahub/ui/assets/fonts/` with its SIL Open Font License 1.1 in `OFL.txt` beside it. It is unmodified, taken from the `vazirmatn` npm package; SHA-256 `696249a2c74b39ffdef55de4df2809c5b639d3ff80d618d8160a095d2fd49dca`. Segoe UI and Tahoma, which belong to Windows, are the fallbacks.
- **ffprobe and ffmpeg.** The app uses a copy already on the machine. Bundling needs a check of the exact build, because GPL builds carry different terms from LGPL ones.
- **Posters and artwork.** They are fetched at run time and never packaged.

## Artwork and icons

The Home mountain art is drawn in code by `MountainBanner.qml`. The app icon is a placeholder drawn in code by `ui/background.py`; the final brand is still undecided. Sidebar symbols are ordinary Unicode characters. No third-party icon set is used.

## Online services

These are off until the user enables online lookup.

- **TMDB.** Uses the user's own key. This product uses the TMDB API but is not endorsed or certified by TMDB. A commercial release needs a separate agreement with TMDB.
- **TVmaze, AniList, Kitsu, AnimeGate.** Each file's cover credit names its source. Check each service's terms before any commercial release. AnimeGate (animegate.net) is read only through its sitemap and anime pages, which its robots.txt opens to crawlers, for posters and Persian story summaries, each shown with its name; it has not granted permission, so ask its owners before shipping to others.
