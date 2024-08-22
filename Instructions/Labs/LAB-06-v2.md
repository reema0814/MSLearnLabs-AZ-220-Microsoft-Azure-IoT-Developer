# Automate IoT Device Management with Azure IoT Hub

IoT devices often use optimized operating systems or even run code directly on the silicon (without the need for an actual operating system). In order to update the software running on devices like these the most common method is to flash a new version of the entire software package, including the OS as well as the apps running on it (called firmware).

Because each device has a specific purpose, its firmware is also very specific and optimized for the purpose of the device as well as the constrained resources available.

The process for updating firmware can also be specific to the hardware and to the way the hardware manufacturer created the board. This means that a part of the firmware update process is not generic and you will need to work with your device manufacturer to get the details of the firmware update process (unless you are developing your own hardware which means you probably know what the firmware update process).

While firmware updates used to be applied manually on individual devices, this practice no longer makes sense considering the number of devices used in typical IoT solutions. Firmware updates are now more commonly done over-the-air (OTA) with deployments of new firmware managed remotely from the cloud.

There is a set of common denominators to all over-the-air firmware updates for IoT devices:

1. Firmware versions are uniquely identified
1. Firmware comes in a binary file format that the device will need to acquire from an online source
1. Firmware is locally stored is some form of physical storage (ROM memory, hard drive,...)
1. Device manufacturer provide a description of the required operations on the device to update the firmware.

Azure IoT Hub offers advanced support for implementing device management operations on single devices and on collections of devices. The [Automatic Device Management](https://docs.microsoft.com/azure/iot-hub/iot-hub-auto-device-config) feature enables you to simply configure a set of operations, trigger them, and then monitor their progress.

## Lab Scenario

The automated air processing system that you implemented in Contoso's cheese caves has helped the company to raise their already high quality bar. The company has more award-winning cheeses than ever before.

Your base solution consists of IoT devices that are integrated with sensors and a climate control system to provide real-time control of temperature and humidity within a multi-chamber cave system. You also developed a simple back-end app that demonstrated the ability to manage devices using both direct methods and device twin properties.

Contoso has extended the simple back-end app from your initial solution to include an online portal that operators can use to monitor and remotely manage the cave environment. With the new portal, operators can even customize the temperature and humidity within the cave based on the type of cheese or for a specific phase within the cheese aging process. Each chamber or zone within the cave can be controlled separately.

The IT department will be maintaining the back-end portal that they developed for the operators, but your manager has agreed to manage the device-side of the solution.

For you, this means two things:

1. The Operations team at Contoso is always looking for ways to make improvements. These improvements often lead to requests for new features in the device software.

1. The IoT devices that are deployed to cave locations need the latest security patches to ensure privacy and to prevent hackers from taking control of the system. In order to maintain system security, you need to keep the devices up to date by remotely updating their firmware.

You plan to implement features of IoT Hub that enable automatic device management and device management at scale.

The following resources will be created:

![Lab 16 Architecture](media/LAB_AK_16-architecture.png)
