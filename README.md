# kicad-single-layer-fabrication-exporter
Commercial-grade KiCad plugin for one-click single-layer fabrication PDF export with Edge.Cuts, mirror mode, and automatic manufacturing-ready output.

# ⚡ Ultra Fabrication Exporter

> A KiCad 9 action plugin for one-click fabrication-ready PDF export from the PCB editor.

![KiCad](https://img.shields.io/badge/KiCad-9.0-blue?logo=kicad&logoColor=white)
![Python](https://img.shields.io/badge/Python-3.x-yellow?logo=python&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green)
![Status](https://img.shields.io/badge/Status-stable-brightgreen)

---

## What it does

Ultra Fabrication Exporter adds a toolbar button to the KiCad PCB Editor that exports a clean, print-ready **F.Cu fabrication PDF** in a single click — no fiddling with Plot dialogs.

- Exports **F.Cu** (front copper layer)
- Optionally merges **Edge.Cuts** board outline into the same PDF
- Supports **mirror mode** for toner-transfer PCB production
- Auto-opens the PDF after export
- Lets you pick any output path via a clean dialog

---

## Screenshots

| Dialog | Output PDF | Success |
|--------|-----------|---------|
| <img width="686" height="438" alt="Screenshot 2026-05-03 174608" src="https://github.com/user-attachments/assets/6fbcb731-a13a-4037-96b9-61c1aca93afe" />
 | <img width="888" height="455" alt="Screenshot 2026-05-03 174714" src="https://github.com/user-attachments/assets/7119c81f-1d8b-44d2-94ef-6c9b677d1c31" />
| <img width="547" height="254" alt="Screenshot 2026-05-03 174617" src="https://github.com/user-attachments/assets/17530c69-3f3c-4592-8b57-fa0196ea4031" />
 |

---

## Installation

### Via KiCad Plugin Manager (recommended)

1. Open KiCad → **PCB Editor**
2. Go to **Tools → Plugin and Content Manager**
3. Click **Install from File…**
4. Select the downloaded `.zip` file
5. Click **Apply Pending Changes** and restart if prompted

### Manual

1. Unzip the package into your KiCad third-party plugins directory:

   | OS | Path |
   |----|------|
   | Windows | `%APPDATA%\kicad\9.0\3rdparty\plugins\` |
   | macOS | `~/Library/Preferences/kicad/9.0/3rdparty/plugins/` |
   | Linux | `~/.local/share/kicad/9.0/3rdparty/plugins/` |

2. Restart KiCad PCB Editor — the plugin toolbar button will appear.

---

## Usage

1. Open your `.kicad_pcb` file in the PCB Editor
2. Click the **Ultra Fabrication Exporter** button in the toolbar (or go to **Tools → External Plugins**)
3. In the dialog:
   - Set your output PDF path
   - Toggle **Edge.Cuts**, **Mirror**, and **Auto-open** as needed
4. Click **Export**

The PDF is saved to the specified location and optionally opened automatically.

---

## Options

| Option | Default | Description |
|--------|---------|-------------|
| Output PDF | `<boardname>_Fabrication_FCu.pdf` | Output file path |
| Include Edge.Cuts | ✅ On | Adds the board outline to the PDF |
| Mirror for toner transfer | ❌ Off | Mirrors the layer for iron-on transfer |
| Auto-open PDF | ✅ On | Opens the PDF in your default viewer after export |

---

## Compatibility

| KiCad Version | Status |
|--------------|--------|
| 9.0 | ✅ Supported |
| 8.x | ⚠️ Untested |
| 7.x and below | ❌ Not supported |

---

## File Structure

```
com_atharva_ultrafabricationexporter/
├── metadata.json          # Plugin metadata (KiCad Package Manager)
├── icon.png               # Toolbar icon
└── plugins/
    ├── __init__.py
    ├── fabrication_exporter.py   # ActionPlugin entry point & plot logic
    └── exporter_gui.py           # wx.Dialog UI
```

---

## Development

Built with:
- **`pcbnew`** — KiCad's Python API for plot control
- **`wx`** (wxPython) — GUI dialog
- **`PLOT_CONTROLLER`** — KiCad's layer-by-layer PDF plotter

To modify and reload without restarting KiCad:

```
Tools → Scripting Console → import importlib; importlib.reload(...)
```

---

## License

MIT — free to use, modify, and distribute.

---

## Author

**Atharva** — [matharva357@gmail.com](mailto:matharva357@gmail.com)
