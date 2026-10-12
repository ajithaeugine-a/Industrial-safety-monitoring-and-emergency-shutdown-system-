# Industrial safety monitoring and emergency shutdown system
The Industrial Safety Monitoring and Emergency Shutdown System Using LPC2129 is an embedded systems project designed to improve industrial safety by detecting dangerous conditions and stopping a motor during emergencies.
The system uses the LPC2129 (ARM7) microcontroller as the main controller. An IR sensor detects the presence of an object or obstacle, while an emergency push button provides a manual shutdown mechanism using an external interrupt (EINT0).
When the IR sensor detects a configured danger condition, the microcontroller stops the DC motor through the L293D motor driver, activates the LED indicator, and displays a warning message on the LCD. When the emergency switch is pressed, an external interrupt triggers the emergency shutdown routine.
This project demonstrates the practical implementation of embedded C programming, ARM7 microcontroller interfacing, sensor monitoring, motor control, LCD interfacing, and external interrupt handling.

Objectives
- Detect objects or obstacles using an IR sensor.
- Stop the DC motor when a configured danger condition is detected.
- Implement an emergency shutdown mechanism using an external interrupt.
- Display system status messages on an LCD.
- Provide visual alerts through an LED indicator.
- Understand GPIO configuration and peripheral interfacing using the LPC2129 microcontroller.

Features
- Automatic Obstacle Detection: Uses an IR sensor to detect objects or obstacles.
- Emergency Shutdown: Uses the EINT0 external interrupt to stop the motor when the emergency switch is pressed.
- Motor Control: Controls a DC motor through the L293D motor driver.
- LCD Status Display: Displays system status messages such as SYSTEM NORMAL, DANGER, and MOTOR STOPPED.
- LED Indication: Provides a visual warning during danger or emergency conditions.
- ARM7-Based Control: Implements the system using the LPC2129 microcontroller and embedded C.
- UART Communication: Can support serial communication between the PC and the development board when configured.
  
Hardware Components
- LPC2129 Development Board: Acts as the main controller and processes sensor inputs.
- IR Sensor: Detects the presence of an object or obstacle.
- L293D Motor Driver: Drives the DC motor using control signals from the microcontroller.
- DC Motor: Represents the machine or moving equipment being controlled.
- LCD Display: Displays the current system status and warning messages.
- Emergency Push Button: Triggers an external interrupt to initiate emergency shutdown.
- LED Indicator: Provides a visual indication of danger or emergency conditions.
- PC: Used for writing, compiling, downloading, and debugging the embedded C program.
- Power Supply: Provides the required power to the microcontroller and connected components.

Pin Configuration
The project uses the following LPC2129 pin assignments:
- P0.10 – IR Sensor: Configured as an input to read the IR sensor output.
- P0.11 – LED: Controls the LED indicator.
- P0.12 – MOTOR_IN1: Provides the first motor direction control signal to the L293D.
- P0.13 – MOTOR_IN2: Provides the second motor direction control signal to the L293D.
- P0.14 – MOTOR_EN: Controls the enable input of the L293D motor driver.
- P0.16 / EINT0 – Emergency Switch: Used to trigger an external interrupt when the emergency switch is pressed.
The LCD pin assignments depend on the connections defined in the LCD header file.
The IR sensor logic assumes that a LOW output indicates the configured danger condition. The LED control uses active-low logic in the current implementation, meaning LOW turns the LED on and HIGH turns it off.
The EINT0 function must be selected through the appropriate pin configuration register. The emergency switch must also be wired to produce the required falling-edge signal.

Working Principle
1. System Initialization
The LPC2129 initializes the LCD, motor control pins, LED, IR sensor input, and EINT0 external interrupt. After initialization, the microcontroller enables interrupts and begins monitoring the system.
2. Normal Operation
When no danger condition is detected, the microcontroller enables the DC motor through the L293D motor driver. The LED remains off, and the LCD displays the normal operating status.
3. Obstacle Detection
When the IR sensor output becomes LOW, the microcontroller identifies the configured danger condition and stops the motor. The LED turns on, and the LCD displays a warning message indicating that the motor has stopped.
4. Emergency Shutdown
When the emergency push button is pressed, the EINT0 external interrupt is triggered. The interrupt service routine sets the emergency flag, stops the motor, and activates the LED.
The LCD displays an emergency message indicating that the motor has stopped. In the current implementation, the emergency state remains active until the microcontroller is reset.

Applications
- Conveyor Belt Systems: Demonstrates obstacle detection and motor shutdown.
- Automated Production Lines: Demonstrates automatic motor stopping when a configured hazard is detected.
- Machine Safety Prototypes: Demonstrates basic obstacle sensing and emergency stopping.
- Industrial Automation Training: Helps students understand sensor interfacing, motor control, and interrupt handling.
- Embedded Systems Education: Provides practical experience with ARM7-based embedded C development.
