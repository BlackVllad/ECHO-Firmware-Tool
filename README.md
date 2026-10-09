# ECHO Series Firmware Upgrade Guide

> **Acknowledgments & Important Notice:**  
> The tool and initial instructions in this repository were provided directly by **FiiO Support**.  
>  
> ⚠️ **Note:** This specific method and tool configuration is primarily effective for devices stuck in **MaskRom Mode**. If your device is currently in **Loader Mode** and you are trying to unbrick it, this process might not work. For Loader Mode unbricking instructions, please refer to this guide: [HOW TO UNBRICK A ECHO MINI : r/snowsky](https://www.reddit.com/r/snowsky/comments/1rql5fy/how_to_unbrick_a_echo_mini/)

## 1. Introduction
This repository contains the RKDevelopTool and drivers required to flash firmware updates to the Snowsky ECHO series of devices.

### Firmware Files Reference
> **Important Note:** It is highly recommended to rename the firmware `.img` file to something simple (e.g., `firmware.img`) before flashing. Computers with English locales often fail to detect or read files properly if their names contain Chinese characters.

Make sure you use the correct firmware `.img` file for your specific device model:
*   **ECHO:** `HT9099(ECHO)BT53_HW_V1.7_SW_V1.2.0_HIFIDAC43198_6KEY_20260204_1130`
*   **Echo Mini (8GB version):** `HT9093BT53_五套UI_HW_V1.3_SW_V3.2.0_HIFIDAC43131_LCD读ID识别_6KEY_20260211_1043`
*   **Echo Mini (512MB version):** `NANO_F512M_HW_V1.0_SW_V1.5.0_HIFIDAC43131_3KEY_20260714_1725`
*   **Echo Nano:** `NANO_F512M_HW_V1.0_SW_V1.4.0_HIFIDAC43131_3KEY_20260623_1024`

## 2. Install the Driver
Before using the tool, you must install the Rockusb driver on your computer:
1. Connect the device to your PC.
2. Right-click **"This PC"** (or "My Computer") → select **"Properties"** → select **"Device Manager"**.
3. Expand **"Other devices"** and find the unknown device with a yellow exclamation mark.
4. Right-click it and click **"Update driver"**.
5. Follow the prompts, select manual installation location, and choose the `Driver` folder inside the tool directory (`Rockusb` folder). 
6. Select the corresponding driver based on your system parameters (x86/x64, Win7/Win10).
*Note: If the Win10 driver fails, you can try installing the Win8 driver.*

## 3. Flash the Firmware
1. Open the **`RKDevelopTool.exe`** program. *(Note: The tool has already been configured to display in English by setting `Selected=2` in the `config.ini` file).*
2. Click **"Load firmware"** (button 1) and select the correct `.img` file for your device from the list above. The tool will say `Loading firmware...` and then `Loading firmware Finished.`.
3. Pay attention to the lower-left corner of the program. It should display **"Found one MSC device"**.
4. Click the **"Switch"** button (button 2).
   * If the driver is installed successfully, the lower-left corner will change to **"Found one MASKROM device"** or **"Found one Loader device"** (either is fine).
   * *Troubleshooting:* If it displays "No devices found", the driver installation failed. The device will power off and cannot connect. Reinstall the driver, then restart the device by long-pressing the Reset button and powering it back on.
5. Click **"Erase system block"** (button 3) to wipe the old firmware.
6. Click **"Upgrade"** (button 5) to flash the new firmware.
7. The data in the lower-right corner will show the progress. Once complete, it will display: `Download Firmware Success`.

## 4. Error Message Description
*   **"Failed to load configuration information..."** — Error loading `config.ini`. Usually caused by special or Chinese characters in the folder path. (This repo fixes that issue).
*   **"Failed to load firmware..."** — The firmware was not selected or the file is unreadable.
*   **"Another operation is in progress, please wait!"** — Wait for the current task to finish.
*   **"Operation mismatch..."** — Ensure the chip supported by the firmware matches the selected tab.
*   **"No device found..."** — Verify the device is connected and in Rockusb state.
*   **"Multiple devices found..."** — Only keep one device connected to the PC.
*   **"Failed to obtain device information..."** — Unplug and reconnect the device.
*   **"Unsupported device type..."** — The device must be in Rockusb state, not USB mass storage (MSC) mode. Click "Switch" first.

## 5. Important Notes
*   If the process gets stuck at *"Download Boot Start"*, please disconnect the device and restart the upgrade process.
*   On Windows Vista or Windows 7 systems, the program must be run with administrator privileges.
