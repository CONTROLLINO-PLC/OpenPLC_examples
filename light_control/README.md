# Stairs Lights Automation Example

![light_control](images/light_control.png)

These example is easy to test using the [CONTROLLINO Training Kit](https://www.controllino.com/product/controllino-training-kit/), so feel free to order if you want a faster learning and testing experience. But you also can tested in other CONTROLLINO taking into account its [pinout](../README.md#controllino-pinout-definitions-for-openplc-integration).

See main [README](../README.md#how-to-get-and-open-examples) to learn how to open this example in OpenPLC Editor.

## Behavior

- The switches at both ends of the stairs are push buttons and will turn the lights on and off.
- The lights will turn on and off in sequence with a delay of N milliseconds.
- The lights will turn off after N seconds if no presence is detected on a sensor that is placed in the middle of the stairs.

## Pinout

Outputs:

- DO0 -> %QX0.0 -> LIGHT_DOWN
- DO1 -> %QX0.1 -> LIGHT_MIDDLE
- DO2 -> %QX0.2 -> LIGHT_UP

Inputs:

- AI2 -> %IX0.0 -> SWITCH_DOWN
- AI3 -> %IX0.1 -> SWITCH_UP
- AI4 -> %IX0.2 -> PRESENCE_SENSOR
