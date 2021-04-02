# Creality-Ender-3-board-v4.2.7
Marlin 2.0.7 compiling proccess to Creality v4.2.7 board

Steps to help anybody that needs to get this board working ok

Download Marlin from git hub https://github.com/MarlinFirmware/Marlin/archive/2.0.x.zip

Download Configuration exemples: https://github.com/MarlinFirmware/Configurations/archive/release-2.0.7.zip

## In platformio.ini (for any firmware version you'll compile)

`default_envs = STM32F103RET6_creality`

## In Configuration.h

###### Simplest firmware
```
#define MOTHERBOARD BOARD_CREALITY_V427

#define CUSTOM_MACHINE_NAME "Ender-3 32bits" // Or any name you'd like to
```

###### BLTouch enabling

If you want to use 5 pins of BL_T connector\
Let the following line commented

`//#define Z_MIN_PROBE_USES_Z_MIN_ENDSTOP_PIN`

**OR**

If you want to connect BLTouch probe pins (white and black wires) to be connected to Z-\

`#define Z_MIN_PROBE_USES_Z_MIN_ENDSTOP_PIN`


Pinout on board (5 pins named as BL_T) and respective connections
*   Board-----BLTouch wires
*   G---------Green----Servo
*   V---------Red------Servo
*   IN--------Yellow---Servo
*   G---------White----Probe (if it doesn't work, try to swap with Black)
*   OUT-------Black----Probe (enabled if the parameter is equal `//#define Z_MIN_PROBE_USES_Z_MIN_ENDSTOP_PIN` as above)

```
#define BLTOUCH

#define NOZZLE_TO_PROBE_OFFSET { -40, -10, 0 } // Using this thingfile as mount, measure correctly using your mounted BLTouch https://www.thingiverse.com/thing:3003725

#define PROBING_MARGIN 15 // If you'd want stay away from the edges (higher values goes to center of the bed)

//#define MIN_SOFTWARE_ENDSTOP_Z // To allow to set Z offset values in negative

#define AUTO_BED_LEVELING_BILINEAR

#define LCD_BED_LEVELING

#define Z_SAFE_HOMING
```
###### Runout Filament Enabling

```
#define FILAMENT_RUNOUT_SENSOR

#define NOZZLE_PARK_FEATURE // To change filament

#define NOZZLE_PARK_POINT { (X_MAX_POS - 10), (Y_MIN_POS + 10), 20 } // To change the position of the hotend in front on the right of the bed
```
## In Configuration_adv.h
```
#define BLTOUCH_DELAY 500

#define ADVANCED_PAUSE_FEATURE

#define PARK_HEAD_ON_PAUSE    // Park the nozzle during pause and filament change.
```
## Compile

In Auto Build Marlin at Visual Studio, click on Build botton and wait for the green line\\
1 succeeded in 00:00:26.355

# Where is the firmware I've compilled
In my case: C:\Marlin-2.0.7\Marlin-2.0.x\.pio\build\STM32F103RET6_creality\
In your case: somedir\.pio\build\STM32F103RET6_creality

# Easiest Download compiled my friend:

**Simplest**

https://github.com/Flawioo/Creality-Ender-3-board-v4.2.7/raw/Marlin-2.0.7/firmware-20201005-165416-Simplest.bin

**BLTouch on -Z**

https://github.com/Flawioo/Creality-Ender-3-board-v4.2.7/raw/Marlin-2.0.7/firmware-20201005-173413-BLTouch_using_probe_connected_to_-Z%20pins.bin

**BLTouch on BL_T (5 pins)**

https://github.com/Flawioo/Creality-Ender-3-board-v4.2.7/raw/Marlin-2.0.7/firmware-20201005-174810-BLTouch_using_5pins_of_BL_T_connector.bin

**Most Complete**

https://github.com/Flawioo/Creality-Ender-3-board-v4.2.7/raw/Marlin-2.0.7/firmware-20201005-180711-Simplest%2BBLTouch%2BRunout%2BFilChange.bin

# Paypal if you feel I helped you in a fair way
My ID flawioo@hotmail.com
