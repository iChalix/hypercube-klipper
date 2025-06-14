# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Klipper 3D printer configuration repository for a custom Hypercube 3D printer. The Hypercube is a CoreXY design, and this configuration uses multiple microcontrollers for distributed control.

## Key Hardware Configuration

- **Motion System**: CoreXY kinematics with TMC2130 stepper drivers
- **MCU Architecture**:
  - Main MCU: Controls X/Y movement
  - Z-board MCU: Controls dual Z-axis motors
  - Aux-board MCU: Controls heaters and extruder
- **Build Volume**: 290mm × 295mm × 270mm
- **Features**: Sensorless homing (X/Y), dual Z motors with tilt adjustment, filament sensor

## Working with Klipper Configuration

### Configuration File Structure

The main configuration is in `/config/printer.cfg`. Key sections include:

- `[mcu]` sections: Define microcontroller connections
- `[stepper_*]` sections: Motor configuration
- `[tmc2130 stepper_*]` sections: Stepper driver settings
- `[extruder]` and `[heater_bed]`: Temperature control
- `[gcode_macro *]`: Custom G-code macros for print operations

### Common Tasks

**Testing Configuration Changes**:
Since this is a live printer configuration, changes should be made carefully. Klipper will automatically reload when printer.cfg is saved.

**Adding New Features**:
- New sensors or peripherals require defining their pin mappings
- Use the Arduino pin aliases (e.g., `ar54`) defined in `[board_pins arduino-mega]`
- Each MCU has its own namespace (e.g., `zboard:ar46` for pins on the Z board)

**Modifying Macros**:
The configuration includes several important macros:
- `START`: Print start sequence with priming line
- `STOP`: Print end sequence
- `LOAD_FILAMENT`/`UNLOAD_FILAMENT`: Filament change procedures
- `M600`: Filament change during print

### Important Klipper Concepts

- **Pin Definitions**: Use format `mcu:pin` for specific MCU, or just `pin` for main MCU
- **Rotation Distance**: Replaces steps/mm in traditional firmware
- **Sensorless Homing**: Uses TMC2130's stallguard feature (see `driver_SGT` settings)
- **Temperature Fans**: Automatically control cooling based on stepper driver temperatures

## Safety Considerations

When modifying this configuration:
- Never exceed max temperatures (Extruder: 270°C, Bed: 130°C)
- Maintain proper current settings for TMC2130 drivers
- Test motion commands at low speeds first
- The Z-axis has automatic tilt adjustment - ensure both motors are properly configured