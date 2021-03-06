# Pump and Tank Automation Example

![pump_control](images/pump_control.png)

These example is easy to test using the [CONTROLLINO Training Kit](https://www.controllino.com/product/controllino-training-kit/), so feel free to order if you want a faster learning and testing experience. But you also can tested in other CONTROLLINO taking into account its [pinout](../README.md#controllino-pinout-definitions-for-openplc-integration).

See main [README](../README.md#how-to-get-and-open-examples) to learn how to open this example in OpenPLC Editor.

## Behavior

- The start button starts the process, the pump will try to maintain the level between the low and high levels.
- The stop button stops the process.
- The pump turns on when the level is lower than the low level sensor and stops when it reaches the high level.
- The low level indicator will blink with a period of N milliseconds in case of critical level, meaning that the level is bellow low level sensor.
- The emergency condition stops the process and occurs when the magnetothermic pump protection activates its auxiliary contact, or the pump feedback from pump contactor auxiliary contact is not received after N seconds, or also when the pump does not reach the desired level after N seconds.
- In an emergency condition, the emergency indicator blink with a period of N milliseconds.
- After the emergency condition, the start button must be pressed to reset the emergency condition and try to restart the process, also the stop button resets the emergency condition.

## Pinout

Outputs:

- DO0 -> %QX0.0 -> Process running/emergency pilot
- DO1 -> %QX0.1 -> Pump working pilot
- DO2 -> %QX0.2 -> High level pilot
- DO3 -> %QX0.3 -> Low/critical level pilot
- R0  -> %QX1.0 -> Control pump contactor coil

Inputs:

- AI2 -> %IX0.0 -> NO Pump contactor auxiliary contact
- AI3 -> %IX0.1 -> NO High level sensor contact
- AI4 -> %IX0.2 -> NO Low level sensor contact
- AI5 -> %IX0.3 -> NC Pump magnetothermic protection auxiliary contact
- AI6 -> %IX0.4 -> NO Start button
- AI7 -> %IX0.5 -> NC Stop button
