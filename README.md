# 3D printer-plan

This repo contains our plan on how to build our own RepRaps. We are currently leaning towars building Prusa i3:s.

## Good Candidates:

http://reprap.org/wiki/Prusa_i3

## Hot End

Comparison charts:
* http://reprap.org/wiki/Hot_End_Comparison

Interesting discussion about clones here:
* http://airtripper.com/1236/j-head-mk-iv-hot-end-clone-design-quick-review/
* http://jheadnozzle.blogspot.se/2013/11/is-j-head-real.html


### Thermistor:
### ThermoCouple:

## Bowden extruder:
+ Faster and lighter.
+ less shaking
+ Faster printing
- Hysteresis. The plastic filament will compress in any extruder, but
putting pressure on such a long length of filament will multiply the
effects of this compression, leading to springiness. The flexibility of
the PFTE tube exacerbates this problem.  It is potentially possible to
control this problem, perhaps with an encoder just above the hot end.
Software might also be able to reduce this problem, but would require
(maybe lengthy) calibration.

Note: The Bowden extruder is not helpful if you have a fixed printing head
(or moving in Z-only) and a XY-moving platform.

A stepper-based extruder is required if no encoder is used. 


## Extruders:

* Pictures etc of different extruders:
http://reprap.org/wiki/RepRap_Options#Extruder

* EMO25 extruder, which can extrude such neat materials as play-doh, clay, and self-setting rubber

* E3D-v6 (e3d-online.com)
  Review: http://www.tridimake.com/2014/08/e3d-v6-hot-end.html

  Popular models:
  * Wade's geared extruder
  * Greg's hinged extruder
  * Greg's Wade's Reloaded extruder
  Seems to be printable with some additional hardware like
  bearings and nuts. I'm gearing towards simply using a metal 
  gear on a stepper motor (that's how it's done on the Zortrax M200)
  Have to research more why this could be a bad idea.
  Seems like the gearing is there to produce more torque? but since
  ABS has less friction than PLA, maybe a single gear will suffice
  for the cold end of the extruder.
  Plenty of parts are available online for making a DIY cold end.

### Notes:
  * Might be wise to glue the thermistor in place with Silicoset 158.

## Stepper motors

  The Prusa requires 5 NEMA 17 stepper motors.

  The 3DR delta requires 4 NEMA 17 (or NEMA 14) stepper motors. max 50mm in
  length

## Stepper motor drivers

### DRV8825
  High Current 32x Microstepping Driver with Heatsink	DRV8825 High Current 32x
  Microstepping Driver

### A4988 Stepper Driver 
  Cheaper than drv...
  Less step resolution?

## Misc links

  * Nice list of printers: https://sites.google.com/site/3dprinterlist

  * Prepare for a build: http://reprap.org/wiki/Planning_and_preparing_for_a_build

  * http://www.sweclockers.com/forum/5-modifikationer-och-egna-konstruktioner/1267878-projekt-diy-3d-printer-reprap-prusa-i3/

  * Richard rates the 3rd generation Solidoodle as the best bang for your buck
  http://www.tomsguide.com/us/best-3d-printers,news-17552.html

  * Supersmart spool holder:
  http://elektronikforumet.com/forum/viewtopic.php?f=3&t=67748&start=1890

##Controller boards

### Smoothie board (ARM based)
https://www.kickstarter.com/projects/logxen/smoothieboard-the-future-of-cnc-motion-control/posts/619044?ref=activity
Seems to be going good!

### RUMBA Basic Board:
used in 3DR Delta, available from
* http://www.reprapdiscount.com/electronics/33-rumba-basic-board.html#
* Dealextreme
* Alibaba 

* Benefits of RUMBA vs RAMPS
1) You have 6 power output instead of 3 of RAMPS;
2) You can power the whole system from 24V power supply;
3) You have the option of power outputs from pins or screws;
4) Onboard 5V and 12V regulators if you prefer using a 12V+ power supply;
5) Smaller and easier to handle;
6) Addicional 12V and 5V outputs;

#### Specs
1 Use the same CPU as that of Arduino MEGA as main control chip, Atmega2560
cooperates with high-performance USB chip in order that it is compatible with
all RAMPS relevant firmware;

2 Five interfaces as input for temperature sensor.

3 All pins being drawn out to permit more function expansion.

4 With expanding interface, it can connect the LCD displayed and the
development board.

5 Servo’s expanding interface to make the automatic leveling easier to add

6 Supporting 6 pieces of 16 micro stepping drivers of A4988.

7 PWM DC output( heating pipe ,fan), six channels of output( 1 channel of high
    current, 3 channels of medium current and 2 channels of low current). Use low
on-resistance MOS Varactor as driver and LED tests each output.

8 Power-supply: power input 12v-35v, dual power to avoid interaction; hot bed
connects 11A, 12V, other sections connect 5A, 12V and add a 12V cooler to
reduce the high temperature from the high current of Mega controller.

9 Adopts popular control board firmware-Marlin, which has good stability,
  usability and function.

  Size: 135 x 175mm

  Weight: 90g

  Software Resources Compiling environment: Arduino IDE

  Firmware: Marlin

  HostComputer Software:printrun Repetier-Host 

##Controller firmwares
### Sprinter:
  https://github.com/kliment/Sprinter
RAMPS (ie, AtMega one MCU controllers)

  Arduino (with some special tricks?)
uses: arduino-0023 (old version)

### Repetier:

### Marlin:
  * GitHub: https://github.com/jcrocholl/Marlin 
  * Arduino
  * Initial investigation indicates good firmware for delta printers.
  * All the implementation is done in *.cpp files to get better compatibility
  with avr-gcc without the Arduino IDE.

##Path Generators
### Slicer
### Kiss (slicer?)

## Mechanical stuff

### Steel rods
  diameter 6mm and 8mm are commonly used for many 3d printer designs
  the linear bearings commonly available will fit these two sizes.
  3DR uses 6mm by default, 
  Prusa 8mm.

### Aluminium extrusions:
  Joining methods:
  http://www.aluminiumdesign.net/design-support/joining-aluminium/
https://www.google.se/search?q=aluminium+extrusion+T-Nut&espv=2&biw=983&bih=513&tbm=isch&imgil=odRI_dLCxQL_6M%253A%253B_4aUsEvjYbFAZM%253Bhttps%25253A%25252F%25252F3dbotic.com%25252Fhardware-resources-for-diy-3d-printer-kit%25252F&source=iu&pf=m&fir=odRI_dLCxQL_6M%253A%252C_4aUsEvjYbFAZM%252C_&usg=__xzq_UDiT9GOiRTsyjRcPOg8sKxE%3D&ved=0CD8Qyjc&ei=PTOHVPPcF-j-ywODxIKQCg#facrc=_&imgdii=odRI_dLCxQL_6M%3A%3Bp5D5s2t3XuRqsM%3BodRI_dLCxQL_6M%3A&imgrc=odRI_dLCxQL_6M%253A%3B_4aUsEvjYbFAZM%3Bhttp%253A%252F%252F123dprinter.com%252Fwp-content%252Fuploads%252F2012%252F11%252FBoschRexroth_T-Nut_1.jpg%3Bhttps%253A%252F%252F3dbotic.com%252Fhardware-resources-for-diy-3d-printer-kit%252F%3B316%3B385

## Heating beads

### DIY:
* Borasilicate glass (what is it used for?)
  * TODO: research Kapton tape in relation to hot beads

## Terms and abbrevations
### oozing:
  Reversing the extruder motor very quickly allows you to have less oozing.
  Would this not withdraw the filement from the hot end?

### honeycomb infill:

### Perimeters:
  The outer sections on a part?

## Printing filament types

### Color shifting nylon

### Flexible plastics

### PLA
  Made of bio degradable plastic. 
  Lower extrusion temperature than ABS.
  TODO: how does acetone react with PLA?

### ABS:
  Glassing temp = 105C
  Extruder target temp = 200-240C for smooth extrusion


## Printer types
### Deltas:
  Seems very interesting. Simpler frame construction, seem to have very good
  resolution if done right and a lot cooler than just having an ordinary 3D
  printer.

  Different delta designs:
  3DR Delta
  https://www.youtube.com/watch?v=11PVy4AUbeQ
http://richrap.github.io/3DR-Delta-Printer/
http://richrap.com/
Assembly instructions (from creators blog)
  http://richrap.blogspot.se/2013/07/3dr-reprap-delta-printer-part-1-release.html

  Tips on building a delta:
  http://minow.blogspot.se/

### Polar bots
  Build area rotates, check em out further.
  http://forums.reprap.org/read.php?185,220993

## Resellers
  * Aliexpress
  * weedo3dprinting (UK ebay), have metal rods up to 80cm at good price. 
  * http://www.robotdigg.com/  (US)
  * e3d-online.com (UK, a bit expensive, got nice extruders, and misc build
      parts)

