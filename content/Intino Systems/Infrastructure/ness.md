---
title: "Ness"
date: 2024-07-18T15:00:00Z
draft: false
---
**Latest version**: [https://github.com/intino/ness/releases/latest](https://github.com/intino/ness/releases/latest).

Ness is an [infrastructure](../) framework that facilitates the creation, management, and distribution of datahub services. This framework includes features such as the management of a messaging broker supporting JMS OpenWire and MQTT protocols, a datalake for storing and organizing events, configurable terminals for client interaction, and shared datamarts for customized data projections.

These features make Ness a practical framework for businesses looking to optimize their data flows and improve decision-making based on events. Ness ensures that all components of a company's IT architecture are aligned with their business objectives, providing a foundation for scalability and adaptability in today's business environment.

Additionally, the [Ness DSL](#dsl) allows the specialization of Ness: the [infrastructure](../) datahub service. This DSL allows for fine-tuned customization and configuration, ensuring that the datahub services can be customized to meet specific business needs and requirements.

## Main Features

Ness is designed with a range of functionalities that support complex event-driven architectures. The key features include:

### Event Structures

Ness enables the definition of event structures, providing a common conceptual framework for all clients connected to the architecture. This standardization helps in maintaining consistency and understanding across different systems and data streams.

### Messaging Broker

The platform includes a messaging broker that supports JMS OpenWire and MQTT protocols. This broker is implemented using the well-established open-source software, [Apache ActiveMQ](https://activemq.apache.org/components/classic/documentation/), ensuring robust and reliable message handling. The use of Apache ActiveMQ also facilitates easy integration and compatibility with various systems and technologies.

### Datalake

Ness features a datalake that organizes events based on the format of the event—be it a message, measurement, or resource—and by the type of event according to business criteria. Events are also grouped and sorted temporally, enabling efficient data retrieval and analysis.

### Terminals

Terminals within Ness describe the different clients that can access the broker. These terminals allow for the configuration of subscription and event production policies from and to the datalake, tailoring access and interaction according to specific client needs. Additionally, using Intino, it is possible to generate customized client libraries for a specific DataHub instance based on these terminal definitions. This enhances the ease of integration and streamlines client setup.

### Shared Datamarts

Ness allows for the creation of shared datamarts, which are projections of the datalake into defined data structures that can be used and shared by connected clients. These projections are also configured in the DSL, providing flexible and customizable data views for users.

## DSL

[Ness](.) provides a homonym domain-specific language (DSL) to allow users to precisely configure and customize the various components of their event-driven architecture. This section of the wiki provides guidance on how to use the DSL to set up and manage the capabilities of DataHub.

### Metamodel

The latest complete version of the source metamodel of the DSL can be found at the following [link](https://github.com/intino/ness/blob/develop/data-hub/src/io/intino/datahub/model/Model.tara). This metamodel serves as a comprehensive definition of all configurable elements within DataHub.

### Step-by-Step Configuration Example

Below, we will walk through an example of how to configure each capability of DataHub using the DSL. This example will cover setting up event structures, the messaging broker, the datalake, terminals, and shared datamarts, providing a practical guide to understanding and applying the DSL in a real-world scenario.

<div style="text-align: center;">
  <img src="File:Ness-m1.png" alt="Example of configuring components in a Datahub" style="width: 50%;">
</div>

In the provided DSL example, a datalake and a broker are configured to manage events and resources in DataHub, using a clear and organized structure that enables efficient data management. The datalake is established with a daily time scale and is located in the "/home/intino/datalake" directory. Additionally, a scheduled task is included to seal data every day at 4:00 AM, which helps maintain the integrity and efficiency of data storage. In this case, the [cron](http://www.cronmaker.com/) format is used to define the period.

Within the `Datalake`, several containers or "tanks" are created. One is dedicated to storing analysis measurements every five minutes, another records logs as resources, and a third tank handles incidents, storing them as messages. Each of these tanks is configured to handle specific types of data, reflecting a highly modular and scalable structure.

On the other hand, a messaging `Broker` is set up with the store directory to "/home/intino/broker," with a primary port for JMS OpenWire and a secondary port for MQTT. This broker also includes basic user authentication, facilitating secure management of data transmission. The directory, users, and ports can also be overridden using external sources of configuration such as configuration files or program parameters. This aspect is addressed in the next subsection.

The "monitoring" `Namespace` defines the data structure that the system will manage, with resources such as logs and messages that include statuses and incidents. Each type of message and resource has specific attributes that allow for detailed classification and efficient retrieval, such as identifiers, severity levels, and detailed descriptions. These attributes are essential for the filtering and subsequent analysis of the collected data.

### Utilizing the Intino Plugin

By using the Intino plugin, users can enhance their DSL experience. This plugin allows viewing the associated metamodel and offers code assistance features such as code completion and real-time error analysis, significantly easing the configuration process and helping to avoid common mistakes. More information about the Intino plugin can be found [here](https://intino.systems/wiki/index.php).

<div style="text-align: center;">
  <img src="File:Ness-artifact.png" alt="Configuration of datahub artifact" style="width: 50%;">
</div>

In the figure, the configuration of an artifact designed to be used as a datahub is displayed. This configuration utilizes the Ness DSL, specifically its latest version. When setting up the artifact to use this DSL, the IDE will require the addition of a set of parameters that are recognized by the Datahub platform. These must be provided in the format "name"="value" on the run configuration. The parameters are:
* `home` (required): Specifies the directory where DataHub will store its files.
* `broker_port` (required): Specifies the port for the JMS OpenWire protocol.
* `broker_secondary_port` (required): Specifies the port for the MQTT protocol.
* `backup_directory` (optional): The directory where periodic backups of the datalake changes can be made.
* **SSL Encryption args** (optional): Additional parameters related to SSL encryption for the protocols can be provided. Concretely: `keystore_path`, `keystore_password`, `truststore_path`, and `truststore_password`.

To launch the datahub, it is essential to configure it using the DSL and also to create a Main class that not only starts the application but also links the parameters with the platform. This Main class expands the configuration options, offering the ability to tailor the application to our specific needs. Through coding, we can customize important aspects of the configuration, such as user management, directory structuring, and certificate security. If you need a practical example of how to implement this, you can refer to a model project available [here](https://github.com/intino/example.datahub).