# Secure BLE Beacon

A secure and configurable BLE beacon implementation for ESP32 using ESP-IDF framework, featuring encryption, persistent storage, and compatibility with both iOS and Android devices.

## Features

- **Secure Broadcasting**: AES-encrypted beacon data transmission
- **iBeacon Compatible**: Fully compliant with Apple iBeacon specifications
- **Persistent Configuration**: Stores settings in NVS flash
- **Configurable Parameters**: 
  - UUID, Major, Minor values
  - TX power level
  - Broadcasting interval
  - Encryption keys
- **Comprehensive Logging**: Multiple log levels for debugging
- **Power Efficient**: Optimized BLE stack configuration

## Requirements

### Hardware
- ESP32 development board (ESP32-DevKitC or ESP32-WROOM-32)
- USB cable for programming and power
- BLE scanner device (smartphone/tablet)
- Optional: External antenna, JTAG debugger

### Software
- ESP-IDF (latest stable version)
- CMake build system
- BLE Scanner apps:
  - Android: nRF Connect, BLE Scanner
  - iOS: LightBlue, Beacon Scanner

## Project Structure
```
secure_ble_beacon/
├── CMakeLists.txt
├── main/
│   ├── CMakeLists.txt
│   ├── include/
│   │   ├── beacon_config.h
│   │   ├── beacon_crypto.h
│   │   └── beacon_storage.h
│   ├── beacon_main.c
│   ├── beacon_crypto.c
│   ├── beacon_storage.c
│   └── Kconfig.projbuild
├── sdkconfig.defaults
└── README.md
```

## Building and Flashing

1. Set up ESP-IDF environment:
```bash
. $IDF_PATH/export.sh  # Linux/macOS
%IDF_PATH%\export.bat  # Windows
```

2. Configure the project:
```bash
idf.py menuconfig
```

3. Build:
```bash
idf.py build
```

4. Flash:
```bash
idf.py -p (PORT) flash
```

## Configuration

### Beacon Settings
- UUID: Custom 128-bit identifier
- Major: 16-bit value for group identification
- Minor: 16-bit value for individual identification
- TX Power: Adjustable signal strength
- Broadcast Interval: Configurable advertising interval

### Security Settings
- AES-256 encryption for secure data transmission
- Secure key storage in NVS
- Optional payload encryption

### Logging Levels
- ERROR: Critical issues
- WARN: Warning conditions
- INFO: General operational information
- DEBUG: Detailed debugging information

## Testing

1. Flash the firmware to ESP32
2. Use BLE scanner apps to verify:
   - Beacon detection
   - Signal strength
   - Data accuracy
   - Encryption functionality

## Power Optimization

The beacon is optimized for power efficiency through:
- BLE-only mode
- Configurable TX power
- Optimized broadcasting intervals

## Security Considerations

- Encryption keys are stored securely in NVS
- Regular key rotation recommended
- Encrypted payload options
- Protected configuration interface
