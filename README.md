# Claw-Machine-PCB
PCB for the UofC GNCTR 2024 claw machine

![PCB Render 1](pcb_render_1.png)

## Main Components
1. 3x Stepper Motor Drivers
    * 2x will drive Y-axis, and 1x will drive X-axis
    * Model: A4988 Breakout
        * [Guide 1 - lastminuteengineers.com](https://lastminuteengineers.com/a4988-stepper-motor-driver-arduino-tutorial/)
    * The [microstep mode](https://lastminuteengineers.com/a4988-stepper-motor-driver-arduino-tutorial/#:~:text=power%20supply%20pins.-,Microstep%20Selection%20Pins,-The%20A4988%20driver) is locked in 1/16th Step Mode.
    * Add LEDs to each control signal
    * Signals (MCU to Driver, for each driver): STEP, DIR, EN

2. 1x DC Motor Driver
    * 1x for the claw to drop
    * Model: L298N (package: multiwatt vertical)
        * [Datasheet 1](https://www.sparkfun.com/datasheets/Robotics/L298_H_Bridge.pdf)
    * L298N contains 2x H-Bridges, so it can drive the 2x motors
    * Add LEDs to each control signal

3. Countdown Clock I2C Connector
    * Uses I2C (so only one bus)
    * Connection over 2.54mm headers

4. 10x Buttons and Limit Switches
    * 3x Limit Switches, 3x User Buttons, 2x Spare
    * Use 5.08mm screw terminal in parallel with 2.54mm header
    * Make them active-low, with external pull-up resistors
    * Put them in parallel with 6mm through-hole push buttons for validation

5. Control Stick
    * Model: [4-Way Switched Discrete Joystick](https://www.amazon.ca/Joystick-Classic-Competition-Arcade1up-Replacement/dp/B0BWWW8Z2J/ref=sr_1_15)
    * Basically 4x more buttons
    * Label them NESW, and use a common GND (5-pin 2.54mm header, but two of them side-by-side)

6. 1x Microcontroller System
    * Model: Arduino Mega 2560 clone
    * Footprint available via plugin

7. 4x General Power Output Channels
    * Use AO3420 MOSFETs, to be able to drive LEDs in the frame, etc.
    * Add a 3-way solder jumper to select between 5V or 12V power
    * Can be used fo LED strip lighting. One channel will be for the 12V claw solenoid.

8. Voltage Input Rails
    * 5V and 12V rails
    * Inputs via 5.08mm screw terminals
    * Powered from computer PSU
