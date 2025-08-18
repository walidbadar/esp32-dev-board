# 🧠 ESP32-Dev Board Support for Zephyr RTOS

This repository contains the board support files for the **ESP32-Dev**, a custom ESP32-based development board designed to work with the **Zephyr RTOS**. It includes a Device Tree source file that defines peripheral mappings, memory regions, and GPIO configurations specific to this board.


<p align="center">
  <img src="https://drive.usercontent.google.com/uc?id=1pIPVY6q-XbUXOz9KB1vCSkcN2TUEpoSZ&export=download" alt="ESP32-Dev Board" width="500"/>
</p>

---

## 📌 Board Features

| Feature       | Description                                 |
|---------------|---------------------------------------------|
| **SoC**       | ESP32-D0WD-V3 (Xtensa dual-core)            |
| **UART0**     | Console output (115200 baud)                |
| **UART1**     | Available (115200 baud)                     |
| **UART2**     | Used for Modbus with DE pin on GPIO5        |
| **I²C0**      | SDA: GPIO21, SCL: GPIO22 (Open-drain)       |
| **Buttons**   | Button 0: GPIO1_1, Button 1: GPIO0_25       |
| **Wi-Fi**     | Enabled                                     |
| **Bluetooth** | HCI interface enabled                       |
| **Flash**     | 4MB external SPI flash                      |
| **SRAM**      | Configured and mapped                       |

---

## Setup Instructions

### 1. Set up Zephyr workspace

If you haven't already set up your Zephyr workspace:

```bash
west init zephyr-workspace
cd zephyr-workspace
west update
west zephyr-export
```

### 2. Add the board files

Place all files from this repository inside the following directory:

```bash
zephyr-workspace/boards/espressif/esp32_dev/
```

Your folder structure should look like:

```
zephyr-workspace/
└── boards/
    └── espressif/
        └── esp32_dev/
            ├── board.cmake
            ├── board.yml
            ├── esp32_dev-pinctrl.dtsi
            ├── esp32_dev_appcpu.dts
            ├── esp32_dev_appcpu.yaml
            ├── esp32_dev_appcpu_defconfig
            ├── esp32_dev_procpu.dts
            ├── esp32_dev_procpu.yaml
            ├── esp32_dev_procpu_defconfig
            ├── Kconfig
            ├── Kconfig.esp32_dev
            └── Kconfig.sysbuild
```

### 3. Build a sample application

```bash
west build -b esp32_dev/esp32/procpu samples/hello_world
```

### 4. Flash the firmware

```bash
west flash
```

### 5. Monitor serial output
```bash
west espressif monitor
```
