---
lab:
    title: 'Lab 04: Connect an IoT Device to Azure'
    module: 'Module 2: Devices and Device Communication'
---

# Connect an IoT Device to Azure

## Lab Scenario

Contoso is known for producing high quality cheeses. Due to the company's rapid growth in both popularity and sales, they want to take steps to ensure that their cheeses stay at the same high level of quality that their customers expect.

In the past, temperature and humidity data was collected by factory floor workers during each work shift. The company is concerned that the factory expansions will require increased monitoring as the new facilities come online and that a manual process for collecting data won't scale.

Contoso has decided to launch an automated system that uses IoT devices to monitor temperature and humidity. The rate at which telemetry data is communicated will be adjustable to help ensure that their manufacturing process is under control as batches of cheese proceed through environmentally sensitive processes.

To evaluate this asset monitoring solution prior to full scale implementation, you will be connecting an IoT device (that includes temperature and humidity sensors) to IoT Hub.

> **Note**: For the purposes of this lab, you will be creating a .NET Core console application that simulates the physical IoT device and sensors. Your simulated device will implement the IoT Device SDK and it will connect to IoT Hub just like a physical device would. Your simulated device will also communicate telemetry values using the same SDK resources used by a physical device, but the sensor readings will be generated values rather than real values read from temperature and humidity sensors.

## Architecure Diagram

![Lab 4 Architecture](media/LAB_AK_04-architecture.png)


## Exercise 1: Create an Azure IoT Hub Device ID using the Azure portal

In this exercise, you will open your IoT Hub in the Azure portal, add a new IoT device to the device registry, and then get a copy of the Connection String that IoT Hub created for your device (which you will use in your device code later in the lab).

> **Note**: This lab focuses on using IoT Hub to establish reliable and secure bidirectional communications between IoT Hub and your IoT device. The Microsoft Learn platform includes other Modules (and Learning Paths) that enable you to explore other IoT Hub capabilities. Collectively, this training will help you to build scalable, full-featured IoT solutions.

### Task 1: Create the Device

1. On the Azure portal, naviagate to Resource group named **az220-rg**.

1. On the resources tile, click **iot-az220-training-{your-id}**

1. On the left-side menu of your IoT Hub blade, under **Device management**, click **Devices**.

1. On the **Devices** pane, click **Add Device**.

1. In the **Device ID** field, enter **sensor-th-0001**

    +++sensor-th-0001+++

    The device identity (Device ID), is used for device authentication and access control.

    It is helpful to establish some form of naming convention for your device identities. There are several reasons for this, including that the device ID is the value IoT Hub uses to represent a device. Having a device ID that succinctly and informatively differentiates one device from another is therefor helpful.

    The suggested naming convention above, _sensor-th-0001_, identifies this device as a sensor enabled device (_sensor_) that reports temperature and humidity values (_-th_) and is the first device of this type in a series of up to 9999 (_-0001_). Contoso may have 200 or 5000 of these devices installed and reporting environmental conditions from the factory floor, and the device identity will be one of the ways that a device can be recognized.

1. Under **Authentication type**, ensure that **Symmetric key** is selected.

    Notice that there are three types of authentication available. In this lab you will leverage the simplest of the three, Symmetric key.

1. Under **Auto-generate keys**, ensure the checkbox is selected.

    With **Auto-generate keys** selected, the **Primary key** and **Secondary key** fields are hidden and will be populated once the record is saved. Un-selecting **Auto-generate keys** will display those fields, allowing for values to be entered directly.

1. Under **Connect this device to an IoT hub**, ensure that **Enable** is selected.

    You could choose the Disable option here during the initial creation of a device if you were creating the device entry ahead of rollout. You could also choose to set this value to Disable at some future time if you wished to retain the device record, but prevent the associated device from connecting to the IoT Hub.

1. Under **Parent device**, leave **No parent device** as the value.

    IoT devices may be parented by other devices such as IoT Edge devices.

1. To add this device record to the IoT Hub, click **Save**.

    After a few moments, the **IoT devices** pane will refresh and the new device will be listed.

    > **TIP**: You may need to refresh manually - click the **Refresh** button on the page, rather than refreshing the browser

### Task 2: Get the Device Connection String

In order for a device to connect to an IoT Hub, it needs to establish a connection. In this lab, you will use a connection string to connect your device directly to the IoT Hub (this for of authentication is often referred to as symmetric key authentication). When using Symmetric key authentication, there are two connection strings available - one that utilizes the Primary key, the other that uses the Secondary key. As noted above, the Primary and Secondary keys are only generated once the device record is saved. Therefore, to obtain one of the connection strings, you must first save the record (as you did in the task above) and then re-open the device record (which is what you are about to do).

1. On the **IoT devices** pane of your IoT Hub, under **DEVICE ID**, click **sensor-th-0001**.

1. Take a minute to review the contents of the **sensor-th-0001** device detail blade.

    In addition to the device properties, notice that the device detail blade provides access to a number of device related functions (such as Direct Method and Device Twin) along the top of the blade.

1. Notice that the key and connection string values are now populated.

    The values are obfuscated by default, but you can click the "eye" icon on the right of each field to toggle between showing and hiding the values.

1. To the right of the **Primary Connection String** field, click **Copy**.

    You can hover your mouse pointer over the button icons to display their names; the Copy button is on the far right.

    > **Note**: You will need to use the Primary Connection String value later in the lab, so you may want to save it to an accessible location (perhaps by pasting the value into a text editor such as Notepad).

    The connection string will be in the following format:

    ```text
    HostName={IoTHubName}.azure-devices.net;DeviceId=sensor-th-0001;SharedAccessKey={SharedAccessKey}
    ```

