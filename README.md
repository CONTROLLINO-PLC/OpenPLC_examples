# ❗Exelent news❗

## A tool to program your CONTROLLINO using IEC 61131-3 PLC programing languages  🤩🦾🚀

![header](images/header.png)

_[OpenPLC Proyect](https://openplcproject.com/)_, in the latest version of its IEC 61131-3 Editor, introduced the functionality to directly programming Arduino boards, and we have recently added support for our CONTROLLINOs. We remain committed to Open Source, and we believe that this tool will make it easy for our user community to develop automation solutions with an experience similar to what they are used to see in more traditional PLC development environments.

---

## Advantages of using OpenPLC Editor with CONTROLLINO

- Nice and mature IDE for IEC 61131-3 programing (Ladder, ST, IL, FBD and SFC). `!!! HOW GOOD SOUNDS THAT !!!` 🤗

- Simulation engine: You can simulate your program before uploaded to the CONTROLLINO. `!!! OMG REALLY !!!` 🤩

- Modbus RTU, Serial and TCP/IP: In our boards support we included the posibility of using the RS485 in our MAXI and MEGA families. `!!! YES IT'S TRUE !!!` 🚀

---

## OpenPLC Editor download, installation and update to include CONTROLLINO boards support

### Download and install

- Go to [OpenPLC download page](https://openplcproject.com/download/) and get the Editor according to your OS.
- After download just follow the normal installation process.

### Check for updates to include CONTROLLINO boards support

- After open for the first time go to File -> Check for updates...
- If there are any updates avialable acept them and `then restart OpenPLC Editor to apply the updates`.

![check_updates_1](images/check_updates_1.png) ![check_updates_2](images/check_updates_2.png)

- After update should be posible to select our boards in the arduido upload within dialog.

![check_updates_3](images/check_updates_3.png)

Maybe in the momment you are seen this turorial CONTROLLINO boards support is already included with the default install  but any way is always a good practice to check for updates ;)

## Awesome examples based on common real automation systems

We have prepared for you some real life automation examples that are easy to put to work, will definitely be useful for understanding how OpenPLC Editor works with CONTROLLINO, and maybe are the solution you want to build with a CONTROLLINO.

This tutorials are easy to test using the [CONTROLLINO Training Kit](https://www.controllino.com/product/controllino-training-kit/), so feel free to order if you want a faster learning and testing experience.

Please follow the links in the example names for more complete example documentation inside each example REDAME file.

### Example list

- [Stairs Lights Automation](./light_control): Stairs with three lights bottom, middle and top, for controlling there are two push button switches in the botton and the top that will turn on and off the lights and there is also and presence sensor...

- [Pump and Tank Automation](./pump_control): There is a pump to fill a tank that has two digital level sensors for high and low level, this pump is handled using a external contactor that also has a thermomagnetic protection, there is also lots of pilot indicators to signal each state...

- Soon we will add with the help of the comunity we will add other clasic PLC automation examples like Elevator and Trafic Lights.

### How to get and open examples

- Install git and clone the examples repository.

```bash
git clone https://github.com/CONTROLLINO-PLC/OpenPLC_examples.git
```

- Hit "Open" folder in the Editor interface and select the example folder you want to open.

![open_example_1](images/open_example_1.png) ![open_example_2](images/open_example_2.png)
