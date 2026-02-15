# Sungrow iHomeManager for Home Assistant

Modbus integration for Sungrow iHomeManager in Home Assistant, providing access to grid metrics and EV charger controls that aren't available through standard inverter Modbus communication.

## 📋 Table of Contents

- [Why This Integration?](#why-this-integration)
- [Features](#features)
- [Current Status](#current-status)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Configuration](#configuration)
- [Available Entities](#available-entities)
- [Usage Examples](#usage-examples)
- [Troubleshooting](#troubleshooting)
- [Roadmap](#roadmap)
- [Contributing](#contributing)
- [Credits](#credits)
- [License](#license)

## Why This Integration?

When you add a Sungrow iHomeManager to your system, critical grid import/export data becomes unavailable through the inverter's Modbus interface. This integration solves that problem by communicating directly with the iHomeManager via Modbus, unlocking:

- **Grid metrics** - Real-time import/export data
- **EV charger control** - Full access to EV charger entities and settings
- **EMS controls** - Battery charge/discharge modes

## ✨ Features

- ✅ Access to all documented iHomeManager Modbus registers
- ✅ Grid import/export monitoring
- ✅ EV charger status and control
- ✅ Write capability for holding registers:
  - EMS mode selection
  - Battery forced charge/discharge mode and rate
  - EV charger mode control
- ✅ Compatible with Sungrow AC chargers (tested with AC22E-01)

## 🚧 Current Status

**BETA** - This integration is in active development and testing.

### What's Working
- ✅ All entities for registers documented in the iHM Communication Protocol
- ✅ Read and write operations for Modbus registers
- ✅ EV charger integration (AC22E-01 tested)

### Known Limitations
- ⚠️ Some iSolarCloud functions lack Modbus documentation (e.g., Self Consumption thresholds for power purchase and feed-in)
- ⚠️ No pre-built dashboard template (yet)
- ⚠️ Scenes/automations not included

## 📦 Prerequisites

- **Home Assistant**
- **Sungrow iHomeManager** on your local network
- **iSolarCloud installer account** (for enabling Modbus TCP)
- Existing Sungrow inverter Modbus integration (recommended: [mkaiser/Sungrow-SHx-Inverter-Modbus-Home-Assistant](https://github.com/mkaiser/Sungrow-SHx-Inverter-Modbus-Home-Assistant))


### Compatible Hardware
- Sungrow iHomeManager
- Sungrow AC EV Chargers (tested: AC22E-01)

## 🔧 Installation

### Step 1: Enable Modbus TCP on iHomeManager

1. Log into iSolarCloud with **installer-level credentials**
   - [Guide: Get installer account access](https://github.com/mkaiser/Sungrow-SHx-Inverter-Modbus-Home-Assistant/wiki/FAQ:-iSolarCloud-installer-account)

2. Navigate to: **Device → iHomeManager → Settings → Common Settings → System parameters**

3. Enable **Modbus TCP 503 port**
   - Port 502 is often occupied by the EV charger
   - Modbus TCP allows only one connection per port
   - Using port 503 avoids conflicts
   - ensure SSL is not enabled for port 503
  <img width="2093" height="1114" alt="image" src="https://github.com/user-attachments/assets/a4fe8ceb-ea8a-48e6-998f-e729553eb74c" />

### Step 2: Install the Integration Files

1. Download the YAML configuration file from this repository

2. Copy it to your Home Assistant configuration directory:
   ```
   /config/integrations/sungrow_ihomemanager.yaml
   ```

3. Add the following to your `configuration.yaml`:
   ```yaml
   # Include "integrations" folder by adding the following lines to your "configuration.yaml":
   homeassistant:
     packages: !include_dir_named integrations
   ```

### Step 3: Update Configuration

Edit `secrets.yaml` and update with contents of secrets.yaml in this repo

### Step 4: Restart Home Assistant

Restart Home Assistant to load the new configuration. Check for any errors in the logs.


### Finding Your iHomeManager IP Address

1. Check your router's DHCP client list
3. Consider setting a static IP or DHCP reservation for stability

## 📊 Available Entities

### Grid Monitoring
- Grid Import Power
- Grid Export Power
- Grid Frequency
- Grid Voltage (L1, L2, L3)
- Total Grid Import Energy
- Total Grid Export Energy

### EV Charger (if installed)
- Charger Status
- Charging Mode
- Charging Current
- Charging Power
- Session Energy
- Charger Enable/Disable

### Battery & EMS
- EMS Mode (Self Consumption, Time of Use, etc.)
- Battery Forced Charge/Discharge Mode
- Battery Charge/Discharge Rate
- Battery SOC

*Full entity list available in the YAML configuration file*


## 🔍 Troubleshooting

### No Entities Appear in Home Assistant

1. Check Home Assistant logs for Modbus errors
2. Verify iHomeManager IP address and port
3. Ensure Modbus TCP port 503 is enabled in iSolarCloud and SSL is disabled
4. Test connectivity: `telnet YOUR_IHM_IP 503`
5. Verify you're using the correct slave ID (usually 247)

### Connection Refused or Timeout

- Port 502 occupied**: Try port 503 instead
- Ensure Modbus TCP port 503 is enabled in iSolarCloud and SSL is disabled
- Multiple connections**: Modbus TCP allows only one connection per port. Close other Modbus clients.

## 🗺️ Roadmap

- [ ] Create pre-built dashboard template
- [ ] Add example automations and scenes for common use cases

## 🤝 Contributing

Contributions are welcome! If you have:
- Tested this with additional hardware
- Found bugs or issues
- Improvements to documentation
- New features or automations

Please open an issue or submit a pull request.

## 📚 Credits

- Based on the structure from [mkaiser/Sungrow-SHx-Inverter-Modbus-Home-Assistant](https://github.com/mkaiser/Sungrow-SHx-Inverter-Modbus-Home-Assistant)
- Register documentation from: `iHM.Communication.Protocol-20260121-test.pdf`
- Community testing and feedback

## Support

- **Issues**: [GitHub Issues](https://github.com/Jam3s97/sungrow_ihomemanager/issues)
- **Discussions**: [GitHub Discussions](https://github.com/Jam3s97/sungrow_ihomemanager/discussions)

## Disclaimer

This integration is not affiliated with or endorsed by Sungrow. Use at your own risk. Always ensure you understand the implications of changing settings on your energy system.

---

⭐ If this integration helps you, consider giving it a star on GitHub!
