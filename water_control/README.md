
# Water Reserve Control System

## Overview

This project demonstrates an automatic control system for a water reserve system, which includes a cistern, an elevated tank, and a pump that supplies water from the cistern to the elevated tank. The system uses three sensors to monitor the minimum level of the cistern, and the minimum and maximum levels of the elevated tank.

The control logic is programmed using OpenPLC software, as illustrated in the provided ladder diagram. This code can be deployed on any CONTROLLINO model, provided the input and output connections match the assigned variable names in the PLC program.

## System Behavior

1. **Automatic Control**:  
   When the system is in automatic mode, the pump is activated to fill the elevated tank if:
   - The tank's water level is at the minimum.
   - The cistern’s water level is above the minimum.

   The pump will stop when:
   - The cistern's water level reaches the minimum level.
   - The tank’s water level reaches the maximum.

2. **Manual Control**:  
   Additionally, there are start and stop buttons connected to the CONTROLLINO that allow manual control over the pump, irrespective of the automatic signals.

![alt text](<images/Level water control.jpg>)

## Configuration

This project can be tested with the CONTROLLINO Training Kit for an easy learning experience or with any CONTROLLINO model by configuring the input and output pins as described below.

### Pinout

#### Outputs

- **DO0** -> `%QX0.0` -> `Water_Pump`  
  Controls the pump; a high signal turns on the motor.

#### Inputs

- **DI0** -> `%IX0.0` -> `Pool_Low_Level_Sensor`  
  Indicates the minimum water level in the cistern. A low signal means the cistern is below the minimum level.

- **DI1** -> `%IX0.1` -> `Tank_High_Level_Sensor`  
  Indicates the maximum water level in the elevated tank. A high signal means the tank has reached the maximum level.

- **DI2** -> `%IX0.2` -> `Tank_Low_Level_Sensor`  
  Indicates the minimum water level in the elevated tank. A low signal means the tank is below the minimum level.

- **DI3** -> `%IX0.3` -> `Automatic_Manual_Switch`  
  Switch for selecting automatic or manual mode. A low state indicates manual mode, while a high state enables automatic mode.

- **DI4** -> `%IX0.4` -> `Stop_Button`  
  Push button to stop the pump manually. When pressed, it sends a high signal to stop the pump.

- **DI5** -> `%IX0.5` -> `Start_Button`  
  Push button to start the pump manually. When pressed, it sends a high signal to start the pump.

![alt text](<images/Esquema de conexion.png>)

## Ladder Logic Explanation

The ladder diagram below (refer to the attached image) shows the control logic programmed in OpenPLC for this system:

![alt text](<images/OpenPLC program.png>)

- **Automatic Mode Logic**:  
  - The `Automatic_Manual_Switch` input enables automatic control.
  - When `Pool_Low_Level_Sensor` and `Tank_Low_Level_Sensor` are activated (i.e., cistern above minimum and tank below minimum), the `Water_Pump` output is set.
  - The `Tank_High_Level_Sensor` or `Pool_Low_Level_Sensor` deactivating will reset the `Water_Pump`, turning off the pump.

- **Manual Mode Logic**:  
  - The `Start_Button` and `Stop_Button` inputs allow direct manual control of the `Water_Pump`.
  - Pressing `Start_Button` will set the `Water_Pump` output to high, activating the pump.
  - Pressing `Stop_Button` will reset the `Water_Pump`, turning it off.

This setup ensures reliable control over the water pumping process, automating tank filling based on water levels and providing manual override options.

## How to Run

1. **Install OpenPLC**: Follow the instructions in the main README to set up and open this example in the OpenPLC Editor.
2. **Load to CONTROLLINO**: Connect the appropriate inputs and outputs on your CONTROLLINO device as per the configuration table above.
3. **Test the System**: Test the system by switching between automatic and manual modes and observing the behavior of the pump based on water levels.
