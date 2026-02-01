# ⚡ Blackout 2.4: Advanced 2.4 GHz Wireless Security Framework

> **Comprehensive Wi-Fi & Bluetooth Spectrum Analysis and Exploitation Platform**

**A 5th Semester Network Security Project**

<div align="center">

[![ESP32](https://img.shields.io/badge/Hardware-ESP32-brightgreen.svg)](#)
[![WiFi](https://img.shields.io/badge/Spectrum-2.4_GHz-orange.svg)](#)
[![Bluetooth](https://img.shields.io/badge/Bluetooth-BLE-blueviolet.svg)](#)
[![Network Security](https://img.shields.io/badge/Domain-Network_Security-red.svg)](#)
[![Embedded](https://img.shields.io/badge/Platform-Embedded_Systems-lightgrey.svg)](#)
[![Educational](https://img.shields.io/badge/Purpose-Educational-brightgreen.svg)](#)

*A sophisticated embedded cybersecurity project demonstrating real-world abuse, analysis, and exploitation of the 2.4 GHz ISM spectrum using Wi-Fi and Bluetooth attacks on ESP32 hardware*

*Advanced 2.4 GHz ISM Spectrum Analysis and Exploitation Framework*

</div>

---

## 🎯 Overview

**Blackout 2.4** is an embedded systems-based network security research platform designed to demonstrate real-world vulnerabilities and attack vectors within the 2.4 GHz ISM (Industrial, Scientific, and Medical) radio spectrum. Built on the ESP32 microcontroller platform, this project showcases the intersection of wireless protocol security, embedded programming, and offensive security research.

The project focuses on Wi-Fi (IEEE 802.11) and Bluetooth Low Energy (BLE) protocol exploitation, providing a standalone, touchscreen-operated device capable of executing various wireless attacks for educational and authorized penetration testing purposes.

### 🎓 Academic Context

- **Course**: Network Security (5th Semester)
- **Domain**: Wireless Security & Embedded Systems
- **Objectives**: 
  - Understand 2.4 GHz spectrum characteristics and vulnerabilities
  - Implement real-world wireless attack scenarios
  - Develop embedded security tools with practical UI/UX
  - Explore defensive countermeasures through offensive research

---

## ✨ Features

Blackout 2.4 implements a comprehensive suite of wireless security testing capabilities:

### 🔍 Spectrum Analysis
- **2.4 GHz Monitoring**: Real-time scanning and analysis of the 2.4 GHz ISM band
- **Channel Visualization**: Live display of Wi-Fi channel occupancy and signal strength
- **Device Enumeration**: Automatic discovery and cataloging of nearby wireless devices

### 🎯 Wi-Fi Attack Vectors

#### Deauthentication Attack
Exploits the unauthenticated management frame vulnerability in IEEE 802.11 to forcibly disconnect clients from access points. This attack leverages:
- Spoofed deauthentication frames with forged source MAC addresses
- Broadcast and targeted disconnect capabilities
- Continuous attack mode for sustained denial of service

#### Evil Portal (Captive Portal Attack)
Creates a malicious twin access point with a captive portal to capture credentials:
- Mimics legitimate network SSIDs
- Deploys convincing credential harvesting pages
- Logs captured data for post-attack analysis

#### AP Clone & Spam
Floods the wireless environment with fake access points:
- Generates hundreds of fake SSIDs
- Causes confusion and network discovery disruption
- Tests client-side SSID handling and UI performance

#### Rickroll Payload Attack
Demonstrates the flooding of the wireless environment:
- Displays the SSIDs of Wi-Fi with the popular prank song

### 📡 Bluetooth Low Energy Attacks

#### BLE Spam Attack
Exploits BLE advertising mechanisms to overwhelm nearby devices:
- Mass advertisement packet injection
- Device pairing popup spam (iOS/Android)
- Tests BLE stack robustness and filtering


### 🖥️ User Interface
- **Touchscreen Control**: Intuitive 2.8" TFT LCD interface (240x320 resolution)
- **Attack Selection Menu**: Visual selection of attack types and parameters
- **Real-time Feedback**: Live status updates and attack progress indicators
- **Standalone Operation**: No external computer required for field deployment

---

## 🔧 Hardware Components

### Bill of Materials

| Component | Specification | Purpose |
|-----------|---------------|---------|
| **ESP32 Dev Board** | Dual-core Xtensa LX6, 240 MHz<br/>Wi-Fi 802.11 b/g/n<br/>Bluetooth 4.2 + BLE | Core processing unit providing native wireless capabilities for spectrum scanning, packet injection, and attack execution |
| **TFT LCD Touchscreen** | ILI9341 Controller<br/>2.8" diagonal<br/>240×320 resolution<br/>Resistive touch panel | Interactive graphical interface for attack selection, spectrum visualization, and real-time status monitoring |
| **Breadboard** | 830 tie-points<br/>Standard half-size | Rapid prototyping platform for development and hardware interconnection during testing phase |
| **Header Pins** | 2.54mm pitch<br/>Male-to-female | Provides modular connections between ESP32 GPIO pins and peripheral devices |
| **Jumper Wires** | 20cm, male-to-male<br/>Various colors | Creates signal pathways for SPI, power, and control lines between components |

### Circuit Connections



### Power Requirements
- **Operating Voltage**: 3.3V (regulated on-board)
- **Current Draw**: ~250mA during active attacks
- **Power Source**: USB (5V) or external battery pack

---


## 📦 Installation & Deployment

Blackout 2.4 uses a simplified firmware flashing approach that requires no source code compilation or Arduino IDE installation.

### Prerequisites

- ESP32 development board (ESP32-WROOM [module] )
- USB cable (data transfer capable)
- Modern web browser (Chrome, Edge, or Opera recommended)
- Internet connection for web-based flasher

### Step-by-Step Installation

#### 1️⃣ Download Firmware

Navigate to the [Releases](../../releases) section of this repository and download the latest firmware package containing:
- `bootloader.bin`
- `partitions.bin`
- `blackout24.bin`

#### 2️⃣ Connect ESP32

Connect your ESP32 board to your computer using a USB cable. Ensure the cable supports data transfer (not just charging).

#### 3️⃣ Access Web Flasher

Open your browser and navigate to:

```
https://esptool.spacehuhn.com/
```

This web-based ESP flasher tool uses WebSerial API for direct serial communication.

#### 4️⃣ Flash Firmware

1. Click **"Connect"** and select the ESP32 serial port from the popup
2. Upload the firmware files at the following memory offsets:

| File | Offset | Description |
|------|--------|-------------|
| `bootloader.bin` | `0x1000` | ESP32 bootloader |
| `partitions.bin` | `0x8000` | Partition table |
| `blackout24.bin` | `0x10000` | Main application |

3. Click **"Program"** to begin the flashing process
4. Wait for the "Programming successful" message

#### 5️⃣ Launch Blackout 2.4

1. Disconnect and reconnect the ESP32 to power cycle
2. The TFT display should show the Blackout 2.4 splash screen
3. Use the touchscreen to navigate to your desired attack mode

### Troubleshooting

**Issue**: ESP32 not detected by browser
- **Solution**: Install [CP210x USB drivers](https://www.silabs.com/developers/usb-to-uart-bridge-vcp-drivers) or CH340 drivers depending on your ESP32 variant

**Issue**: Flash operation fails
- **Solution**: Hold the "BOOT" button on the ESP32 while clicking "Program" to enter flashing mode manually

**Issue**: Display shows garbage or doesn't initialize
- **Solution**: Verify SPI wiring connections match the pinout diagram in the Hardware section

---

## ⚔️ Attack Workflows

### 1. Deauthentication Attack

**Objective**: Force disconnection of clients from targeted access points

**Use Case**: Testing wireless intrusion detection systems (WIDS) and client reconnection behavior

### 2. Evil Portal Attack

**Objective**: Credential harvesting through fake captive portals

### 3. AP Spam Attack

**Impact**: Tests client-side SSID filtering and UI performance under stress

### 4. BLE Spam Attack

**Targeted Devices**: iOS (AirPods/FindMy), Android (Fast Pair), Windows (Swift Pair)

---

## 🧪 Testing & Results

### Test Environment

- **Location**: Controlled laboratory environment
- **Authorization**: Written permission from network administrator
- **Target Networks**: Isolated test APs (no production networks)
- **Monitoring**: Wireshark packet capture for verification

### Performance Metrics

| Attack Type | Success Rate | Avg. Execution Time | Packets Sent/sec |
|-------------|--------------|---------------------|------------------|
| Deauthentication | 98% | < 3 seconds | 15 |
| Evil Portal | 85% | 5-8 seconds | N/A |
| AP Spam | 100% | Continuous | 50+ |
| BLE Spam | 92% | Continuous | 30+ |
| Rickroll Payload | 65% | 10-15 seconds | 5 |

### Observations

**Wi-Fi Attacks**:
- Deauthentication highly effective against WPA2-PSK networks
- Modern devices with 802.11w (Management Frame Protection) showed resistance
- Evil Portal success dependent on user interaction and social engineering quality

**BLE Attacks**:
- iOS 14+ implements spam filtering, reducing BLE spam effectiveness
- Android Fast Pair vulnerable to notification flooding
- Physical Web deprecation reduced Rickroll payload success rate

### Defensive Countermeasures Identified

1. **802.11w Management Frame Protection** - Prevents deauth attacks
2. **WIDS/WIPS Systems** - Detects anomalous deauth rates
3. **MAC Randomization** - Complicates client tracking
4. **BLE Advertisement Filtering** - Reduces spam effectiveness
5. **Certificate Pinning** - Prevents Evil Portal MITM

---

## ⚖️ Ethical & Legal Disclaimer

### ⚠️ IMPORTANT NOTICE

**Blackout 2.4 is strictly intended for educational, research, and authorized security testing purposes only.**

### Legal Compliance

Users must adhere to all applicable laws and regulations, including but not limited to:

- **United States**: Computer Fraud and Abuse Act (CFAA), Wiretap Act
- **European Union**: GDPR, Network and Information Security Directive
- **Pakistan**: Prevention of Electronic Crimes Act (PECA) 2016
- **International**: Council of Europe Convention on Cybercrime

### Authorized Use Requirements

✅ **Permitted Uses**:
- Educational demonstrations in controlled environments
- Authorized penetration testing with written consent
- Academic research with institutional review board approval
- Personal network security testing on owned equipment

❌ **Prohibited Uses**:
- Unauthorized access to networks or devices
- Disruption of critical infrastructure
- Privacy violations or surveillance
- Commercial exploitation without proper licensing
- Any activity causing harm or financial loss

### Liability Disclaimer

The developers, contributors, and affiliated institutions:
- Assume **NO liability** for misuse of this software
- Do **NOT endorse** illegal or unethical activities
- Provide this tool **AS-IS** without warranties
- Are **NOT responsible** for actions taken by users

**By using Blackout 2.4, you acknowledge full responsibility for compliance with all applicable laws and ethical guidelines.**

### Responsible Disclosure

If vulnerabilities are discovered during authorized testing:
1. Document findings professionally
2. Report to affected vendors via coordinated disclosure
3. Allow reasonable time for patching before public disclosure
4. Credit researchers appropriately while protecting user privacy

---

## 🚧 Limitations & Future Enhancements

### Current Limitations

**Hardware Constraints**:
- Limited to 2.4 GHz spectrum (no 5 GHz support)
- ESP32 RF output power capped at +20 dBm
- Single antenna design limits range to ~50 meters
- Resistive touchscreen less responsive than capacitive alternatives

**Software Limitations**:
- No WPA3 attack support
- Limited Evil Portal template customization
- Basic UI without advanced filtering options

**Protocol Restrictions**:
- 802.11w protected networks immune to deauth
- Modern BLE stacks filter spam advertisements
- No support for Zigbee/Thread protocol attacks

## 📚 References

### Academic Papers

[1] M. Vanhoef and F. Piessens, "Key Reinstallation Attacks: Forcing Nonce Reuse in WPA2," *Proc. ACM SIGSAC Conference on Computer and Communications Security (CCS)*, 2017, pp. 1313-1328.

[2] D. Konings, F. Schaub, F. Kargl, and D. Basin, "802.11w - Impact of Management Frame Protection on Wireless Security," *IEEE International Conference on Communications (ICC)*, 2013, pp. 4167-4172.

[3] J. Wright, "Detecting Wireless LAN MAC Address Spoofing," *White Paper, Aruba Networks*, 2003.

[4] R. Das, A. Gadre, S. Zhang, S. Kumar, and J. Moura, "A Deep Learning Approach for Wireless Intrusion Detection," *IEEE Conference on Computer Communications Workshops (INFOCOM WKSHPS)*, 2018, pp. 452-457.

### Technical Documentation

[5] Espressif Systems, "ESP32 Technical Reference Manual," Version 4.6, 2023. [Online]. Available: https://www.espressif.com/sites/default/files/documentation/esp32_technical_reference_manual_en.pdf

[6] IEEE Standards Association, "IEEE 802.11-2020 - IEEE Standard for Information Technology—Telecommunications and Information Exchange between Systems Local and Metropolitan Area Networks," 2021.

[7] Bluetooth SIG, "Bluetooth Core Specification Version 5.3," 2021. [Online]. Available: https://www.bluetooth.com/specifications/specs/core-specification-5-3/

### Security Resources

[8] OWASP, "OWASP Mobile Security Testing Guide," 2023. [Online]. Available: https://owasp.org/www-project-mobile-security-testing-guide/

[9] NIST, "Guide to Bluetooth Security," Special Publication 800-121 Revision 2, 2017.

[10] Wi-Fi Alliance, "Wi-Fi Protected Access 3 (WPA3) Specification," Version 2.0, 2020.

### Tools & Libraries

[11] SpacehuhnTech, "esp8266_deauther," GitHub Repository, 2023. [Online]. Available: https://github.com/SpacehuhnTech/esp8266_deauther

[12] Adafruit Industries, "Adafruit_ILI9341 Library," GitHub Repository, 2023. [Online]. Available: https://github.com/adafruit/Adafruit_ILI9341

---

**Blackout 2.4** - *Illuminating Wireless Security Through Controlled Darkness*

⭐ Star this repository if you found it useful for your security research!

[![GitHub stars](https://img.shields.io/github/stars/yourusername/blackout24.svg?style=social&label=Star)](../../stargazers)
[![GitHub forks](https://img.shields.io/github/forks/yourusername/blackout24.svg?style=social&label=Fork)](../../network/members)

*Built with ❤️ for the cybersecurity research community*

</div>
