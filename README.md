# Digital Clock – STM32 (Embedded Real-Time Systems)
## A digital clock developed on the STM32F103C8 (Blue Pill) microcontroller as part of the Embedded Real-Time Systems course.
https://github.com/user-attachments/assets/cea35933-9625-4ede-adba-10175e17f776


This project is an example of a digital clock that was conceptualized and implemented using the STM32 class of microcontrollers, with the following features:
- **Time and alarm settings** controlled through external interrupts  
- **Periodic time updates** handled by timer interrupts  
- **Sound generation** achieved by using PWM (Pulse Width Modulation)

## ⚙️ Hardware Setup
- **STM32F103C8 microcontroller** – Core of the system, manages timekeeping, alarm control, and sound generation.
- **TM1637 chip** – Drives the Grove 4-digit display and simplifies segment control. 
- **Grove 4-digit 7-segment display** – Displays the current/alarm time. 
- **Push buttons (x4)** – Enable user interaction for setting hours, minutes, and switching between clock and alarm modes.
- **Sounder (buzzer)** – Generates the alarm melody.

## 💻 Software Tools
- **STM32CubeIDE** – Used for project setup, peripheral configuration, C code development, compilation, and debugging. 
- **Proteus** – Used for circuit simulation, virtual hardware testing, and firmware validation.

## ⏰ Time Display and Update
The current time (hours and minutes) is managed through global variables that are updated using timer interrupts.  
A hardware timer is configured to trigger a periodic interrupt every 60 seconds, ensuring precise timekeeping.  
The TM1637 display driver updates the screen via the `updateDisplay()` function, synchronizing visual output with timer events.  

## 🔧 Time and Alarm Configuration
External interrupts are used for user input via four push buttons:  
- **Time** – switches to time-setting mode  
- **Alarm** – switches to alarm-setting mode  
- **Hour** and **Minute** – increment time values  

Input handling ensures proper mode switching and prevents button conflicts.  
Both time and alarm settings wrap correctly (e.g., `23 → 0` for hours, `59 → 0` for minutes). 

## 🔔 Alarm Functionality
The alarm activates automatically when the current time matches the preset alarm time.  
A melody is generated using PWM (Pulse Width Modulation), where the pitch and tone are controlled by adjusting the timer’s auto-reload (ARR) and compare (CCR) registers.  
The sound is clean and distinct, with gradual pitch variation to create a recognizable alarm tone.  
