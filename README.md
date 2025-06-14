# Hypercube Klipper Configuration

This repository contains the Klipper configuration for a custom-built Hypercube 3D printer.

## Printer Specifications

- **Design**: Hypercube CoreXY
- **Build Volume**: 290mm × 295mm × 270mm
- **Control System**: Klipper firmware with multiple MCUs
- **Stepper Drivers**: TMC2130 with SPI communication
- **Features**:
  - Sensorless homing on X/Y axes
  - Dual Z motors with automatic tilt adjustment
  - Filament runout sensor
  - Temperature-controlled cooling for stepper drivers
  - Input shaping for vibration compensation

## Hardware Configuration

### Microcontrollers
- **Main MCU**: RAMPS-based board controlling X/Y movement
- **Z-board MCU**: Dedicated controller for dual Z-axis motors
- **Aux-board MCU**: Controls heating elements and extruder

### Motion System
- **Kinematics**: CoreXY
- **X/Y Motors**: TMC2130 drivers with sensorless homing
- **Z Motors**: Dual motors with TMC2130 drivers
- **Extruder**: TMC2130 driver

## Installation

1. Install Klipper on your Raspberry Pi following the [official documentation](https://www.klipper3d.org/Installation.html)
2. Clone this repository:
   ```bash
   git clone https://github.com/iChalix/hypercube-klipper.git
   ```
3. Copy `printer.cfg` to your Klipper config directory:
   ```bash
   cp hypercube-klipper/config/printer.cfg ~/klipper_config/
   ```
4. Update the MCU serial paths in `printer.cfg` to match your system
5. Restart Klipper

## Configuration Notes

### MCU Serial Connections
The configuration uses specific USB paths that need to be updated for your system:
- Main MCU: `/dev/serial/by-path/platform-3f980000.usb-usb-0:1.1.3:1.0`
- Z-board: `/dev/serial/by-path/platform-3f980000.usb-usb-0:1.1.2:1.0`
- Aux-board: `/dev/serial/by-path/platform-3f980000.usb-usb-0:1.2:1.0`

Find your serial paths using:
```bash
ls -l /dev/serial/by-path/
```

### Key Features

#### Sensorless Homing
X and Y axes use TMC2130 stallguard for sensorless homing. Adjust `driver_SGT` values if homing sensitivity needs tuning.

#### Automatic Bed Leveling
The printer uses dual Z motors with `[z_tilt]` configuration for automatic tilt adjustment. Run `Z_TILT_ADJUST` before printing.

#### Temperature-Controlled Fans
Three cooling fans automatically manage stepper driver temperatures:
- XY stepper fan (target: 40°C)
- Z stepper fan (target: 40°C)
- Auxboard stepper fan (target: 50°C)

## G-Code Macros

### Print Control
- `START`: Initialize print with priming line
- `STOP`: End print and park toolhead
- `PAUSE`: Pause print and park
- `RESUME`: Resume from pause
- `CANCEL_PRINT`: Cancel and cleanup

### Filament Management
- `LOAD_FILAMENT TEMP=220`: Load filament at specified temperature
- `UNLOAD_FILAMENT TEMP=220`: Unload filament
- `M600`: Filament change during print

## Calibration

1. **PID Tuning**: Already calibrated for extruder and bed
2. **Rotation Distance**: Pre-configured for standard hardware
3. **Input Shaper**: Configured with MZV shaper (X: 46.62Hz, Y: 55.55Hz)
4. **Pressure Advance**: Uncomment and adjust in `[extruder]` section if needed

## Safety

- Maximum temperatures are set to safe limits (Extruder: 270°C, Bed: 130°C)
- TMC2130 current settings are configured for reliable operation
- Minimum extrude temperature set to 160°C to prevent cold extrusion

## License

This configuration is provided as-is for the Hypercube 3D printer community.