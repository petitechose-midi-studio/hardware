# MIDI Studio - Hardware Design

Open-source hardware design files for the MIDI Studio controller.

**Teensy 4.1 based MIDI controller with ILI9341 display, 10 rotary encoders, and 15 buttons.**

---

## Hardware Specifications

### Core Components

- **MCU:** Teensy 4.1 (ARM Cortex-M7 @ 600 MHz)
- **RAM:** 8 MB PSRAM (**mandatory** - soldered on underside pads)
- **Display:** ILI9341 2.8" TFT (320x240, SPI)
- **Encoders:**
  - 8x Bourns PEC11R rotary encoders (24 PPR, smooth, with push button)
  - 1x Bourns PEC11R rotary encoder (24 PPR, detented, with push button)
  - 1x E38S6G5 optical encoder (600 PPR, high-resolution)
- **Buttons:** 15x tactile buttons (6x panel-mounted + 9x via multiplexer)
- **Multiplexer:** CD74HC4067 (16-channel analog multiplexer)
- **Connectivity:** USB MIDI (USB-B connector)

### Display Interface (SPI)

- CS = Pin 28
- DC = Pin 0
- RST = Pin 29
- MOSI = Pin 26
- SCK = Pin 27
- MISO = Pin 1
- Firmware-configured SPI speed: 50 MHz

### Power

- USB-powered (5V)
- Teensy 4.1 regulates to 3.3V for peripherals

---

## Repository Contents

### `pcb/`

KiCad PCB design files and manufacturing outputs.

```
pcb/kicad/
midi-studio.kicad_pro      # KiCad project
midi-studio.kicad_sch      # Schematic
midi-studio.kicad_pcb      # PCB layout
midi-studio.step           # 3D model
gerbers/                   # Gerber files for PCB fabrication
bom/                       # Bill of Materials + CPL
pdf/                       # Schematic and assembly drawings (PDF)
```

**PCB Specifications:**
- Layers: 2-layer PCB
- Thickness: 1.6mm
- Surface finish: HASL or ENIG
- Compatible: JLCPCB, PCBWay, OSH Park

---

### `cnc/`

CNC machining files for enclosure fabrication (G-code, DXF).

---

### `keyshot/`

Photorealistic renders for documentation and marketing.

---

## Software Tools

This project was designed using the following software:

- **KiCad** (latest stable version) - PCB schematic and layout design
- **Aspire 12.5** - CNC toolpath generation and G-code export
- **OnShape** - 3D mechanical enclosure design
- **KeyShot** - Photorealistic rendering

All design files are provided in their native formats as well as exported to common interchange formats (PDF, STEP, DXF, Gerber) for maximum compatibility.

---

## 3D Model (OnShape)

**Public OnShape CAD Model:**

**https://cad.onshape.com/documents/a6b73f1c7a20e07680bfab81**

Includes:
- Complete enclosure design
- Mounting holes for all components
- Panel cutouts
- Export-ready for 3D printing or CNC

---

## Bill of Materials (BOM)

### Electronic Components

| Component | Quantity | Part Number | Notes |
|-----------|----------|-------------|-------|
| Teensy 4.1 | 1 | TEENSY41 | **Must have 8MB PSRAM** |
| ILI9341 Display | 1 | 2.8" 320x240 | SPI interface |
| Rotary Encoder (smooth) | 8 | Bourns PEC11R-4220F-S0024 | 24 PPR + button |
| Rotary Encoder (detented) | 1 | Bourns PEC11R-4220K-S0024 | 24 PPR + button |
| Optical Encoder | 1 | E38S6G5 | 600 PPR |
| Tactile Buttons (panel) | 6 | 6mm tactile switch | Panel-mounted |
| Tactile Buttons (PCB) | 9 | 6mm tactile switch | PCB-mounted |
| CD74HC4067 | 1 | CD74HC4067 | Multiplexer IC |
| USB-B Connector | 1 | Standard USB-B | Chassis-mounted |

**Estimated Cost:** ~€80-100 (excluding enclosure)

---

## Manufacturing

### PCB Fabrication

**Recommended:** JLCPCB

**Gerber Files:** `pcb/kicad/gerbers/`

---

### CNC Machining

**Materials:**
- Front panel: Plywood 5mm + 2 thin wood layers 0.6mm
- Bottom panel: Plywood 5mm
- Enclosure: Birch plywood 12mm

---

## Assembly Guide

1. **PCB Assembly** - Solder components, install Teensy 4.1 (verify PSRAM!)
2. **Enclosure Prep** - CNC mill or 3D print parts
3. **Final Assembly** - Mount display, encoders, buttons, PCB
4. **Testing** - Flash firmware, test all inputs

Detailed assembly instructions: See wiki (coming soon)

---

## Related Repositories

- **[Core Firmware](https://github.com/petitechose-midi-studio/core)** - Teensy 4.1 firmware
- **[Bitwig Plugin](https://github.com/petitechose-midi-studio/plugin-bitwig)** - Bitwig Studio extension

---

## License

Licensed under **CERN Open Hardware Licence Version 2 - Strongly Reciprocal (CERN-OHL-S-2.0)**.

### What This Means

**✓ You MAY:**
- Manufacture for **personal use**
- Modify and improve the design
- Share modifications (same license)

**⚠ You MUST (if commercial):**
- Publish all modifications
- Keep the same license
- Provide attribution

**✗ You MAY NOT:**
- Sell without publishing design files

See [LICENSE](LICENSE) for full terms.

---

## Important Notes

### PSRAM is Mandatory

**⚠ Teensy 4.1 MUST have 8MB PSRAM** soldered on underside pads.

Without PSRAM, firmware will NOT run.

Purchase: https://www.pjrc.com/store/psram.html

---

## Support

**Issues:** GitHub Issues

**Commercial Licensing:** <contact@petitechose.audio>

---

**Built by petitechose.audio**
