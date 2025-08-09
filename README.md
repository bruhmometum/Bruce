# LORD Board Firmware

**L**ittle **O**ffensive **R**econnaissance **D**evice

A custom Bruce firmware port for the  ESP32-S3 WITH ILI9341 TFT TOUCH.

---

## 🔍 Overview

This firmware is a custom port of the popular Bruce firmware, specifically adapted for the ESP32-S3 hardware configuration with optimized pin mappings and feature support.

## ⚡ Hardware Specifications

### Core Processor
- **Microcontroller**: ESP32-S3 with dual-core Xtensa LX7
- **Flash Memory**: 16MB QSPI Flash
- **PSRAM**: 8MB Octal SPI PSRAM
- **USB Interface**: CH343 USB-Serial converter for programming and debugging

### Display & Input
- **Display**: 2.8" ILI9341 TFT LCD (240×320 pixels)
- **Touch Screen**: XPT2046 resistive touch controller
- **Backlight**: PWM-controlled LED backlight
- **Storage**: MicroSD card slot (shared SPI bus)

### Wireless Communication
- **WiFi**: Built-in ESP32-S3 802.11 b/g/n
- **Bluetooth**: Built-in ESP32-S3 Bluetooth 5.0 LE
- **Sub-GHz Radio**: CC1101 transceiver (315/433/868/915 MHz)
- **2.4GHz Radio**: nRF24L01+ transceiver
- **NFC**: PN532 NFC controller (I²C interface)

### Navigation & Sensors
- **GPS**: NEO-6M GPS module (UART1 interface)
- **Positioning**: Support for GPS, GLONASS, and other GNSS systems

### Infrared Capabilities
- **IR Transmitter**: PWM-controlled IR LED
- **IR Receiver**: Digital IR sensor for signal capture

### Visual Indicators
- **RGB LED**: Onboard WS2812B programmable LED


### Power & Connectivity
- **USB**: USB-C connector for power and data
- **Power Management**: Integrated battery charging circuit
- **Programming**: USB HID support for enhanced device interaction

## 📌 Pin Configuration

### UART Interfaces
| Function | Pin | Description |
|----------|-----|-------------|
| USB-Serial TX | GPIO 43 | CH343 programming interface |
| USB-Serial RX | GPIO 44 | CH343 programming interface |
| GPS TX | GPIO 17 | ESP32 TX1 → GPS RX |
| GPS RX | GPIO 18 | ESP32 RX1 ← GPS TX |

### I²C Bus (PN532 NFC)
| Function | Pin | Description |
|----------|-----|-------------|
| SDA | GPIO 8 | I²C data line |
| SCL | GPIO 16 | I²C clock line |

### Shared VSPI Bus (Display, Touch, SD)
| Function | Pin | Description |
|----------|-----|-------------|
| SCK | GPIO 12 | SPI clock |
| MOSI | GPIO 11 | Master out, slave in |
| MISO | GPIO 13 | Master in, slave out |

### ILI9341 TFT Display
| Function | Pin | Description |
|----------|-----|-------------|
| CS | GPIO 10 | Chip select |
| DC | GPIO 21 | Data/Command select |
| RST | GPIO 18 | Reset |
| BL | GPIO 4 | Backlight control (PWM) |

### XPT2046 Touch Controller
| Function | Pin | Description |
|----------|-----|-------------|
| CS | GPIO 9 | Chip select |
| IRQ | GPIO 7 | Touch interrupt |

### MicroSD Card
| Function | Pin | Description |
|----------|-----|-------------|
| CS | GPIO 5 | Chip select |

### Dedicated HSPI Bus (Radios)
| Function | Pin | Description |
|----------|-----|-------------|
| SCK | GPIO 36 | SPI clock |
| MOSI | GPIO 35 | Master out, slave in |
| MISO | GPIO 37 | Master in, slave out |

### CC1101 Sub-GHz Radio
| Function | Pin | Description |
|----------|-----|-------------|
| SS (CS) | GPIO 38 | Chip select |
| GDO0 | GPIO 6 | Interrupt/status pin |
| GDO2 | GPIO 22 | Additional status pin |

### nRF24L01+ 2.4GHz Radio
| Function | Pin | Description |
|----------|-----|-------------|
| SS (CS) | GPIO 47 | Chip select |
| CE | GPIO 14 | Chip enable |

### Infrared Interface
| Function | Pin | Description |
|----------|-----|-------------|
| IR TX | GPIO 15 | IR transmitter (PWM capable) |
| IR RX | GPIO 2 | IR receiver input |

### Status LEDs
| Function | Pin | Description |
|----------|-----|-------------|
| RGB LED | GPIO 48 | WS2812B data line |


---

## 🛠️ Getting Started

### Prerequisites
- PlatformIO or Arduino IDE
- USB-C cable for programming
- Lord Board hardware

### Installation Steps

1. **Clone the Repository**
   ```bash
   git clone <repository-url>
   cd lord-board-firmware
   ```

2. **Configure PlatformIO**
   - Open the project in PlatformIO
   - The environment is pre-configured as `lord-board`

3. **Build and Upload**
   ```bash
   pio run -e lord-board --target upload
   ```

4. **Serial Monitor**
   ```bash
   pio device monitor -b 115200
   ```

### Configuration

The pin configuration is defined in `pins_arduino.h`. Modify this file if you have hardware variations or custom pin assignments.

---

## 📚 Firmware Features

### Core Capabilities
- **Bruce Firmware Base**: Built on the proven Bruce firmware foundation
- **Multi-Radio Support**: Simultaneous operation of multiple radio interfaces
- **Touch UI**: Intuitive graphical user interface
- **File System**: MicroSD card support for data storage
- **GPS Integration**: Location services and navigation
- **NFC Operations**: Read/write NFC tags and cards
- **IR Control**: Transmit and receive infrared signals
- **USB HID**: Keyboard/mouse emulation and custom HID devices

### Power Management
- **Battery Support**: Integrated charging and power management
- **Sleep Modes**: Multiple power-saving modes
- **Backlight Control**: Automatic and manual brightness adjustment

---

## 🤝 Contributing

This is a community-driven port of Bruce firmware. Contributions are welcome:

### Areas for Contribution
- Hardware driver improvements
- Power optimization
- New feature implementations
- Bug fixes and testing
- Documentation improvements

### Contribution Guidelines
1. Fork the repository
2. Create a feature branch
3. Make your changes with clear commit messages
4. Test thoroughly on actual hardware
5. Submit a pull request with detailed description

### Coding Standards
- Follow existing code style and structure
- Maintain pin mapping centralization
- Include comprehensive comments
- Preserve compatibility with base Bruce firmware where possible

---

## 📄 License

This firmware is based on Bruce firmware and follows its licensing terms. Hardware-specific adaptations for the LORD board are provided as-is for educational and research purposes.

---

## ⚠️ Disclaimer

The LORD board and this firmware are intended for educational, research, and authorized security testing purposes only. Users are responsible for ensuring compliance with all applicable laws and regulations in their jurisdiction.

---

## 🙏 Acknowledgments

- **Bruce Firmware Team**: For the excellent base firmware that made this port possible
- **ESP32 Community**: For extensive documentation and support
- **Hardware Contributors**: For the LORD board design and testing

---

## 📞 Support

For issues, questions, or contributions:
- Open an issue in the repository
- Join the community discussions
- Refer to Bruce firmware documentation for core functionality

---

*LORD - Little Offensive Reconnaissance Device*
