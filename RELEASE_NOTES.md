# Release v1.0.0 - Initial Public Release

**Release Date**: November 8, 2025

## Overview

This is the initial public release of a fully-featured Klipper configuration for a custom Hypercube CoreXY 3D printer. The configuration showcases a professional multi-MCU setup with advanced features including sensorless homing, automatic bed leveling, input shaping, and comprehensive temperature management.

## Highlights

### 🎯 Multi-MCU Architecture
- 4 microcontrollers working in harmony
- Distributed control for optimal performance
- Main MCU (XY), Z-board (dual Z), Aux-board (heating), Cartographer (probing)

### 🔧 Advanced Motion Control
- **CoreXY kinematics** with 290×295×270mm build volume
- **TMC2130 drivers** with SPI control on all axes
- **Sensorless homing** on X/Y axes using stallguard
- **Dual Z motors** with automatic tilt adjustment

### 📊 Professional Probing System
- **Cartographer probe** with temperature compensation
- **20×20 bed mesh** for precise first layers
- **Axis twist compensation** for gantry alignment
- **6-point Z-tilt** adjustment system

### 🎚️ Input Shaping Calibration
- Fully calibrated with onboard ADXL345 accelerometer
- Optimized EI and 2HUMP_EI shapers
- Reduced ringing and improved print quality

### 🌡️ Intelligent Cooling
- Temperature-controlled fans for all stepper drivers
- Automatic speed adjustment based on driver temperature
- Prevents overheating during long prints

### 🎮 Comprehensive Macros
- **START**: Automated print preparation with bed mesh and priming
- **STOP**: Safe shutdown and parking
- **LOAD_FILAMENT** / **UNLOAD_FILAMENT**: Intelligent filament handling
- **M600**: Mid-print filament change support
- **PAUSE** / **RESUME** / **CANCEL_PRINT**: Full print control

## What's Included

- ✅ Complete printer.cfg with all features configured
- ✅ Comprehensive documentation (README.md, CLAUDE.md)
- ✅ Pre-calibrated PID values
- ✅ Pre-calibrated input shaper settings
- ✅ Safety limits and proper current settings
- ✅ Filament sensor integration
- ✅ Firmware retraction configured

## Technical Specifications

| Component | Configuration |
|-----------|--------------|
| **Kinematics** | CoreXY |
| **Build Volume** | 290 × 295 × 270 mm |
| **Stepper Drivers** | TMC2130 (SPI) |
| **Max Speed** | 200 mm/s |
| **Max Acceleration** | 3000 mm/s² |
| **Extruder Temp** | 270°C max |
| **Bed Temp** | 130°C max |
| **Probe** | Cartographer inductive |

## Installation

```bash
# Clone the repository
git clone https://github.com/iChalix/hypercube-klipper.git

# Copy configuration to Klipper
cp hypercube-klipper/config/printer.cfg ~/klipper_config/

# Update MCU serial paths in printer.cfg
# Restart Klipper
```

## Important Notes

⚠️ **Before using this configuration:**
1. Update MCU serial port paths to match your system
2. Verify pin assignments match your wiring
3. Test motion at low speeds first
4. Re-tune PID values if your hardware differs
5. Adjust sensorless homing sensitivity (SGT) if needed

## Getting Started

1. Follow installation instructions in README.md
2. Update serial port paths in printer.cfg
3. Verify basic motion with low speeds
4. Run `Z_TILT_ADJUST` for bed leveling
5. Create a bed mesh with `BED_MESH_CALIBRATE`
6. Test print with START macro

## Community & Support

This configuration is shared with the Hypercube community. Feel free to:
- Report issues on GitHub
- Suggest improvements
- Share your modifications
- Ask questions in discussions

## Future Enhancements

Potential areas for future development:
- Additional macro refinements
- Alternative probe support
- Expanded sensor integration
- Print time estimation macros

---

**Full Changelog**: See [CHANGELOG.md](CHANGELOG.md) for detailed feature list

**Repository**: https://github.com/iChalix/hypercube-klipper
**License**: MIT (Community shared)
