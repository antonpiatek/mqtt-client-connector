mqtt-client-connector
=====================

The MQTT connector enables you to extend the capability of IBM Integration Bus (IIB) to connect to an MQTT server. [IIB](http://www.ibm.com/software/products/us/en/integration-bus/) is available free of charge for developers. This repository includes nodes that allow you to publish and subscribe to topics on an MQTT server from a message flow, and a sample to demonstrate this. 

##Dependencies
Install [IBM Integration Bus Developer Edition](http://www.ibm.com/software/products/us/en/integration-bus/).

To avoid having to manually import the projects into the Integration Toolkit, install the EGit client. A specific version of the client is needed, see [additional instructions](INSTRUCTIONS.md).

##Setup
1. Clone the Git repositories and import the projects (see [additional instructions](INSTRUCTIONS.md) if you need more detailed instructions):
  * Clone and import the Eclipse Paho project (URI: git://git.eclipse.org/gitroot/paho/org.eclipse.paho.mqtt.java.git).
  * Clone and import this repository (URI:  git@github.com:ot4i/mqtt-client-connector.git).
 
2. Add the nodes to the Integration Toolkit:
  * Clean the projects by clicking **Project** on the menu bar, and selecting **Clean All**.
  * Define an eclipse classpath variable called IIB\_PATH which points to your IBM Integration Bus installation directory by opening the eclipse preferences (Window -> Preferences) and navigating to Java -> Build Path -> Classpath Variables and selecting NEW.
  * In the MQTTNodes project, you may need to remove the package declaration 'package ComIbm;' from the start of the two files MQTTInputNodeUDN.java and MQTTOutputNodeUDN.java. Note, every time a full build is run or the user defined node project is built, the package declaration will need to be removed from these files.
  * In the Application Development view of the Integration Development perspective, right-click the Independent Resource **MQTTNodes** and select **Start Simulation**. The MQTTNodes resource is now accessible to the Integration Toolkit, and the project MQTTSample is rebuilt.

3. Install the connector on IIB:
  * Export the MQTTConnector and the org.eclipse.paho.client.mqttv3 projects as separate jar files, with the same names as the projects, into your file system's *ConnectorRuntimeDirectory*, e.g. C:\Connectors\MQTT.
  * Ensure you have [created a default configuration](http://pic.dhe.ibm.com/infocenter/wmbhelp/v9r0m0/topic/com.ibm.etools.mft.doc/ae20200_.htm).
  * In the WebSphere MQ Explorer, under integration node *IB9NODE*, right-click **Configurable Services** and select **Import *.configurableservice** to import the mqtt.configurableservice from the MQTTSetupForIIB project. Note, if you do not see a Configurable Services option, ensure your integration node is connected (right-click and select **Connect**).
  * Restart integration node *IB9NODE*.

##Platforms
Tested on Windows 7 Pro N x64 with [IIB Developer Edition](http://www.ibm.com/software/products/us/en/integration-bus/).

##Copyright and license
Copyright 2013 IBM Corp. under the [Eclipse Public license](http://www.eclipse.org/legal/epl-v10.html).
