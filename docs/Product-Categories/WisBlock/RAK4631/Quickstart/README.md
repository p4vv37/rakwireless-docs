---
rak_desc: Contains instructions and tutorials in installing and deploying your RAK4631. Instructions are written in a detailed and step-by-step manner for an easier experience in setting up your device. Aside from the hardware configuration, it also contains a software setup that includes detailed example codes that will help you get started.
rak_img: /assets/images/wisblock/rak4631/overview/RAK4631_home.png
prev: ../Overview/
next: ../Datasheet/
tags:
  - RAK4631
  - quickstart
  - wisblock
---

# RAK4631 Quick Start Guide

This guide introduces the RAK4631 WisBlock Core LPWAN Module and how to use it. RAK4631 consists of a nRF52840 MCU and a SX1262 LoRa® chip making it ideal for various IoT projects.

## Prerequisite

### What Do You Need?

Before going through each and every step on using RAK4631 WisBlock module, make sure to prepare the necessary items listed below:

#### Hardware

- [RAK4631 WisBlock Core LPWAN Module](https://store.rakwireless.com/collections/wisblock-core/products/rak4631-lpwan-node)
- Your choice of [WisBlock Base](https://store.rakwireless.com/collections/wisblock-base) 
- Your choice of [WisBlock Modules](https://store.rakwireless.com/pages/wisblock)
- USB Cable
- Li-Ion/LiPo battery with JST PHR-2 2&nbsp;mm female connector (optional)
- Solar charger (optional)

RAK4631 is also included in various WisBlock kits in RAKwireless store:

- [WisBlock Starter Kit](https://store.rakwireless.com/collections/kits-bundles/products/wisblock-starter-kit) - This includes a RAK4631 with RAK5005-O WisBlock Base board. This kit is ideal to get started immediately with WisBlock.
- [WisBlock Kit](https://store.rakwireless.com/collections/kits-bundles/products/wisblock-kit?variant=37758662049990) - This is like the Starter Kit but with various WisBlock modules already included on the kit like sensors, IO, and other interfaces.
- [WisBlock Connected Box](https://store.rakwireless.com/collections/kits-bundles/products/wisblock-connected-box) - This is like the WisBlock Kit but cheaper because some modules and peripherals are not included. **Excluded** parts are RAKBox-B5, RAK1921, RAKDAP1, electric screwdriver (manual is included), and battery holder.
- [Helium Developer Kit](https://store.rakwireless.com/collections/kits-bundles/products/helium-developer-kit) - This is the WisBlock Kit for the Helium brand.


#### Software

You can choose Arduino IDE or Platform IO in coding RAK4631 WisBlock Core.

<b>Programming RAK4631 via Arduino IDE:</b>

- Download and install [Arduino IDE](https://www.arduino.cc/en/Main/Software).
- To add the WisBlock Core boards on your Arduino board, you need to install the RAKwireless Arduino BSP. You can follow this complete guide on [adding the BSP in Arduino IDE](https://docs.rakwireless.com/Knowledge-Hub/Learn/Installation-of-Board-Support-Package-in-Arduino-IDE/). You can also have a look on the RAKwireless Arduino BSP [github repository](https://github.com/RAKWireless/RAKwireless-Arduino-BSP-Index).

In Arduino IDE, once you installed the BSP, the examples for RAK4631 will be automatically included on the list of examples when you select WisBlock Core RAK4631 Board in the Board Manager. 

<b>Programming RAK4631 via Platform IO:</b>

- [Platform IO for RAK4631 complete setup guide](https://docs.rakwireless.com/Knowledge-Hub/Learn/Board-Support-Package-Installation-in-PlatformIO/)

## Product Configuration

### Hardware Setup

#### RAK4631 to WisBlock Base

The RAK4631 will not work without a WisBlock Base board. The WisBlock Base provides a USB connection for programming the RAK4631. It also provides a power source and various interfaces to RAK4631 so that it can be connected to other WisBlock modules via different module slots. To illustrate, RAK4631 can be connected to RAK5005-O WisBlock Base, as shown in Figure 1.

<rk-img
  src="/assets/images/wisblock/rak4631/quickstart/RAK5005-connect.png"
  width="80%"
  caption="RAK4631 Connection to WisBlock Base RAK5005-O"
/>

There are few pins that are exposed on RAK5005-O, and you can easily use them via header pins. The labels are at the back, as shown in Figure 2.

<rk-img
  src="/assets/images/wisblock/rak4631/quickstart/IO-pins.png"
  width="35%"
  caption="WisBlock Base exposed pins"
/>

More information can be found on the [official documentation of the specific WisBlock Base](https://docs.rakwireless.com/Product-Categories/WisBlock/#wisblock-base) you used in your project.

For RAK5005-O WisBlock Base with RAK4631 WisBlock Core, the accessible GPIO pins are defined as follows in the Arduino IDE and Platform IO:

- `WB_IO1` for IO1 pin
- `WB_IO2` for IO2 pin (Also used to control the 3.3V supply of some WisBlock Modules to achieve low-power IoT devices.)
- `WB_A0` for AIN

There are usable LEDs as well that can be controlled by the RAK4631 on the WisBlock Base board:

- `WB_LED1` for LED1   
- `WB_LED2` for LED2

UART1 and I2C_1 are also exposed on the header of the WisBlock Base board.

- RAK4631 has a native USB peripheral onboard (Serial) which is used for programming and Serial debugging and two usable hardware **UART1** and **UART2** (Serial 1 and Serial 2). **UART1** is accessible to WisBlock Slot A, WisBlock IO slot, and the exposed header pins. **UART2** is accessible only on the WisBlock IO slot.
- The **I2C_1** header pins are as well shared to the WisBlock Base Slots A to D. The second **I2C_2** is available only on the WisBlock IO slot.


#### RAK4631 to WisBlock Modules

RAK4631 WisBlock Core is designed to be interfaced to other WisBlock Modules like sensors, displays, and other interfaces. You need to connect these modules to the compatible slots on the WisBlock Base.

Each WisBlock Modules that will be used with RAK4631 WisBlock Core have a dedicated quick start guide you can follow on how to connect to the WisBlock Base.

Listed are the quick start guide of some [WisBlock modules you can buy from our store](https://store.rakwireless.com/pages/wisblock):

- [RAK1901 Quick Start Guide](https://docs.rakwireless.com/Product-Categories/WisBlock/RAK1901/Quickstart/)
- [RAK1902 Quick Start Guide](https://docs.rakwireless.com/Product-Categories/WisBlock/RAK1902/Quickstart/)
- [RAK1903 Quick Start Guide](https://docs.rakwireless.com/Product-Categories/WisBlock/RAK1903/Quickstart/)

Figure 3 shows an illustration on how you can combine various WisBlock Modules with the RAK4631 WisBlock Core via the WisBlock Base board.

<rk-img
  src="/assets/images/wisblock/rak4631/quickstart/exa-weather-assy.png"
  width="70%"
  caption="RAK4631 Connection to WisBlock Base and other WisBlock Modules"
/>

#### Assembling and Disassembling of WisBlock Modules

##### Assembling

Figure 4 shows how to mount the RAK4631 module on top of a WisBlock Base board (RAK5005-O). Follow carefully the procedure defined in [WisBlock module assembly/disassembly instructions](https://docs.rakwireless.com/Knowledge-Hub/Learn/RAK5005-O-Baseboard-Installation-Guide/) in order to secure the connection safely. Once attached, carefully fix the module with one or more pieces of M1.2 x 3&nbsp;mm screws depending on the module.

<rk-img
  src="/assets/images/wisblock/rak4631/datasheet/mounting-sketch.png"
  width="50%"
  caption="RAK4631 Mounting Sketch"
/>

##### Disassembling

The procedure in disassembling any type of WisBlock modules is the same. 

1. First, remove the screws.  

<rk-img
  src="/assets/images/wisblock/rak1910/quickstart/16.removing-screws.png"
  width="70%"
  caption="Removing screws from the WisBlock module"
/>

2. Once the screws are removed, check the silkscreen of the module to find the correct location where force can be applier.

<rk-img
  src="/assets/images/wisblock/rak1910/quickstart/17.detaching-silkscreen.png"
  width="70%"
  caption="Detaching silkscreen on the WisBlock module"
/>

3. Apply force to the module at the position of the connector, as shown in Figure 7, to detach the module from the baseboard.

<rk-img
  src="/assets/images/wisblock/rak1910/quickstart/18.detaching-module.png"
  width="70%"
  caption="Applying even forces on the proper location of a WisBlock module"
/>

#### LoRa and BLE Antenna

Another important part component of RAK4631 are the antennas. 

<rk-img
  src="/assets/images/wisblock/rak4631/quickstart/lora-antenna.png"
  width="30%"
  caption="LoRa Antenna"
/>

<rk-img
  src="/assets/images/wisblock/rak4631/quickstart/ble-antenna.png"
  width="40%"
  caption="BLE Antenna"
/>

You need to ensure that it is properly connected to have a good LoRa and BLE signal. You can damage the RF section of the chip if you leave the IPEX connector without antenna connected.

RAK4631 has a label on its sticker where to connect the antennas, as shown in Figure 10.


<rk-img
  src="/assets/images/wisblock/rak4631/quickstart/RAK4631-antenna-label.png"
  width="30%"
  caption="RAK4631 Antenna Label"
/>

:::tip 📝 NOTE
Detailed information about the RAK4631 BLE and LoRa antenna can be found on the [antenna datasheet](https://downloads.rakwireless.com/LoRa/WisBlock/Accessories/). 
:::

:::warning ⚠️ WARNING
When using the LoRa or Bluetooth Low Energy transceivers, make sure that an antenna is always connected. Using these transceivers without an antenna can damage the system. Make sure to fix the module with the screws to ensure a proper function.
:::

#### Battery and Solar Connection

RAK4631 can be power via the USB cable or Li-Ion/LiPo battery via the dedicated connectors as shown in Figure 11. The matching connector for the battery wires is an [JST PHR-2 2&nbsp;mm pitch female](https://www.jst-mfg.com/product/detail_e.php?series=199)

<rk-img
  src="/assets/images/wisblock/rak4631/quickstart/battery-connect.png"
  width="50%"
  caption="WisBlock Base Connection"
/>

<rk-img
  src="/assets/images/wisblock/quickstart/battery-connection.gif"
  width="25%"
  caption="Battery Connection"
/>

The battery can be recharged as well via small solar panel, as shown in Figure 13. The matching connector for the solar panel wires is an [JST ZHR-2 1.5&nbsp;mm pitch female](https://www.jst-mfg.com/product/detail_e.php?series=287).

<rk-img
  src="/assets/images/wisblock/rak4631/quickstart/solar-connect.png"
  width="90%"
  caption="Solar Panel Connection"
/>

Specification of the battery and solar panel can be found on the datasheet of the WisBlock Base.

:::warning ⚠️ WARNING

- Only 3.7-4.2&nbsp;V Rechargeable LiPo batteries are supported. Do not use other types of batteries with the system.
- Only 5&nbsp;V solar panels are supported. Do not use 12&nbsp;V solar panels. It will destroy the charging unit and eventually other electronic parts.
- Make sure the battery wires are matching the polarity on the RAK5005-O board. Not all batteries have the same wiring.

:::


### Software Setup

RAK4631 WisBlock Core is designed to be interfaced to other WisBlock Modules like sensors, displays, and other interfaces. To make useful devices, you need to upload a source code to the RAK4631. Before you continue, you should have either the [Arduino BSP or Platform IO already setup](/Product-Categories/WisBlock/RAK4631/Quickstart/#software).

#### RAK4631 Example Repository

To quickly build your IoT device with less friction, example codes for RAK4631 to be used on all WisBlock Modules are provided. 

You can access the codes on the [WisBlock Example code repository](https://github.com/RAKWireless/WisBlock/tree/master/examples). The example codes compatible to RAK4631 are in the folders `RAK4630` and `common` of that example repository. 

To use these examples, you have two options: Arduino IDE or Platform IO.

##### RAK4631 on Arduino IDE

To access the example codes of various WisBlock Modules like the RAK1901 and RAK1902, install the [BSP for the Arduino IDE](/Product-Categories/WisBlock/RAK4631/Quickstart/#software) as mentioned in the prerequisite part of the this guide. Getting the code on the example repository is not necessary. As long as you selected RAK4631 in the Arduino IDE Board Manager, you can browse the different examples on the Arduino IDE easily, as shown in Figure 14.

<rk-img
  src="/assets/images/wisblock/rak4631/quickstart/rak4631_gps.png"
  width="100%"
  caption="RAK4631 WisBlock Core Examples"
/>

It is highly recommended to also check the dedicated quick start guide that you can follow on various WisBlock Modules. Each quick start guide of these modules contains the detailed steps on how to open the example codes and upload it to the RAK4631.

Listed are the examples where you can check the Software Setup on the quick start guide of the following WisBlock Modules:

- [RAK1901 Quick Start Guide](https://docs.rakwireless.com/Product-Categories/WisBlock/RAK1901/Quickstart/)
- [RAK1902 Quick Start Guide](https://docs.rakwireless.com/Product-Categories/WisBlock/RAK1902/Quickstart/)
- [RAK1903 Quick Start Guide](https://docs.rakwireless.com/Product-Categories/WisBlock/RAK1903/Quickstart/)

##### RAK4631 on Platform IO

For the Platform IO, get the example codes on the [WisBlock Example code repository](https://github.com/RAKWireless/WisBlock/examples) and add the necessary libraries individually. Then you can compile the example code.

#### Connecting RAK4631 to LoRaWAN

RAK4631 is the WisBlock Core capable of LoRaWAN connectivity.

There is an example on how to start with LoRaWAN in the **RAK WisBlock examples** in Arduino IDE named `LoRaWAN_OTAA_ABP`. This is also available in the [WisBlock Repository](https://github.com/RAKWireless/WisBlock/blob/master/examples/RAK4630/communications/LoRa/LoRaWAN/LoRaWAN_OTAA_ABP/LoRaWAN_OTAA_ABP.ino).

<rk-img
  src="/assets/images/wisblock/rak4631/quickstart/lora_solution.png"
  width="100%"
  caption="RAK4631 LoRaWAN Example"
/>

##### Configuration of LoRaWAN Example Code

There are configurations that you need to setup to ensure that the device can join a LoRaWAN Network server.

The guide below will explain the default settings and how to configure it.

1. Setup the region.

Default is EU868.

```
LoRaMacRegion_t g_CurrentRegion = LORAMAC_REGION_EU868;
```

You can change this to a region that is applicable to you like `LORAMAC_REGION_US915`, `LORAMAC_REGION_AU915`, etc.

2. Setup the activation method.

Default is **OTAA**.

```
bool doOTAA = true;
```

To configure the device to ABP, you need to make this boolean variable `false`.

3. Setup the message type if confirmed or not.

Default is **confirmed message**.

```
lmh_confirm g_CurrentConfirm = LMH_CONFIRMED_MSG;
```
You can change to unconfirmed message by changing the value to `LMH_UNCONFIRMED_MSG`.

4. Setup device class.

Default is **Class A**.

```
DeviceClass_t g_CurrentClass = CLASS_A;	
```
You can change this to `CLASS_B` (still underdevelopment) or `CLASS_C`.

5. Setup the keys.

If configured for OTAA Activation,

```
uint8_t nodeDeviceEUI[8] = {0x88, 0x88, 0x88, 0x88, 0x88, 0x88, 0x33, 0x33};
uint8_t nodeAppEUI[8] = {0xB8, 0x27, 0xEB, 0xFF, 0xFE, 0x39, 0x00, 0x00};
uint8_t nodeAppKey[16] = {0x88, 0x88, 0x88, 0x88, 0x88, 0x88, 0x88, 0x88, 0x88, 0x88, 0x88, 0x88, 0x88, 0x88, 0x88, 0x88};
```

If configured for OTAA Activation,

```
uint32_t nodeDevAddr = 0x260116F8;
uint8_t nodeNwsKey[16] = {0x7E, 0xAC, 0xE2, 0x55, 0xB8, 0xA5, 0xE2, 0x69, 0x91, 0x51, 0x96, 0x06, 0x47, 0x56, 0x9D, 0x23};
uint8_t nodeAppsKey[16] = {0xFB, 0xAC, 0xB6, 0x47, 0xF3, 0x58, 0x45, 0xC7, 0x50, 0x7D, 0xBF, 0x16, 0x8B, 0xA8, 0xC1, 0x7C};
```

6. Setup uplink period.

The default is **20000&nbsp;mS**. 

```
#define LORAWAN_APP_INTERVAL 20000
```
You can make the transmission interval faster or slower by changing this value.


##### LoRaWAN Payload

This default example will send a string `Hello!` to the LoRaWAN server. This is setup on the `void send_lora_frame(void)` function.

```
    memset(m_lora_app_data.buffer, 0, LORAWAN_APP_DATA_BUFF_SIZE);
    m_lora_app_data.port = gAppPort;
    m_lora_app_data.buffer[i++] = 'H';
    m_lora_app_data.buffer[i++] = 'e';
    m_lora_app_data.buffer[i++] = 'l';
    m_lora_app_data.buffer[i++] = 'l';
    m_lora_app_data.buffer[i++] = 'o';
    m_lora_app_data.buffer[i++] = '!';
    m_lora_app_data.buffsize = i;
```

The LoRaWAN payload is packaged in this function.

You can change this section to format your payload.

##### Formatting the Payload

For illustration, you can check how 32bit **ilat** variable is formatted to 4-byte size array.

This is the exact code snippet in formatting the Latitude data of the [GPS Tracker](https://github.com/RAKWireless/WisBlock/blob/master/examples/RAK4630/solutions/GPS_Tracker/GPS_Tracker.ino) example. 

```
    gps.f_get_position(&flat, &flon, &age);
    flat == TinyGPS::GPS_INVALID_F_ANGLE ? 0.0 : flat;
    ilat = flat * 100000;

    // longitude section...
    
    m_lora_app_data.port = gAppPort;
    m_lora_app_data.buffer[0] = 0x09;
    //lat data
    m_lora_app_data.buffer[1] = (ilat & 0xFF000000) >> 24;
    m_lora_app_data.buffer[2] = (ilat & 0x00FF0000) >> 16;
    m_lora_app_data.buffer[3] = (ilat & 0x0000FF00) >> 8;
    m_lora_app_data.buffer[4] =  ilat & 0x000000FF;
```

Another important part of the code is configuring the size of the payload.

This is done on the `m_lora_app_data.buffsize` variable. For illustration above with only **ilat** as the value to send, you need to set the buffer size to 5 because the array starts from 0 up to 4.

```
    m_lora_app_data.buffsize = 5;
```

##### Decoding the Payload on the LoRaWAN Network Server

On the LoRaWAN network server side like TTN, Chirpstack, Helium, etc., the value transmitted can be retrieved via decoding the payload.

```
    latitude_int = (bytes[1] << 24) | (bytes[2] << 16) | (bytes[3] << 8) | (bytes[4]);
    decoded.latitude = latitude_int / 100000;
```

##### Important Function in the LoRaWAN Example.

LoRa periodic transmission function should be very short and all reading and processing of the data must be in the main loop.
```
void tx_lora_periodic_handler(void)
```

Same with the transmission function, the receiving event handler should be short as well. All processing of the received data should be in the main loop.
```
void lorawan_rx_handler(lmh_app_data_t *app_data)
```

##### Uploading the LoRaWAN Code

After all the configuration is done and the payload is already formatted properly, you can now compile and upload the code.

If you get errors compiling the LoRaWAN example, ensure that you have an updated BSP by checking it in board manager.

<rk-img
  src="/assets/images/wisblock/rak4631/quickstart/bsp_version.png"
  width="60%"
  caption="RAK4631 BSP(Board Support Package) in Arduino IDE Board Manager"
/>
  
You also need to ensure that you have the updated SX126x.

<rk-img
  src="/assets/images/wisblock/rak4631/quickstart/sx126x_lib.png"
  width="60%"
  caption="SX126x-Arduino Library"
/>

:::tip 📝 NOTE
On the other hand, if the error is related to the difficulty of uploading the FW, try to double click the reset button on the WisBlock Base board and reupload it again.
:::

#### RAK4631 LoRa Mesh via Meshtastic

[Meshtastic](https://meshtastic.org/) is an open source community project that uses LoRa technology to make long-range mesh communicator.

RAK4631 Meshtastic FW support is first released on Meshtastic 1.2.30 Beta. You need to [download the 1.2.30 Beta release](https://github.com/meshtastic/Meshtastic-device/releases/download/v1.2.30.80e4bc6/firmware-1.2.30.80e4bc6.zip) to get the RAK4631 Meshtastic FW named `firmware-rak4631-1.2.30.80e4bc6.uf2`.

To upload this to the RAK4631 board, connect the RAK4631 to the PC via USB. Then double click the reset button on the WisBlock Base board to see the `RAK4631 drive`.

You have few seconds to drag the `firmware-rak4631-1.2.30.80e4bc6.uf2` file to the RAK4631. 

Once you successfully dragged the Meshtastic FW file, restart the device. After reset, you must have a Meshtastic display on the OLED if you successfully uploaded the Meshtastic firmware.

You can get also get an android device and download Meshtastic App then connect to RAK4631 via Bluetooth.

:::tip 📝 NOTE
Meshtastic is constantly changing and it is advisable to check the [Meshtastic device repository](https://github.com/meshtastic/Meshtastic-device) every time you will use RAK4631 as a Meshtastic node.
:::

The bootloader of RAK4631 is not overwritten by the Meshtastic FW. You also override the Meshtastic FW by uploading another Arduino or Platform IO code.


## Miscellaneous

### How to Check if You Have the Updated RAK4631 Bootloader

You need to connect the RAK4631 to the PC via USB cable and double click reset button on the WisBlock Base.

There will be a new drive named `RAK4631` that will be shown on your folder explorer. Inside this drive, there will a text file named `INFO_UF2.TXT`, as shown in Figure 18.

<rk-img
  src="/assets/images/wisblock/rak4631/quickstart/new_drive.png"
  width="60%"
  caption="RAK4631 drive content"
/>

If you open `INFO_UF2.TXT`, you'll see `Date: Mar 31 2021`, as shown in Figure 19.

<rk-img
  src="/assets/images/wisblock/rak4631/quickstart/info_uf2txt.png"
  width="40%"
  caption="INFO_UF2.TXT content"
/>

If you have a different drive name or older date, it means you do not have the updated RAK4631 Bootloader and you need to update it. 


### Updating the Bootloader

RAK4631 WisBlock Core is programmed with a USB bootloader so that you can upload application firmware to it without using any external tools like Jlink and other programmers/debuggers. However, there are situations that you need to update the bootloader when there is an updated version that supports new features, improvements, and bug fixes.

There are various ways to update the bootloader like via USB, Bluetooth, and Jlink. The procedure for these methods is explained in this guide. 

#### Bootloader update via USB

In this method, you need two things:

1. Adafruit-nrfutil utility program.
2. RAK4631 Bootloader FW.

##### For Windows

Download the [adafruit-nrfutil.exe](https://github.com/adafruit/Adafruit_nRF52_nrfutil/releases/download/%24(APPVEYOR_REPO_TAG_NAME)/adafruit-nrfutil.exe) and the latest [RAK4631 bootloader firmware](https://github.com/RAKWireless/WisBlock/blob/0093b9b5d7ec3c32c3fe3550b797fe364582b083/bootloader/RAK4630/new/RAK4630_bootloader-0.4.1.zip).

:::tip 📝 NOTE
Detailed information about the RAK4631 Bootloader can be found on the [bootloader repository](https://github.com/RAKWireless/WisBlock/tree/0093b9b5d7ec3c32c3fe3550b797fe364582b083/bootloader/RAK4630). 
:::

Once you downloaded these files, you need to put them on a same directory/folder in your computer.

For simplicity, this guide will assume the files are in C: drive.

<rk-img
  src="/assets/images/wisblock/rak4631/quickstart/c_location.png"
  width="70%"
  caption="Adafruit-nrfutil and RAK4631 Bootloader file in C: drive"
/>

When the files are ready, you need to open Windows Command Prompt application. Then you need to change the location to C:\.

`cd C:\`

After that, you can now execute the update using this command.

`adafruit-nrfutil.exe --verbose dfu serial --package RAK4630_bootloader-0.4.1.zip --port COM8 -b 115200 --singlebank --touch 1200`

<rk-img
  src="/assets/images/wisblock/rak4631/quickstart/success_upload.png"
  width="100%"
  caption="RAK4631 Bootloader Updated Successfully"
/>

You need to determine the right COM port number of your device. COM8 on the command above is only for illustration. You will get an error if you are not connected to the right COM port number.

##### For Linux

You can get and install adafruit-nrfutil via pip3.

`sudo pip3 install adafruit-nrfutil`

or

`pip3 install --user adafruit-nrfutil`

Then download the latest [RAK4631 bootloader firmware](https://github.com/RAKWireless/WisBlock/blob/0093b9b5d7ec3c32c3fe3550b797fe364582b083/bootloader/RAK4630/new/RAK4630_bootloader-0.4.1.zip).

You also need to determine the port name of the RAK4631 using the command:

`ls /dev/tty*`

After determining the port name, go to the directory where the bootloader FW file `RAK4630_bootloader-0.4.1.zip` is located.

Then execute the following command:

`adafruit-nrfutil --verbose dfu serial --package RAK4630_bootloader-0.4.1.zip -p /dev/ttyACM0 -b 115200 --singlebank --touch 1200`


##### For macOS

The same with Windows and Linux procedures, download the latest [RAK4631 bootloader firmware](https://github.com/RAKWireless/WisBlock/blob/0093b9b5d7ec3c32c3fe3550b797fe364582b083/bootloader/RAK4630/new/RAK4630_bootloader-0.4.1.zip).

There are two ways to update the RAK4631 bootloader in macOS.

- If you have Python installed, you can follow the same steps for Linux.

- Another way is by creating a macOS executable. To do this method, download [adafruit-nrfutil-macos](https://github.com/adafruit/Adafruit_nRF52_nrfutil/releases/download/%24(APPVEYOR_REPO_TAG_NAME)/adafruit-nrfutil-macos) and make it executable.

Usually, the `adafruit-nrfutil-macos` file will go to the downloads folder. 

The next step after downloading the file is to open the terminal and go to the downloads directory or the location where you put the downloaded file.

`cd /Users/username/Downloads`

And then execute this command:

`chmod +x adafruit-nrfutil-macos`

<rk-img
  src="/assets/images/wisblock/rak4631/quickstart/macos_executable.png"
  width="50%"
  caption="Executable adafruit-nrfutil-macos"
/>

You also need to determine the port name of the RAK4631 using the command:

`ls /dev/cu.*`.

<rk-img
  src="/assets/images/wisblock/rak4631/quickstart/macos_checkport.png"
  width="50%"
  caption="Checking the RAK4631 USB port connection"
/>

After all these steps, you can now upload the latest RAK4631 Bootloader Firmware by executing this command:

`adafruit-nrfutil-macos --verbose dfu serial --package RAK4630_bootloader-0.4.1.zip -p /dev/cu.usbmodem411 -b 115200 --singlebank --touch 1200`

<rk-img
  src="/assets/images/wisblock/rak4631/quickstart/macos_boot_update.png"
  width="60%"
  caption="Updated RAK4631 Bootloader"
/>

Your RAK4631 will now have the updated Bootloader Firmware.

#### Bootloader update via Bluetooth

Updating the firmware via BLE is also possible.

The complete guide is on the [RAK4631 Bootloader repository using BLE](https://github.com/RAKWireless/WisBlock/tree/0093b9b5d7ec3c32c3fe3550b797fe364582b083/bootloader/RAK4630/new).

#### Bootloader update via Jlink

Updating the firmware via Jlink is possible as well.

The complete guide is on the [RAK4631 Bootloader repository using Jlink](https://github.com/RAKWireless/WisBlock/tree/0093b9b5d7ec3c32c3fe3550b797fe364582b083/bootloader/RAK4630).









 

