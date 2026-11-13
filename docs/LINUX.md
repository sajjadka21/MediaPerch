# MediaPerch on Linux

Linux packages are **x86_64**, built on Ubuntu 24.04 (glibc 2.39 or newer). They target Ubuntu 24.04+, Linux Mint 22+, Debian 13+ and Fedora 40+ / similarly recent distributions. These builds do not support ARM or older glibc distributions. Python is included; no separate Python installation is required.

Download from [GitHub Releases](https://github.com/sajjadka21/MediaPerch/releases/latest).

| Format | Use |
| --- | --- |
| `.AppImage` | Portable single file. Make it executable and run it. |
| `.deb` | Ubuntu, Debian and Linux Mint; integrates with the application menu. |
| `.rpm` | Fedora-compatible systems; integrates with the application menu. |
| `.tar.gz` | Extract the directory and run its `MediaPerch` executable. |

## Install

```sh
# Ubuntu 24.04 / Debian 13 / Mint 22
sudo apt install ./MediaPerch-0.9.0-linux-x86_64.deb

# Fedora 40+
sudo dnf install ./MediaPerch-0.9.0-linux-x86_64.rpm

# AppImage
chmod +x MediaPerch-0.9.0-linux-x86_64.AppImage
./MediaPerch-0.9.0-linux-x86_64.AppImage
```

If FUSE is unavailable, AppImage can be extracted and run:

```sh
./MediaPerch-0.9.0-linux-x86_64.AppImage --appimage-extract
./squashfs-root/AppRun
```

The tarball is portable too:

```sh
tar -xzf MediaPerch-0.9.0-linux-x86_64.tar.gz
./MediaPerch-0.9.0-linux-x86_64/MediaPerch
```

Use your normal desktop session, not `sudo`, to run the app. A graphical desktop is required. On X11, ensure the system's Qt/XCB/OpenGL dependencies are installed (including `libxcb-cursor0` on Ubuntu). `ffmpeg` is optional for video probing/frame artwork. Playback uses the desktop's associated media player.

## Behaviour and differences from Windows

- English and Persian UI, library browsing, identification, online posters, subtitles, collections and Smart Organize are available.
- File paths are native POSIX paths and case-sensitive. Moves use an atomic no-overwrite rename. Cross-filesystem moves verify the copy before sending the source to the desktop Trash; failure to trash leaves the source intact.
- Catalogue and artwork: `$XDG_DATA_HOME/mediaperch`, normally `~/.local/share/mediaperch`.
- Autostart is optional and uses an app-owned file under `$XDG_CONFIG_HOME/autostart/mediaperch.desktop`.
- Saving optional private provider credentials requires an unlocked desktop Secret Service/keyring. Credentials are never silently stored in plaintext. The shared metadata service does not require a personal key.
- Explorer `desktop.ini` folder artwork is Windows-only and hidden on Linux. Your posters remain visible in MediaPerch.
- Install updates through your package manager or download a newer portable package. The Windows `.exe` update installer is disabled on Linux.
- Mount polling tracks disconnected filesystems; Linux does not provide the Windows-specific pre-eject notification used by the Windows build. Safely finish/cancel file operations before unmounting a drive.
- The tarball/AppImage do not register themselves in the app menu automatically. DEB/RPM packages install the desktop entry and approved icon.

## Verify downloads

Download `SHA256SUMS-linux.txt` beside the package and run:

```sh
sha256sum --check SHA256SUMS-linux.txt --ignore-missing
```

The packages are unsigned distribution packages. This is not a Flatpak/Snap store release. Removing the package does not remove your personal catalogue or original media.

## Testing scope

The native Linux adapter, scan/analyze/organize flow, case-sensitive paths, non-overwrite rename, autostart and real QML startup are tested on Ubuntu 24.04 under WSL. The frozen executable and extracted package payloads are tested before upload. Fedora hardware, every desktop environment and physical drive-ejection behaviour have not been independently verified.
