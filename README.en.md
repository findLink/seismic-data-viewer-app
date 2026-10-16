<p align="center"><img src="assets/hero.png" alt="Seismic Data Viewer" width="100%"></p>

<p align="center"><a href="README.md">中文</a> · English · <a href="https://github.com/findLink/seismic-data-viewer-app/releases/latest">Download</a> · <a href="https://github.com/findLink/seismic-data-viewer-app/issues">Feedback</a></p>

# Seismic Data Viewer

**Open a volume. Move a slider. Compare your seismic data and labels.**

A desktop viewer for **3D NPY/NPZ seismic volumes, fault masks and stratigraphic labels**. Use it for dataset inspection, annotation review, teaching and checking model outputs. No terminal or separate Python installation is required for everyday use. Installed builds work offline with local files.

This is the **public downloads and feedback repository**. Application source code remains private. Personal and commercial use is free under the [application terms](LICENSE.txt); this is a proprietary application, not an open-source project. Third-party components retain their own licenses.

## Download

| Platform | Installer | Requirements |
| --- | --- | --- |
| Mac | [Download DMG](https://github.com/findLink/seismic-data-viewer-app/releases/download/v1.0.2/Seismic-Data-Viewer-1.0.2-macos-arm64.dmg) | Apple Silicon, macOS 15+; no Intel Mac build |
| Windows | [Download Setup.exe](https://github.com/findLink/seismic-data-viewer-app/releases/download/v1.0.2/Seismic-Data-Viewer-1.0.2-windows-x64-setup.exe) | x64; installer minimum is Windows 10 1809 |

[Latest release and all files](https://github.com/findLink/seismic-data-viewer-app/releases/latest) · [Synthetic demo data](https://github.com/findLink/seismic-data-viewer-app/releases/download/v1.0.2/Seismic-Data-Viewer-1.0.2-demo-data.zip)

**No GitHub login is needed to download.** Mac builds use ad-hoc signing and are not Developer ID signed/notarized. Windows installers are not publisher-signed; target Windows GUI/GPU testing remains pending.

![Real application screenshot with seismic amplitudes and fault masks](assets/fault-overlay.jpg)

*Screenshots show Mac version 1.0.2 with original synthetic 160³ data. They contain no real survey data. Colors represent label IDs.*

## Features

| Feature | What you can do |
| --- | --- |
| Separate imports | Load data and labels independently, even from different directories. |
| Three slice directions | Select fixed X/Y/Z sections and browse positions with the bottom slider. |
| Label overlays | Toggle faults and strata separately and adjust opacity to compare annotations with amplitudes. |
| 3D inspection | View volume and label geometry in 3D; performance depends on data size, GPU and drivers. |
| Display controls | Adjust contrast, gamma, colormap, interpolation and volume rendering without changing source amplitudes. |
| Review and export | Use label painting, points and shapes for review; save layers or export a view separately. |
| Chinese / English | Switch language without reloading data. Hover over controls for explanations. |
| Advanced console | A Python console remains available to experienced NumPy/napari users. |

<table><tr><td width="50%"><img src="assets/strata-overlay.jpg" alt="Stratigraphic labels over seismic data"><br>Stratigraphic label overlays</td><td width="50%"><img src="assets/volume-3d.jpg" alt="3D volume and labels in the English interface"><br>3D volume and label inspection</td></tr></table>

## Get started

1. Install: on Mac, open the DMG and drag the application into Applications; on Windows, run the installer.
2. Click **Import data…** and choose a 3D NPY/NPZ file. Alternatively, extract the demo and select its folder with **Choose data folder…**.
3. Click **Import labels…**, then browse sections with the slider and toggle layer visibility using the eye icons.

<details><summary>Mac drag-to-install window</summary>

![Mac drag-to-Applications installer](assets/install-mac.jpg)

</details>

## Data requirements

- Data must be a nonempty **3D real numeric array**. Select an array key when a NPZ contains multiple arrays.
- Labels must be **3D nonnegative integer IDs**, with exactly the same shape and axis order as the data; 0 is background. A single array can be assigned to faults or strata.
- Standard `labels.npz` keys are `fault_id` and `layer_id`.
- Folder mode accepts `seis.npy` or `seis.npz` with key `seismic`, plus optional `labels.npz`.
- Coordinates are **array indices**; Z is a sample index, not automatically a geographic/depth coordinate. The main import flow does not read SEG-Y directly; convert it to NumPy first.

This application is for viewing and annotation review. It does not generate seismic data, train models or perform automatic geological interpretation. The demo is entirely synthetic.

## Shortcuts and practical notes

| Task | Control |
| --- | --- |
| Browse slices | Bottom slider |
| Change section | `1` / `2` / `3` or orientation dropdown |
| Toggle faults / strata | `F` / `L`, or layer eye icons |
| Adjust transparency | Select a label layer, then opacity |
| Learn a control | Hover over it |

Data can be opened without labels. Label shape/axis mismatches must be fixed before import; the viewer does not align, transpose or resample them automatically. Large datasets require sufficient RAM and GPU memory. NPY data may be memory-mapped; compressed NPZ arrays are decompressed into memory. Use 2D slices first if 3D rendering is slow. Ordinary import/display is local; do not attach sensitive survey data to public issues.

## Feedback and support

If this viewer saves you time, please consider a **⭐ Star** so other seismic, geoscience and annotation practitioners can find it.

[Report a bug or suggest a feature](https://github.com/findLink/seismic-data-viewer-app/issues/new). Include app version, OS, GPU, array shape/dtype and reproducible steps; use synthetic data when possible.

## Licensing

Personal and commercial use is permitted under [LICENSE.txt](LICENSE.txt). Redistribution/resale of the proprietary application requires separate rights-holder permission. Applicable third-party rights take precedence. The app uses napari, PySide6/Qt, NumPy, VisPy and other components; their notices and library-replacement instructions are bundled with the app. Platform-specific third-party source archives in Releases are compliance materials, **not the application's complete source code**.
