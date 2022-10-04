# Klipper Config File for Elegoo Neptune 3 (WIP)

Base printer config file for **Klipper** (based on the original code from [jerryngm](https://github.com/jerryngm/Neptune-Elegoo3-Klipper)). **Use at your own risk!!** Please read the comments in the file, you will need to calibrate multiple things specially the heater PID for the hotend and bed.  

## 📄 **Done:**  
 ✔️ X Y Z E Steppers and Endstops  
 ✔️ Heaters and Fans  
 ✔️ Filament sensor  
 ✔️ Klipper's Pressure Advance  
 ✔️ Klipper's Input Sharper

## **👨‍🏫 Building Klipper Firmware**  
 
 The **Elegoo Neptune 3** printer uses a proprietary board called **ZNP Robin Nano_DW V2.1**, but, according to the official Marlin [source code](https://github.com/NARUTOfzr/Neptune_3) from Elegoo this board is based on the **STM32F401** chipset and has the exact same pinout of the [MKS Robin E3 V2](https://github.com/NARUTOfzr/Neptune_3/blob/main/ZNP_F401_Marlin-V_1.0.3/Marlin/src/pins/stm32f4/pins_MKS_E3_V2.h) board.

 So, just use the following config in **make menuconfig**:
 - Micro-controller Architecture (**STMicroelectronics STM32**)
 - Processor model (**STM32F401**)
 - Bootloader offset (**32KiB bootloader**)
 - Communication interface (**Serial (on USART1 PA10/PA9)**)
 
![Klipper firmware configuration](https://github.com/jerryngm/Neptune-Elegoo3-Klipper/raw/main/Klipper-Build-Settings.jpg)  

 Once compiled, copy **klipper.bin** to an SD card (root folder) then rename it to **ZNP_ROBIN_NANO.bin**, insert it to your Neptune then switch on. You can remove the stock screen, it will become useless since it doesn't work with Klipper.
 
 **You can revert back to original firmware by placing the original firmware bin file to the SD card.**
 
 ## **🔧 Installation**  

 1) First, compile and install the Klipper firmware according to the configuration [above](https://github.com/bsas/Neptune-Elegoo3-Klipper#-building-klipper-firmware) and then connect the printer to a Klipper machine via USB. You can completely remove the screen since it is useless with Klipper.
 
 2) My configuration file uses the stock Z endstop sensor (not the probe). I notice that using the probe forced the printer to bump the nozzle with an uncomfortable force into the bed. The original configuration mitigate that changing the **homing_speed** and **second_homing_speed** to very low numbers but that made the printer homing and bed mesh calibration unbearably slow. The stock Elegoo sensor is very high, so, you need to calibrate the **Z-Offset**. Home the printer, calibrate the new Z-Offset using the UI and a paper (similar to manual bed leveling) and then save it as a **position_endstop**.
 
 3) Calibrate the probe offset (**PROBE_CALIBRATE**), following the instructions here: https://www.klipper3d.org/Bed_Level.html
 
 4) Do a **PID** calibration for the extruder heater and the bed, following the instructions here: https://www.klipper3d.org/Config_checks.html#calibrate-pid-settings
 
 5) Calibrate the extruder **rotation_distance** (E-Steps): https://www.klipper3d.org/Rotation_Distance.html#calibrating-rotation_distance-on-extruders
 
 6) Run a **heightmap** calibration. If something goes wrong, maybe you need to align your X gantry. Worse case, you can increase the **horizontal_move_z** under **bed_mesh** if the probe keeps bumping on the bed during calibration. 

 ## **🔧 Advanced tuning** 
 
 For **Input Shaper** you can use an **ADXL345** accelerometer. It is quite simple to attach it to the bed or the hotend and run the resonance tuning. For more details read the [official documentation](https://www.klipper3d.org/Resonance_Compensation.html). I will soon upload the pictures of how I attached my accelerometer.
 
 For **Pressure Advance** just follow the [official documentation](https://www.klipper3d.org/Pressure_Advance.html) and use the configuration for **long bowden extruders**.
