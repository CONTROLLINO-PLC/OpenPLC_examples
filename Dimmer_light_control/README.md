
# PWM Light Intensity Control System

## Overview

This project implements a PWM-based light intensity control system using a single push button. The light can be set to varying brightness levels, starting from maximum brightness when turned on. Each subsequent press of the button decreases the light's intensity until it cycles back to full brightness. The control logic is programmed using OpenPLC software and is designed to run on a CONTROLLINO Micro device.

The program utilizes ladder logic to regulate the light's intensity, controlled via pulse-width modulation (PWM). The system behavior and ladder diagram components are described below.

## System Behavior

### Button-Controlled Light Intensity Adjustment

1. **Initial State:**  
   When the system is activated, pressing the button (`Control_button`) turns the light on at maximum intensity (`Full_bright`).
2. **Decreasing Brightness:**  
   Each subsequent button press reduces the brightness level in predefined steps until the light reaches the lowest level.
3. **Cycling Behavior:**  
   After the lowest brightness level, the next button press resets the light back to maximum brightness.
4. **Output Signal:**  
   The brightness is modulated by the `Light_output` signal, generated using PWM.

### State Variables

- **Full Brightness (`Full_bright`):** Indicates when the light is at its maximum intensity.
- **Light On (`Light_on_state`):** Represents the overall "ON" state of the light.
- **Reset State (`Reset_state`):** Handles the cycling back to maximum brightness.
- **Pulse Regulator (`Pulse_regulator`):** Determines the timing for PWM signal adjustments.

## Configuration

This system is designed to operate on the CONTROLLINO Micro model. Below is the configuration of the inputs, outputs, and timers used in the project.

### Wire Connection

![alt text](<images/Electric diagram.png>)

### Variables Table

| Name            | Type    | Description                                      |
|-----------------|---------|--------------------------------------------------|
| `Control_button` | BOOL    | Push button input to control brightness cycling. |
| `Light_output`   | BOOL    | PWM output controlling the light intensity.      |
| `Light_bright`   | INT     | Tracks the current brightness level.             |
| `Pulse_regulator`| TIME    | Timing variable for PWM modulation.              |
| `Light_on_state` | BOOL    | Indicates whether the light is currently on.     |
| `Reset_state`    | BOOL    | Resets the brightness level to maximum.          |
| `Flag_cicle`     | BOOL    | Controls PWM signal cycling.                     |
| `Full_bright`    | BOOL    | Indicates the full brightness state.             |
| `CTU0`           | CTU     | Counter used to cycle through brightness levels. |
| `TP0`            | TP      | Timer for PWM pulse duration.                    |
| `TOF0`           | TOF     | Timer to deactivate output after a delay.        |

![alt text](<images/OpemPLC Variables.png>)

## Ladder Logic Explanation

### Button Press and Brightness Cycling

1. **Counter (`CTU0`)**:
   - Counts the number of button presses (`Control_button`).
   - Cycles through brightness levels (0, 1, 2, 3) and resets to 0 after reaching 3.

2. **Brightness Level Comparison**:
   - Comparators (`EQ`, `GT`) evaluate the current brightness level (`Light_bright`) to determine the appropriate PWM pulse width.

3. **PWM Signal Generation**:
   - Timers (`TP0`, `TOF0`) regulate the on/off cycle of the PWM signal based on the current brightness level.

### Light Output Control

- The `Pulse_regulator` variable modulates the `Light_output` signal, adjusting the intensity based on the selected brightness level.

![alt text](<images/OplenPLC Program 1.png>)

![alt text](<images/OplenPLC Program 2.png>)

## How to Run

### Setup Instructions

1. **Install OpenPLC**: Download and install OpenPLC software from the official website.
2. **Load the Program**: Import the ladder logic program into the OpenPLC editor.
3. **Connect the Device**:
   - Assign the input and output variables (`Control_button` and `Light_output`) to the appropriate pins on the CONTROLLINO Micro.
   - Configure the variable addresses in OpenPLC to match your device's pinout.

### Testing

1. Power on the CONTROLLINO Micro device.
2. Press the button to toggle the light's brightness through its predefined levels.
3. Observe the PWM-controlled output signal on `Light_output`.
