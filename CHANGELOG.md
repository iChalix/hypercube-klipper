# Changelog

All notable changes to this Hypercube Klipper configuration will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.0] - 2025-11-08

### Initial Release

This is the first public release of the Hypercube CoreXY Klipper configuration featuring a multi-MCU setup with advanced features.

### Hardware Configuration

#### Microcontrollers
- **Main MCU**: RAMPS-based Arduino Mega 2560 for X/Y motion control
- **Z-board MCU**: Dedicated Arduino Mega 2560 for dual Z-axis control
- **Aux-board MCU**: Dedicated Arduino Mega 2560 for heating and extruder control
- **Cartographer MCU**: Advanced probe system with ADXL345 accelerometer

#### Motion System
- CoreXY kinematics with 290mm × 295mm × 270mm build volume
- TMC2130 stepper drivers with SPI communication on all axes
- X-axis: Sensorless homing with stallguard (SGT: 5)
- Y-axis: Sensorless homing with stallguard (SGT: 4)
- Dual Z-axis motors with automatic tilt adjustment
- Rotation distances optimized for Hypercube mechanics

### Features

#### Probing & Leveling
- **Cartographer Probe**: High-precision inductive probe with temperature compensation
- **Bed Mesh**: 20×20 point mesh with adaptive margins
- **Z-Tilt Adjustment**: 6-point automatic leveling for dual Z motors
- **Axis Twist Compensation**: 5-point gantry twist correction
- **Endstop Phase Detection**: Enhanced repeatability for Z-homing

#### Temperature Management
- Extruder: E3D-compatible with custom NTC 3950 thermistor (max 270°C)
- Heated bed: EPCOS 100K thermistor with PID control (max 130°C)
- PID tuning pre-configured for both extruder and bed
- Temperature monitoring for Cartographer probe

#### Cooling System
- Part cooling fan with PWM control
- Extruder cooling fan (heater-activated)
- **Temperature-controlled stepper cooling**:
  - XY stepper fan (target: 40°C, speed: 0.3-0.6)
  - Z stepper fan (target: 40°C, speed: 0.3-0.5)
  - Auxboard stepper fan (target: 50°C, speed: 0.2-0.4)

#### Advanced Features
- **Input Shaping**: Calibrated with ADXL345 accelerometer
  - X-axis: EI shaper @ 102.8 Hz
  - Y-axis: 2HUMP_EI shaper @ 86.2 Hz
- **Resonance Testing**: Multi-point probe configuration
- **Firmware Retraction**: Pre-configured (4mm @ 50mm/s)
- **G-code Arcs**: Enabled with 1.0mm resolution
- **Filament Sensor**: Runout detection on main board
- **Virtual SD Card**: Support for printing from Raspberry Pi

#### Print Management Macros

##### Core Print Control
- `START`: Automated print start sequence
  - Homes all axes
  - Performs bed mesh calibration
  - Draws priming line
  - Enables filament sensor
- `STOP`: Print end sequence with heater shutdown and park
- `PAUSE`: Intelligent pause with toolhead parking
- `RESUME`: Resume with automatic retraction compensation
- `CANCEL_PRINT`: Safe print cancellation with cleanup

##### Filament Management
- `LOAD_FILAMENT [TEMP=215]`: Automated filament loading
  - Heats to specified temperature
  - Loads 100mm fast, then purges 40mm slowly
- `UNLOAD_FILAMENT [TEMP=215]`: Safe filament unloading
  - Includes anti-stringing retraction sequence
  - Slow extraction for clean removal
- `M600`: Filament change macro for mid-print swaps

#### Performance Settings
- Maximum velocity: 200 mm/s
- Maximum acceleration: 3000 mm²/s
- Maximum Z velocity: 5 mm/s
- Maximum Z acceleration: 30 mm²/s

#### Safety Features
- Minimum extrusion temperature: 160°C
- Maximum extrusion cross-section: 50mm²
- Maximum extrusion-only distance: 150mm
- Temperature limits enforced on all heaters
- Proper current limits on all stepper drivers:
  - XY motors: 0.9A run / 0.3A hold
  - Z motors: 0.7A run / 0.4A hold
  - Extruder: 0.8A run

### Calibration Data

The following calibration values are included:

- **Extruder PID**: Kp=19.536, Ki=0.716, Kd=133.201
- **Bed PID**: Kp=60.403, Ki=1.768, Kd=515.957
- **Cartographer Z-offset**: 0.00 (probe), -0.05 (touch mode)
- **Cartographer Backlash**: 0.00337mm
- **Axis Twist Compensation**: 5-point correction across X-axis
- **Endstop Phase**: Configured for consistent Z-homing

### Documentation

- Comprehensive README.md with installation instructions
- Detailed CLAUDE.md for AI-assisted development
- Pin mapping documentation for Arduino Mega boards
- Safety guidelines and calibration notes

### Notes

This configuration is optimized for a Hypercube CoreXY printer with:
- TMC2130 drivers on all axes
- Cartographer probe system
- Multi-MCU distributed control architecture
- RAMPS 1.4 or compatible boards

### Known Considerations

- Serial port paths need to be updated for your specific system
- Input shaper values are calibrated for this specific machine
- PID values may need retuning after hardware changes
- Sensorless homing sensitivity (SGT values) may require adjustment based on mechanical friction

---

[1.0.0]: https://github.com/iChalix/hypercube-klipper/releases/tag/v1.0.0
