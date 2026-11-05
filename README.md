<div align="center">

<img src="snap/gui/openscreen.png" alt="OpenScreen logo" width="128" />

# OpenScreen

**Record your screen and turn it into a polished demo video.**

[![openscreen](https://snapcraft.io/openscreen/badge.svg)](https://snapcraft.io/openscreen)
[![Base: core26](https://img.shields.io/badge/Base-core26-2C8C3C?logo=canonical&logoColor=white)](https://snapcraft.io/core26)
![Confinement: strict](https://img.shields.io/badge/Confinement-strict-2C8C3C)
[![Maintainer: sidaliteir](https://img.shields.io/badge/Maintainer-sidaliteir-2C8C3C?logo=snapcraft&logoColor=white)](https://snapcraft.io/publisher/sidaliteir)
![Architectures: amd64, arm64](https://img.shields.io/badge/Architectures-amd64%20%7C%20arm64-2C8C3C?logo=linux&logoColor=white)

[Getting Started](#getting-started) · [Configure](#configure) · [Limitations](#limitations) · [Build](#build) · [Support](#support) · [License](#license)

Unofficial snap packaging for [OpenScreen](https://github.com/getopenscreen/openscreen), the maintained continuation of Siddharth Vaddem's screen recorder and video editor.

</div>

---

## Getting Started

<a href="https://snapcraft.io/openscreen"><img alt="Get it from the Snap Store" src="https://snapcraft.io/en/dark/install.svg" width="180"></a>

```bash
sudo snap install openscreen
sudo snap connect openscreen:pipewire
sudo snap connect openscreen:audio-record
openscreen
```

Choose a screen or window in your desktop's sharing dialog, record a take, then edit and export it. Screen recording needs a running PipeWire session and an `xdg-desktop-portal` backend that implements ScreenCast, on both Wayland and X11.

## Configure

Use the application's settings. Settings, projects and downloaded speech models stay inside `~/snap/openscreen/common`; exported files can be saved to your home directory. There are no `snap set` options.

For a webcam, encrypted AI-provider credentials, or files on removable storage, connect the corresponding interface:

```bash
sudo snap connect openscreen:camera
sudo snap connect openscreen:password-manager-service
sudo snap connect openscreen:removable-media
```

The `pipewire` connection grants access to the session's media server for native microphone and system-audio recording. Speech models download on first use; optional AI editing uses a provider you configure yourself.

## Limitations

- Capture sources and editable cursor movement depend on your desktop's portal support. Global mouse-click recording is disabled under confinement, so recorded click effects and click-based automatic zooms are unavailable. Manual zooms and portal cursor capture remain available.
- Audio capture requires the `pipewire` connection and a running PipeWire server. Webcam access needs the `camera` connection.
- Vulkan GPU support affects preview, export and transcription performance. Software fallbacks can be slow; the amd64 speech fallback requires AVX2-capable hardware.
- Hidden folders outside the snap's own data are not automatically accessible. Desktop updates come through `snap refresh openscreen`.

## Build

```bash
git clone https://github.com/sidalit/openscreen-snap.git
cd openscreen-snap
sudo snap install snapcraft --classic
snapcraft pack
```

```bash
sudo snap install --dangerous ./openscreen_*.snap
sudo snap connect openscreen:pipewire
sudo snap connect openscreen:audio-record
openscreen
```

## Support

- **Installation or snap issues:** [open a packaging issue](https://github.com/sidalit/openscreen-snap/issues).
- **Application bugs:** [report them upstream](https://github.com/getopenscreen/openscreen/issues).

## License

Snap packaging: [MIT](LICENSE).
