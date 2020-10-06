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

```
#define Z_MIN_PROBE_USES_Z_MIN_ENDSTOP_PIN // Enable BLTouch probe pins (white and black wires) to be connected to Z-\
or\
Change:   //#define Z_MIN_PROBE_PIN 32 // Pin 32 is the RAMPS default\
To:       #define Z_MIN_PROBE_PIN 17   // Creality V4.2.7 BLTouch OUT (written on the board)
```

Pinout on board (5 pins named as BL_T) and respective connections 
*   Board-----BLTouch wires
*   G---------Green----Servo
*   V---------Red------Servo
*   IN--------Yellow---Servo
*   G---------White----Probe (if it doesn't work, try to swap with Black)
*   OUT-------Black----Probe (if you are using Z_MIN_PROBE_PIN 17, if you don't, please just uncomment Z_MIN_PROBE_USES_Z_MIN_ENDSTOP_PIN as above)

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
In my case: C:\creality-v4.2.7-marlin-2.0.6-bugfix\Marlin-bugfix-2.0.x\.pio\build\STM32F103RET6_creality\
In your case: somedir\.pio\build\STM32F103RET6_creality

Download compiled: https://github.com/Flawioo/Creality-Ender-3-board-v4.2.7/blob/master/firmware-20200825-161146-BLT-and_Runnout-filament.bin

# Paypal if you feel I helped you in a fair way
My ID flawioo@hotmail.com
