# IODeviceManager

**Cross-Platform Hardware Device Management for ULTRA OS**

IODeviceManager is a unified hardware abstraction layer providing consistent access to scanners, cameras, GPIO, and other I/O devices across Linux, Windows, and macOS through native protocols.

---

## Implemented Categories

### Scanners

Unified scanning API across all major platforms and protocols.

| Protocol | Platform | Description |
|----------|----------|-------------|
| SANE | Linux | Scanner Access Now Easy |
| WIA | Windows | Windows Image Acquisition |
| TWAIN | Windows | Industry standard protocol |
| ICA | macOS | Image Capture Architecture |
| eSCL | Network | AirPrint/driverless scanning |

**Features:** Device enumeration, single/multi-page scanning, resolution/color configuration, scan area definition, preview mode, hot-plug support.

---

### Cameras 

Complete camera ecosystem from webcams to professional DSLRs and network cameras.

| Phase | Type | Protocols |
|-------|------|-----------|
| Phase 1 | USB Webcams | V4L2 (Linux), Media Foundation (Windows), AVFoundation (macOS) |
| Phase 2 | Built-in Webcams | Platform-native APIs |
| Phase 3 | DSLR Cameras | libgphoto2 (Linux), WIA (Windows), ImageCapture (macOS) |
| Phase 4 | Network/IP Cameras | RTSP streaming, ONVIF discovery |

**Features:** Single frame and continuous capture, resolution/format control, exposure/focus/white balance, PTZ controls, multi-stream support, camera discovery (ONVIF/UPnP/mDNS).

---

### GPIO 

Hardware I/O control for embedded platforms via libgpiod wrapper.

**Platforms:** Linux (Raspberry Pi, ARM boards)

**Features:** Digital I/O (read/write), PWM control, interrupt handling, I2C/SPI/UART protocols, high-level abstractions (LED, Button, Servo).

---

## Future Categories

| Category | Status | Planned Protocols |
|----------|--------|-------------------|
| Printer | Planned | CUPS, Windows Print API |
| Audio | Planned | ALSA/PulseAudio, WASAPI, CoreAudio |
| Storage | Planned | USB mass storage |
| Network | Planned | Network interface management |
| Display | Planned | Monitor detection/configuration |
| HID | Planned | Generic HID devices |

---

## Architecture

```
IODeviceManager/
├── include/
│   ├── UltraCanvasIODevice.h           # Base device interface
│   ├── UltraCanvasIODeviceTypes.h      # Types and enumerations
│   ├── UltraCanvasIODeviceManager.h    # Central manager
│   ├── UltraCanvasIODeviceCamera.h     # Camera interface
│   └── UltraCanvasGPIOController.h     # GPIO interface
├── core/
│   ├── UltraCanvasIODevice.cpp
│   ├── UltraCanvasIODeviceManager.cpp
│   └── UltraCanvasIODeviceSupport_eSCL.cpp
└── OS/
    ├── Linux/
    │   ├── UltraCanvasIODeviceSupport_Linux.cpp      # SANE
    │   ├── UltraCanvasIODeviceSupport_Camera.cpp     # V4L2
    │   └── UltraCanvasGPIOSupport_Linux.cpp          # libgpiod
    ├── MSWindows/
    │   └── UltraCanvasIODeviceSupport_Windows.cpp    # WIA/TWAIN
    └── MacOS/
        └── UltraCanvasIODeviceSupport_MacOS.cpp      # ICA


## Technical Stack

- **Language:** C++20
- **Scanner Libraries:** SANE, WIA COM, TWAIN DSM, ImageCapture Framework
- **Camera Libraries:** V4L2, Media Foundation, AVFoundation, libgphoto2, FFmpeg (RTSP)
- **GPIO Library:** libgpiod
- **Build System:** CMake

---

## Design Principles

- Unified API across all platforms and protocols
- Platform-specific code isolated in OS folders
- Plugin-based architecture for extensibility
- Thread-safe device management
- Hot-plug device detection
- Comprehensive error handling

---

## Status

| Component | Linux | Windows | macOS |
|-----------|-------|---------|-------|
| Scanners | ✅ | ✅ | ✅ |
| Webcams | ✅ | ✅ | ✅ |
| DSLR Cameras | ✅ | ✅ | ✅ |
| Network Cameras | ✅ | ✅ | ✅ |
| GPIO | ✅ | — | — |

---

## License

Open Source — Part of the ULTRA OS Project

---

*Developed by Cloverleaf UG*
