# TVturntable - no need to get up to turn the TV!

Are you tired of having to get up and ajust the viewing angle of your TV?
You might want to build the TVturntable which will allow you to rotate your TV (or an ything else, really)
from your phone.

![TVturntable in action](./documentation/20211113_115309.gif)


## BOM
* 3D printed turntable
* motor spacer (3d printed)
* GT2 pully (can be 3d printed)
* 3/16" (4.76 mm) bearing steel balls  
* ESP8266 or any other microcontroller
* stepper driver
* stepper motor
* closed loop GT2 timing belt, 200 mm, 7 mm wide
* M3 bolt and hex nut


## 3D printed parts
* TVturntable_large_V3-bottomV3_motormount.stl
* TVturntable_large_V3-bottomV3_003.stl
* TVturntable_large_V3-motor spacer.stl
* TVturntable_large_V3-middle.stl
* TVturntable_large_V3-top.stl
* GT2_pulley.stl


### Printing instructions
I've printed all parts in PLA with 20% infill, no supports, no rafts.

### Assembly
![Assembly of 3D printed parts](./documentation/assembly.gif)
## Electronics
In addition to the printed parts you will need a microcntroller, a stepper driver and a stepper motor.
You can use any combination which is available to you or with which you have experience.

My setup consists of a Wemos D1 mini (ESP8266 based controller),  flashed with TASMOTA.
Convieniently, [TASMOTA](https://tasmota.github.io/docs/Commands/#stepper-motors) includes a driver for A4988 based stepper drivers. You can use any stepper driver which need the same input.
I use an EasyDriver stepper driver based on (A3967). It requires three inputs: enable, direction and step.

Then I use the standard TASMOTA commands over MQTT to turn the motor:
```bash
MotorRotate 360
```
will turn the motor clockwise
```bash
MotorRotate -360
```
will turn the motor counterclockwise for a full rotation.

Depending on the stepper motor, microstepping and gear ratio between pully and the TVTurntable, you will have to adjust the parameters to achieve the desired angle of rotation.
