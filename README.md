# Automotive Non Adaptive Cruise Control retrofit for cars
Specifically designed for a Nissan Micra K12 but can be adapted to other cars with existing PCB and firmware changes. 
**DEVICE UNDER DEVELOPMENT. DO NOT USE IT IN A CAR.**

## Description
The goal of this project is to design an aftermarket KIT that is able to hold the specified speed of a car. 

## How it works
**Inputs**

 - Abs speed sensor signal for measuring speed
 - Brake light signal to detect when brake pedal is pressed
 - Actual accelerator pedal signal 
- Various Buttons for controlling the Cruise Control 

**Outputs**
- The accelerator pedal signal that is routed to the car ECU
- Various indicator lights

How it works:

 -  If the Cruise Control is OFF, the actual accelerator pedal signal is routed to the ECU without the intervention of the KIT. 
 - If the Cruise Control is ON, the Arduino reads the speed of the vehicle through the Speed Sensors and generates the correct pedal signal so that the vehicle maintains set speed. The generated (fake) pedal signal is then routed to the ECU.
 - A MUX is used that outputs either the real accelerator pedal signal (when Cruise Control is disabled) or the (fake) signal of the Arduino (if Cruise Control is enabled).  
 - Two relays connected in series act as a MUX while also providing redundancy. In case one relay is stuck the real accelerator pedal will always be routed to the output.
 - The brake pedal deactivates the Cruise Control and immediately (via hardware logic) changes the Select signal of the MUX so that the output changes to the real accelerator pedal. The system will always switch the output to the real accelerator pedal even if the Arduino is frozen. 

## Status
I am currently testing the board, the functionality works as expected with the prototypes. Never use it in car since it is not 100% tested and I can not guarantee that it works flawlessly. Severe injury can be made. More testing has to be done. Software will be the next step.

## License 
Copyright 2021 Lolis Ilias

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE. 
 


 
