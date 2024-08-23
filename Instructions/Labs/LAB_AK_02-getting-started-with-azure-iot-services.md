# Getting Started with Azure IoT Services

# Module 1: Introduction to IoT and Azure IoT Services

## Lab Scenario

You are an Azure IoT Developer working for Contoso, a company that crafts and distributes gourmet cheeses.

You have been tasked with exploring Azure and the Azure IoT services that you will using to develop Contoso's IoT solution. You have already become familiar with the Azure portal and created a resource group for your project. Now you need to begin investigating the Azure IoT services.

## In This Lab

In this lab, you will create and examine an Azure IoT Hub and an IoT Hub Device Provisioning Service. The lab includes the following exercises:

* Create an IoT Hub using the Azure portal
* Examine features of the IoT Hub service
* Create a Device Provisioning Service and link it to your IoT Hub
* Examine features of the Device Provisioning Service

## Lab Instructions


### Exercise 1: Create an IoT Hub using the Azure portal

The Azure IoT Hub is a fully managed service that enables reliable and secure bidirectional communications between IoT devices and Azure. The Azure IoT Hub service provides the following:

* Establish bidirectional communication with billions of IoT devices
* Multiple device-to-cloud and cloud-to-device communication options, including one-way messaging, file transfer, and request-reply methods.
* Built-in declarative message routing to other Azure services.
* A queryable store for device metadata and synchronized state information.
* Secure communications and access control using per-device security keys or X.509 certificates.
* Extensive monitoring for device connectivity and device identity management events.
* SDK device libraries for the most popular languages and platforms.

In this exercise, you will use the Azure portal to create and configure your IoT Hub.

#### Task 1: Use the Azure portal to create a IoT Hub with required property settings

   
1. On the Azure portal menu, click **+ Create a resource**.

    ![](media/create.png)

1. In the Azure portal, in the **Search resources, services, and Docs (G+/)** bar search **iot hub** and click on it.

    ![](media/hub.png)

1. To begin the process of creating your new IoT Hub, click **Create**.

    ![](media/createiot.png)
    
1. On the **IoT hub** blades **Basics** tab, in the **Subscription** dropdown, select the available Subscription **(1)**.
 
1. Select your **Resource group(2)** from the drop down menu.

1. Enter the **IoT hub name**: **iot-az220-training-cah<inject key="DeploymentID" enableCopy="false"/>(3)**
      
    > **Note**:  Azure will ensure that the name you enter is unique. If the name that you enter is not unique, Azure will display a message below the name field as a warning. If you see the warning message, you should update your unique ID. Try appending your unique ID with '**00**', or '**01**', or '**02**, 'etc. as necessary to achieve a globally unique name.

    > **Note**: Some resource names do not allow extended characters like the dash (-) or underscore (_), so stick with numeric digits when updating your unique ID.

1. **Region** : **<inject key="Region" enableCopy="false"/>** 

1. Select the **Tier** as **Free(5)** from the drop down.

    ![](media/randc.png)

1. At the top of the blade, click **Networking**.

1. Ensure the **Minimum TLS Version** is set to **1.0**.

    ![](media/Net.png)

1. At the top of the blade, click **Management**.

1. Under **Scale** (you may need to scroll down), ensure that **Device-to-cloud partitions** is set to **2**.

    ![](media/manage.png)

1. At the bottom of the blade, click **Review + create**.

1. click **Create**.

    Deployment can take a minute or more to complete. 

1. Once the Deployment is completed,Click on **Go to resource** and then you will be able to see the newly created IoT Hub.

    ![](media/iothub.png)


### Exercise 2: Examine the IoT Hub Service

IoT Hub is a managed service, hosted in the cloud, that acts as a central message hub for bi-directional communication between your Azure IoT services and your connected devices.


In this exercise, you will examine some of the features that IoT Hub provides.

#### Task 1: Explore the IoT Hub Overview information

1. Open your Azure dashboard.

1. Search and select **IoT hub** and then click on the newly created **iot-az220-training-cah<inject key="DeploymentID" enableCopy="false"/>**

    ![](media/iot10.png)

1. At the bottom of your IoT Hub blade **Overview** page, notice the **IoT Hub Usage** tile.


1. To the right of the **IoT Hub Usage(1)** tile, notice the **Number of messages used(2)** tile and the **Device to cloud messages(3)** tile.

    ![](media/iott11.png)

    The **Device to cloud messages** tile provides a quick view of the incoming messages from your devices over time.

    The **Number of messages used** tile can help you to keep track of the total number of messages used.

#### Task 2: View features of IoT Hub using the left-side menu

1. On the IoT Hub blade,from the left navigation menu,under **Device management**, click **Devices**

    ![](media/iot12.png)

    This pane can be used to add, modify, and delete devices registered to your hub.


1. On the left-side menu, near the top, click **Activity log**

    As the name implies, this pane gives you access to a log that can be used to review activities and diagnose issues. 

    ![](media/iott13.png)

1. On the left-side menu, under **Hub settings**, click **Built-in endpoints**

    IoT Hub exposes "endpoints" that enable external connections. Essentially, an endpoint is anything connected to or communicating with your IoT Hub. You should see that your hub already has endpoints defined, including the following:

    * _Event Hub compatible endpoint_ **(1)**
    * _Cloud to device messaging_ **(2)**

    ![](media/iot14.png)

1. On the left-side menu, under **Hub settings**, click **Message routing**

    The IoT Hub message routing feature enables you to route incoming device-to-cloud messages to service endpoints such as Azure Storage containers, Event Hubs, and Service Bus queues. You can also create routing rules to perform query-based routes.

1. At the top of the **Message routing** pane, click **Custom endpoints**.

    ![](media/iot15.png)

    Custom endpoints (such as Event Hubs and Storage) are often used within an IoT implementation.

    > **Note**:  This lab exercise is only intended to be an introduction to the IoT Hub service and get you more comfortable with the UI, so don't worry if you feel a bit overwhelmed at this point.

### Exercise 3: Create a Device Provisioning Service using the Azure portal

The Azure IoT Hub Device Provisioning Service is a helper service for IoT Hub that enables zero-touch, just-in-time provisioning to the right IoT hub without requiring human intervention. The Device Provisioning Service provides the following:

* Zero-touch provisioning to a single IoT solution without hardcoding IoT Hub connection information at the factory (initial setup)
* Load balancing devices across multiple hubs
* Connecting devices to their owner's IoT solution based on sales transaction data (multitenancy)
* Connecting devices to a particular IoT solution depending on use-case (solution isolation)
* Connecting a device to the IoT hub with the lowest latency (geo-sharding)
* Reprovisioning based on a change in the device
* Rolling the keys used by the device to connect to IoT Hub (when not using X.509 certificates to connect)

#### Task 1: Use the Azure portal to a Device Provisioning Service with required property settings

1. On the Azure portal menu, click **+ Create a resource**.

1. In the Search textbox, type **device provisioning service(1)** and then press Enter.


1. On the **Marketplace** blade, click **IoT Hub Device Provisioning Service(2)** search result.

    ![](media/iot16.png)

1. To begin the process of creating your new DPS instance, click **Create**.

    ![](media/iot29.png)

1. **Subscription**: Select the available subscription from the drop down **(1)**

1. **Resource Group**: Select your Resource group **(2)**

1. **Name**: Enter a globally unique name.
    For example: **dps-az220-training-cah<inject key="DeploymentID" enableCopy="false"/>(3)**

1. **Region**: **<inject key="Region" enableCopy="false"/>**

    > **Note**: When picking a datacenter to host your resources, keep in mind that picking a datacenter close to your end users will decrease load/response times. If you are on the other side of the world from your end users, you should not be picking the datacenter nearest you.

1. At the bottom of the blade, **Review + create**, and then click **Create**.

    ![](media/iot18.png)

1. After the deployement is completed, click on **Go to resource** to see the newly created **DPS**.

#### Task 2: Link your IoT Hub and Device Provisioning Service.

1. On the Azure dashboard you can see the list of both your **IoT Hub(2)** and **DPS resources(1)**.

    ![](media/iott19.png)

1.click on **dps-az220-training-cah281216**.

1. On the **Device Provisioning Service** blade, under **Settings**, click **Linked IoT hubs(1)**.

1. At the top of the blade, click **+ Add(2)**.

1. On the **Add link to IoT hub** blade, ensure that the **Subscription(3)** dropdown is displaying the subscription that you are using for this lab.

1. Open the IoT hub dropdown, and then click **iot-az220-training-cah<inject key="DeploymentID" enableCopy="false"/>(4)**.

    This is the IoT Hub that you created in the previous exercise.

1. In the Access Policy dropdown, select **iothubowner(5)**.

1. Click on **Save(6)**.

    ![](media/iott20.png)

1. Here you can see the newly created Lined IoT hub.

    ![](media/iott21.png)

### Exercise 4: Examine the Device Provisioning Service

The IoT Hub Device Provisioning Service is a helper service for IoT Hub that enables zero-touch, just-in-time provisioning to the right IoT hub without requiring human intervention, enabling customers to provision millions of devices in a secure and scalable manner.

#### Task 1: Explore the Device Provisioning Service Overview information

1. On your Azure dashboard, click on the three lines **(1)** at the top left corner and select **All resources(2)**

    ![](media/iot22.png)

1. On the All resources tile, click **dps-az220-training-cah281216**

    ![](media/iott23.png)

    * [Azure IoT Hub Device Provisioning Service Documentation](https://docs.microsoft.com/en-us/azure/iot-dps/)
    * [Learn more about IoT Hub Device Provisioning Service](https://docs.microsoft.com/en-us/azure/iot-dps/about-iot-dps)
    * [Device Provisioning concepts](https://docs.microsoft.com/en-us/azure/iot-dps/concepts-service)
    * [Pricing and scale details](https://azure.microsoft.com/en-us/pricing/details/iot-hub/)

    When time permits, you can come back and explore these links.

#### Task 2: View features of Device Provisioning Service using the navigation menu


1. On the left-side menu, near the top, click **Activity log**

    As the name implies, this pane gives you access to a log that can be used to review activities and diagnose issues. You can also define queries that help with routine tasks. Very handy.

    ![](media/iott24.png)

1. On the left-side menu, under **Settings**, click **Quick Start**.

    This pane lists the steps to start using the Iot Hub Device Provisioning Service, links to documentation and shortcuts to other blades for configuring DPS.

    ![](media/iott25.png)

1. On the left-side menu, under **Settings**, click **Shared access policies**.

    This pane provides management of access policies, lists the existing policies and the associated permissions.

    ![](media/iott26.png)

1. On the left-side menu, under **Settings**, click **Linked IoT hubs**.

    Here you can see the linked IoT Hub from earlier. The Device Provisioning Service can only provision devices to IoT hubs that have been linked to it. Linking an IoT hub to an instance of the Device Provisioning service gives the service read/write permissions to the IoT hub's device registry; with the link, a Device Provisioning service can register a device ID and set the initial configuration in the device twin. 

    ![](media/iott27.png)


1. On the left-side menu, under **Settings**, click **Certificates(1)**.

    Here you can manage the X.509 certificates that can be used to secure your Azure IoT hub using the X.509 Certificate Authentication.

1. On the left-side menu, under **Settings**, click **Manage enrollments(2)**.

    Here you can manage the enrollment groups and individual enrollments.

    Enrollment groups can be used for a large number of devices that share a desired initial configuration, or for devices all going to the same tenant. An enrollment group is a group of devices that share a specific attestation mechanism. Enrollment groups support both X.509 as well as symmetric. 

    An individual enrollment is an entry for a single device that may register. 

    ![](media/iot28.png)

1. Take a minute to review some of the other menu options under **Settings**

   > **Note**:  This lab exercise is only intended to be an introduction to the IoT Hub Device Provisioning Service and get you more comfortable with the UI, so don't worry if you feel a bit overwhelmed at this point.
