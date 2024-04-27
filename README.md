# 8051 Motor Monitoring System with IR and Hall Effect Sensors
This project implements a motor monitoring system using an 8051 microcontroller.
The system monitors the motor's rotation and magnetic field using an IR sensor and a Hall effect sensor, respectively.
The data is then displayed on a 16x2 LCD.
Other contributors: @Manishkumar1062 @Ayush180204

***Hardware Requirements:***
- 8051 Microcontroller
- 16x2 LCD Display
- IR Sensor
- Hall Effect Sensor
- ADC (Analog-to-Digital Converter) (optional, can be internal to the microcontroller)
- LEDs (2)
- Resistors (as required for circuit)

***Software Requirements:***
* Keil uVision (or similar IDE for 8051)
* [stcgal](https://github.com/grigorig/stcgal) (Open-source tool for flashing STC microcontrollers)

***Description:***
The code utilizes several functions to manage the LCD display, sensor data acquisition, and LED control.

_Main Function:_
Initializes LEDs, LCD, and ADC (if external).
Continuously reads sensor values and displays them on the LCD.
Controls LEDs based on the IR sensor threshold.

_LCD Functions:_
+ LCD_Ready(): Checks if the LCD is ready to receive data.
+ LCD_CMD(): Sends a command to the LCD.
+ LCD_DATA(): Sends data to the LCD.
+ LCD_init(): Initializes the LCD display.
+ convert_display_LCD(): Converts a float value (IR sensor voltage) to a string with two decimal places for LCD display.

_Sensor Functions:_
+ display_mag(): Displays the Hall effect sensor data (magnet state) on the LCD and controls LED_1.
+ display_prox(): Displays the IR sensor data (voltage) on the LCD, controls LED_2 based on a threshold, and performs a delay.

***Notes:***
+ The code assumes a specific LCD pin configuration and instruction set. You might need to modify it based on your LCD model.
+ The ADC configuration and data reading might need adjustments depending on your specific ADC implementation (internal or external).
+ The threshold value for the IR sensor can be adjusted in the main function.

***How to Use:***
1. Connect the hardware components.
2. Compile the code using your preferred 8051 IDE.
3. Download the compiled code to your microcontroller using stcgal.
   stcgal is an open-source tool available on GitHub that can be used to program STC microcontrollers. Refer to the stcgal documentation for usage instructions specific to your system.[^1]
4. Power on the system and observe the LCD display.

***Further Development:***
- Implement functionalities based on the sensor readings (e.g., motor speed calculation, fault detection).
- Integrate communication protocols for remote monitoring or data logging.
- Enhance the user interface with additional displays or menus.

[^1]: We used the Keil IDE to create a hex file from the C Code, and dumped that to the 8051 using the `stcgal -p {PORTNAME} {HEXFILEPATH}` command.
