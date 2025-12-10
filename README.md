# MedicalDeviceSecurity_Project_1
This is a project that uses an Arduino Leonardo, a basic LED circuit and a USB-TTL cable to 1) monitor sensor data on the arduino using the serial monitor, and use the cable to observe a second serial monitor 2) use the TTL cable to flash code onto the Arduino by the second serial bus and 3) use a state machine to control the Arduino


## Definitions
### Serial Communication
*   What is Serial Communication?
      * Serial Communication is a means of digital communication where information is sent one bit at a time (in series.) It is a very common and typically quick way of conveying information from a transmitting device to a receiving device.
*   How do devices communicate serially?
    * Devices require four connections: a clock signal that dictates the rate at which information is sent, a common ground or reference voltage, a Tx (transmit) and Rx (receive) lines.  Rx is connected to Tx and Tx is connected to Rx.  Data is sent in packets, typically consisting of a start bit, a byte of information, and a stop bit.  In some instances these packets include a parity bit which is a means of error checking. It describes what the information in the packet is supposed to look like by way of counting an odd or even number of ones and zeros. If the information in the packet doesn't match the parity then the information can be handled appropriately or discarded without causing problems.
*   What is a Serial Communciation Protocol?
      * Serial communication protocols are means by which serial communication is conducted.  Basically it is the rules of communication and  it describes how this communication is done. (fix me)
*   What is a Serial Monitor?
      * Computers and IDEs will sometimes have a serial monitor, which is a tool that reads out information conveyed over serial communication ports, such as a USB port.  The most common form of serial port is a program called PuTTy.
### Baud Rate
*   What is Baud Rate?
      * Baud rate is effectively the rate at which devices can communicate by serial protocol.  It is also known as bits per second (bps) and it effectively describes the frequency of a digital signal.  Most devices operate on 11520 or 9600 baud.
*   How do you calculate baud
      * Baud is calculated by considering the number of bits that can be transmitted in one second, or how often the signal through a serial line can change within a second.
### TTL Cable
*   [This is our cable](https://www.adafruit.com/product/954)
*   This allows a device to use a USB cable to send data over pins
| Pin            | Function | Description      |
| -------------- | -------- | ---------------- |
| V<sub>CC</sub> | +3.3V    | Power supply     |
| GND            | Ground   | Common reference |
| Tx             | Data Out | Transmit data    |
| Rx             | Data In  | Receive data     |
### Arduino Leonardo
*   [Documentation](https://docs.arduino.cc/hardware/leonardo/)
*   Pinout Information
*   Arduino ISP 
## Multiple Serial Port Communication
## State Machine
*   What is a State Machine?
      * A state machine is a machine or devices that has multiple states through which it iterates over either a time frame or by user input
    * think stoplight
*   Pinout
| Leonardo Pin | TTL Cable Pin | Description          |
| ------------ | ------------- | -------------------- |
| 0 (Rx)       | Tx            | Receives serial data |
| 1 (Tx)       | Rx            | Sends serial data    |
| GND          | GND           | Common reference     |
| **Leonardo Pin** |  **LED**    | **Description** |
| Digital 13 | Red | Red State of Machine, with a 1kOhm Resistor|
|Digital 12 | Green | Green State of Machine, with a 1kOhm Resistor|
|Digital 11 | Yellow | Yellow State of Machine, with a 1kOhm Resistor|
*   Rules
      * Our state machine works by iterating through states 0,1 and 2. It changes states every 2 and a half seconds, and can be controlled through the serial monitor.
*   TInkerCad Link: https://www.tinkercad.com/things/iSYwGsP4CDE/editel?returnTo=%2Fdashboard
   <img width="1117" height="587" alt="image" src="https://github.com/user-attachments/assets/ba7da280-fea3-472b-b16a-b7710fcc75d6" />


| Concept              | Key Idea                                                          |
| -------------------- | ----------------------------------------------------------------- |
| Serial Communication | Sends data one bit at a time                                      |
| Baud Rate            | Speed of serial communication (bps)                               |
| TTL Cable            | Converts USB to serial logic levels                               |
| Arduino Leonardo     | Microcontroller with built-in USB and serial capabilities         |
| State Machine        | System that cycles through defined states based on rules or input |

## Implementation

This project uses VSCode as well as the Arduino.IDE to program the Arduino Uno microcontroller, and also a TTL-USB Converter Cable.  The Arduino is flashed with the StateMachine.ino script and the SerialChecker is ran through VSCode.

<insert photo here<

The digital serial port function is used in the .ino script. This allows the microcontroller to send data through the auxillary Tx/Rx pins to the computer. 

The connections are made as described above, indicating which state is active.  In the command line of the digital serial monitor, the user may inpht an integer number from 0-2 to alter the next phase of the state machine, otherwise it will iterate through each state.  Changes in the state machine are visible in the digital serial port.  

This should enable the user to write and read across multiple serial ports. This creates a semblance of a toolchain, wehre data is sent through one port, processed by the intermediary device, and read out of a different port.  The same is true for sending.

<insert another photo here

