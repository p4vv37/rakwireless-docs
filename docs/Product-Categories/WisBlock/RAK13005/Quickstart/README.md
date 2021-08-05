---
rak_desc: Contains instructions and tutorials in installing and deploying your RAK13005. Instructions are written in a detailed and step-by-step manner for an easier experience in setting up your device. Aside from the hardware configuration, it also contains a software setup that includes detailed example codes that will help you get started.
tags:
  - quickstart
  - wisblock
  - RAK13005
prev: ../Overview/ 
next: ../Datasheet/ 
rak_img: /assets/images/wisblock/rak13005/overview/RAK13005_home.png
---

# RAK13005 Quick Start Guide

## Prerequisite

### What Do You Need?

Before going through each and every step on using RAK13005 WisBlock module, make sure to prepare the necessary items listed below:

#### Hardware 

- [RAK13005 WisBlock LIN Module](https://store.rakwireless.com/collections/wisblock-interface/products/lin-bus-module-rak13005)
- Your choice of [WisBlock Base](https://store.rakwireless.com/collections/wisblock-base/)
- Your choice of [WisBlock Core](https://store.rakwireless.com/collections/wisblock-core)
- USB Cable
- [Li-Ion/LiPo battery (optional)](/Product-Categories/WisBlock/RAK5005-O/Datasheet/#battery-connector)
- [Solar charger (optional)](/Product-Categories/WisBlock/RAK5005-O/Datasheet/#solar-panel-connector)

#### Software 

##### Arduino

- Download and install [Arduino IDE](https://www.arduino.cc/en/Main/Software).
- To add the RAKwireless Core boards on your Arduino Boards Manager, install the [RAKwireless Arduino BSP](https://github.com/RAKWireless/RAKwireless-Arduino-BSP-Index).

## Product Configuration

### Block Diagram

### Hardware Setup

RAK13005 is a WisBlock LIN Module that extends the WisBlock system to be used on communication protocol called Local Interconnect Network also known as LIN. This communication is initiated by the automotive industry for the communication of in-vehicle devices on cars. Today, LIN is also used in other applications that requires robust communication line. For more information about RAK13005, refer to the [Datasheet](../Datasheet/).

#### Pin Definition

<rk-img
  src="/assets/images/wisblock/rak13005/quickstart/rak13005-pinout.svg"
  width="30%"
  caption="RAK13005 Pin Definition"
/>

#### LIN Peripheral and Controller Mode Hardware Configuration

By default, the RAK13005 LIN Module is configured as Peripheral (slave), and an SMD resistor must be relocated to make the module operate in Controller mode (master). You need to use a soldering iron to reposition the resistor to make the module a LIN Controller. The resistor location is shown in Figure 2.

<rk-img
  src="/assets/images/wisblock/rak13005/quickstart/rak13005-mod.png"
  width="60%"
  caption="RAK13005 LIN Mode Configuration"
/>


#### Assembling and Disassembling of WisBlock Modules

##### Assembling

The RAK13005 module can be mounted on the IO slot of the WisBlock Base board, as shown in **Figure 3**. Also, always secure the connection of the WisBlock module by using the compatible screws.

<rk-img
  src="/assets/images/wisblock/rak13005/quickstart/mounting-mechanism.png"
  width="60%"
  caption="RAK13005 mounting connection to WisBlock Base module"
/>

##### RAK13005 Connector Crimping Mechanism

The RAK13005 features a fast-crimping terminal connector to simplify and ensure the wiring process on the fields. The fast-crimping terminal can support cable with a width between 20&nbsp;AWG to 24&nbsp;AWG. The usual stripping length is around 6 to 7&nbsp;mm. 

As shown in **Figure 4**, during the crimping process, you should first press down and maintain the spring head of the crimping terminal firmly, then insert the stripped cable head into the corresponding connector’s hole. Once inserted correctly, release the spring head, and the crimping process is completed.

<rk-img
  src="/assets/images/wisblock/rak13005/quickstart/crimping_process.png"
  width="40%"
  caption="RAK13005 Module Connector"
/>

##### Disassembling

The procedure in disassembling any type of WisBlock modules is the same. 

1. First, remove the screws.  

<rk-img
  src="/assets/images/wisblock/rak13005/quickstart/16.removing-screws.png"
  width="70%"
  caption="Removing screws from the WisBlock module"
/>

2. Once the screws are removed, check the silkscreen of the module to find the correct location where force can be applied.

<rk-img
  src="/assets/images/wisblock/rak13005/quickstart/17.detaching-silkscreen.png"
  width="70%"
  caption="Detaching silkscreen on the WisBlock module"
/>

3. Apply force to the module at the position of the connector, as shown in **Figure 7**, to detach the module from the baseboard.

<rk-img
  src="/assets/images/wisblock/rak13005/quickstart/18.detaching-module.png"
  width="70%"
  caption="Applying even forces on the proper location of a WisBlock module"
/>

::: tip 📝 NOTE
If you will connect other modules to the remaining WisBlock Base slots, check on the [WisBlock Pin Mapper](https://docs.rakwireless.com/Knowledge-Hub/Pin-Mapper/) tool for possible conflicts.
:::

Now, you can connect the battery (optional) and USB cable to start programming your WisBlock Core.

### Software Configuration and Example

In this example, you will be using two RAK13005 Modules to demonstrate LIN functionality.

These are the quick links that go directly to the software guide for the specific WisBlock Core module you use:

- [RAK13005 in RAK4631 WisBlock Core Guide](#rak13005-in-rak4631-wisblock-core-guide)
- [RAK13005 in RAK11200 WisBlock Core Guide](#rak13005-in-rak11200-wisblock-core-guide)

#### RAK13005 in RAK4631 WisBlock Core Guide

##### Arduino Setup

**Figure 8** is an illustration on how to use two RAK13005 LIN modules for communication application. One RAK13005 is configured as controller and the other RAK13005 is configured as peripheral. The SMD resistors that set the mode are highlighted in yellow box. 

<rk-img
  src="/assets/images/wisblock/rak13005/quickstart/RAK13005-LIN-Controller-and-Peripheral-Connection.png"
  width="70%"
  caption="Two RAK13005 Interconnection for Controller and Peripheral mode"
/>

1. First, you need to select the RAK4631 WisBlock Core. Install the [RAKwireless Arduino BSP](https://github.com/RAKWireless/RAKwireless-Arduino-BSP-Index) to find the RAK4631 in the Arduino board selection.

<rk-img
  src="/assets/images/wisblock/rak13005/quickstart/rak4631-board.png"
  width="100%"
  caption="Selecting RAK4631 as WisBlock Core"
/>

2. Next, install the RAKwireless TLE7259 library by via Arduino Library manager. Select `Sketch` followed by `Include Library` then ` Manage Libraries`.

<rk-img
  src="/assets/images/wisblock/rak13005/quickstart/managelibraries.png"
  width="100%"
  caption="Open Arduino Library Manager"
/>

3. Search for the RAKwireless TLE7259 on the search box. Select the latest version then click install. 

<rk-img
  src="/assets/images/wisblock/rak13005/quickstart/tle7259.png"
  width="100%"
  caption="Look for RAKwireless TLE7259 LIN Bus Library"
/>

4. After successful installation, close the Arduino Library window.

<rk-img
  src="/assets/images/wisblock/rak13005/quickstart/installed.png"
  width="100%"
  caption="RAKwireless TLE7259 LIN Bus Library Successfully Installed"
/>

5. The example code is now available in your Arduino IDE. Upload `RAK13005_linbus_master` on the RAK13005 module in controller mode and `RAK13005_linbus_slaver` on the RAK13005 module in peripheral mode.

6. Connect the first WisBlock with the RAK13005 module in controller mode and select the `RAK13005_linbus_master`.

<rk-img
  src="/assets/images/wisblock/rak13005/quickstart/example_master.png"
  width="100%"
  caption="Open the code for the RAK13005 Controller"
/>

7. Select the port where RAK4631 WisBlock Core is connected.

<rk-img
  src="/assets/images/wisblock/rak13005/quickstart/master_port.png"
  width="100%"
  caption="Select the Serial Port of RAK4631 for the RAK13005 LIN module in controller mode."
/>

8. Then upload the code to the WisBlock Core.

<rk-img
  src="/assets/images/wisblock/rak13005/quickstart/upload_master.png"
  width="100%"
  caption="Uploading the Code"
/>

<rk-img
  src="/assets/images/wisblock/rak13005/quickstart/master_success.png"
  width="100%"
  caption="Successful Code Upload"
/>

9.  After the successful code upload, you can now open the serial terminal and see the Serial output.

<rk-img
  src="/assets/images/wisblock/rak13005/quickstart/master_output.png"
  width="100%"
  caption="Serial Output of the RAK13005 Controller Mode"
/>

10. After the RAK13005 LIN Controller, you can now prepare the RAK13005 LIN Peripheral. Connect the second WisBlock with the RAK13005 in Peripheral mode then select `RAK13005_linbus_slaver`.

<rk-img
  src="/assets/images/wisblock/rak13005/quickstart/example_slave.png"
  width="100%"
  caption="Open the code for the RAK13005 Peripheral"
/>

11. Then select the port, which is the additional port from the previous port for the controller. You should see two ports in your Arduino IDE.

<rk-img
  src="/assets/images/wisblock/rak13005/quickstart/slave_port.png"
  width="100%"
  caption="Select the Serial Port of RAK4631 for the RAK13005 LIN module in peripheral mode."
/>

12. After ensuring the port matching the RAK13005 LIN Peripheral, you can now upload the code.

<rk-img
  src="/assets/images/wisblock/rak13005/quickstart/slave_upload.png"
  width="100%"
  caption="Uploading the Code"
/>

13. Then you can see the Serial Output on the RAK13005 Peripheral device receiving the data coming from the RAK13005 Controller device. You must have the external power supply connected to have successful transmissions.

<rk-img
  src="/assets/images/wisblock/rak13005/quickstart/slave_output.png"
  width="100%"
  caption="Serial Output of the RAK13005 Peripheral Mode"
/>


#### RAK13005 in RAK11200 WisBlock Core Guide

##### Arduino Setup

**Figure 22** is an illustration on how to use two RAK13005 LIN modules for communication application. One RAK13005 is configured as controller and the other RAK13005 is configured as peripheral. The SMD resistors that set the mode are highlighted in yellow box. 

<rk-img
  src="/assets/images/wisblock/rak13005/quickstart/RAK13005-LIN-Controller-and-Peripheral-Connection.png"
  width="70%"
  caption="Two RAK13005 Interconnection for Controller and Peripheral mode"
/>

1. First, you need to select the RAK11200 WisBlock Core. Install [RAKwireless Arduino BSP](https://github.com/RAKWireless/RAKwireless-Arduino-BSP-Index) to find the RAK4631 in the Arduino board selection.

<rk-img
  src="/assets/images/wisblock/rak13005/quickstart/rak11200-board.png"
  width="100%"
  caption="Selecting RAK4631 as WisBlock Core"
/>

2. Next, install the RAKwireless TLE7259 library by via Arduino Library manager. Select `Sketch` followed by `Include Library` then ` Manage Libraries`.

<rk-img
  src="/assets/images/wisblock/rak13005/quickstart/managelibraries.png"
  width="100%"
  caption="Open Arduino Library Manager"
/>

3. Search for the RAKwireless TLE7259 on the search box. Select the latest version then click install. 

<rk-img
  src="/assets/images/wisblock/rak13005/quickstart/tle7259.png"
  width="100%"
  caption="Look for RAKwireless TLE7259 LIN Bus Library"
/>

4. After successful installation, close the Arduino Library window.

<rk-img
  src="/assets/images/wisblock/rak13005/quickstart/installed.png"
  width="100%"
  caption="RAKwireless TLE7259 LIN Bus Library Successfully Installed"
/>

5. The example code is now available in your Arduino IDE. Upload the `RAK13005_linbus_master` on the RAK13005 module in controller mode then `RAK13005_linbus_slaver` on the RAK13005 module in peripheral mode.

6. Connect the first WisBlock with the RAK13005 module in controller mode and select the `RAK13005_linbus_master`.

<rk-img
  src="/assets/images/wisblock/rak13005/quickstart/e32_example_master.png"
  width="100%"
  caption="Open the code for the RAK13005 Controller"
/>

7. Select the port where RAK11200 WisBlock Core is connected.

<rk-img
  src="/assets/images/wisblock/rak13005/quickstart/e32_master_port.png"
  width="100%"
  caption="Select the Serial Port of RAK11200 for the RAK13005 LIN module in controller mode."
/>

8. Then upload the code to the WisBlock Core.

<rk-img
  src="/assets/images/wisblock/rak13005/quickstart/e32_upload_master.png"
  width="100%"
  caption="Uploading the Code"
/>

<rk-img
  src="/assets/images/wisblock/rak13005/quickstart/e32_master_success.png"
  width="100%"
  caption="Successful Code Upload"
/>

9. After the successful code upload, you can now open the serial terminal and see the Serial output.

<rk-img
  src="/assets/images/wisblock/rak13005/quickstart/e32_master_output.png"
  width="100%"
  caption="Serial Output of the RAK13005 Controller Mode"
/>

10. After the RAK13005 LIN Controller, you can now prepare the RAK13005 LIN Peripheral. Connect the second WisBlock with the RAK13005 in Peripheral mode then select `RAK13005_linbus_slaver`.

<rk-img
  src="/assets/images/wisblock/rak13005/quickstart/e32_example_slave.png"
  width="100%"
  caption="Open the code for the RAK13005 Peripheral"
/>

11. Then select the port, which is the additional port from the previous port for the controller. You should see two ports in your Arduino IDE.

<rk-img
  src="/assets/images/wisblock/rak13005/quickstart/e32_slave_port.png"
  width="100%"
  caption="Select the Serial Port of RAK4631 for the RAK13005 LIN module in peripheral mode."
/>

:::tip 📝 NOTE:
RAK11200 requires the BOOT0 pin to be configured properly before uploading. If not done properly, uploading the source code to RAK11200 will fail. Check the full details on the [RAK11200 Quick Start Guide](/Product-Categories/WisBlock/RAK11200/Quickstart/#uploading-to-wisblock).
:::

12.  After ensuring the port matching the RAK13005 LIN Peripheral, you can now upload the code.

<rk-img
  src="/assets/images/wisblock/rak13005/quickstart/e32_slave_upload.png"
  width="100%"
  caption="Uploading the Code"
/>


13. Then you can see the Serial Output on the RAK13005 Peripheral device receiving the data coming from the RAK13005 Controller device. You must have the external power supply connected to have successful transmissions.



<rk-img
  src="/assets/images/wisblock/rak13005/quickstart/e32_slave_output.png"
  width="100%"
  caption="Serial Output of the RAK13005 Peripheral Mode"
/>