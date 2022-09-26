# Klipper Config File for Elegoo Neptune 3 (WIP)
Base Klipper Config file for Klipper. **Use at your own risk!!** Please read the comments in the file, you will need to calibrate your hotend heater PID and E-steps   
## 📄 **Todo:**  
 ✔️ X Y Z E Steppers config  
 ✔️ Heaters and Fans  
 ⭕ (WIP) ABL using Z- (ZNP Glevel board - Strain Gauge Sensor) - 8bit AVR (STM8S003F3P6) + HX711 (Load cell amplifier), this board send out z-end digital signal at predetermined weight, triggered by probe contact  
 ⭕ (WIP) Filament sensor  
 ⭕ (WIP) Klipper's Pressure Adance calibrate  
 ⭕ (WIP) Klipper's Input Sharper  

## **👨‍🏫 Building Klipper Firmware**  
 **I have pre-complied the firmware, you can download "ZNP_ROBIN_NANO_Klipper.bin" then remove _Klipper from the name and copy this file to your SD Card**  
 If you would like to compile your own, please follow the instructions below:  
 Use the following config in make menuconfig    
![enter image description here](https://github.com/jerryngm/Neptune-Elegoo3-Klipper/raw/main/Klipper-Build-Settings.jpg)  

Once compiled, copy klipper.bin to an SD card (root folder) then rename it to ZNP_ROBIN_NANO.bin, insert it to your Neptune then switch on.  
You can revert back to original firmware by placing the original firmware bin file to the SD card  

**I have also pre-complied the firmware, you can download "ZNP_ROBIN_NANO_Klipper.bin" then remove _Klipper from the name and copy this file to your SD Card**
 
 ## **🔧 Calibrations**  
 You will need to run your own PID calibration for the extruder heater, following the instructions here: https://www.klipper3d.org/Config_checks.html#calibrate-pid-settings or enter PID_CALIBRATE HEATER=extruder TARGET=170 into the console  
 Also extruder rotation_distance (I.e E-Steps): https://www.klipper3d.org/Rotation_Distance.html#calibrating-rotation_distance-on-extruders
 
 ## **🧭 Input Sharper - ADXL345 Mount**
 - [X Axis - Mount to X Carriage](https://github.com/jerryngm/Neptune-Elegoo3-Klipper/blob/main/Neptune3-ADXL345-HOTEND-X-Axis.stl)
 - [Y Axis - Mount to Bed](https://github.com/jerryngm/Neptune-Elegoo3-Klipper/blob/main/Neptune3-ADXL345-BED.stl)
 - -[Clamp to hold board in place for Bed mount, sandwich the board in the middle](https://github.com/jerryngm/Neptune-Elegoo3-Klipper/blob/main/Neptune3-ADXL345-BED-Clamp.stl)
 - [Fusion 360 source file, it's a mess tho but I included it here if you like to make any changes](https://github.com/jerryngm/Neptune-Elegoo3-Klipper/blob/main/Neptune%203%20-%20ADXL345%20-%20Mount%20v1.f3d)
 

