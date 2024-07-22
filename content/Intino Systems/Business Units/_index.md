---
title: "Business Units"
date: 2024-07-18T15:26:15Z
draft: false
weight: 2
---

Business units are the custom components of an [Intino System](../). A business unit refers to a segment of a company that operates within its own individual guidelines but is still tied to the larger organizational framework. It is a discrete operational entity within a corporation, with its own mission, resources, and objectives, and is often aligned around a specific product line, market segment, or geography. Business units are typically responsible for their own strategic planning, product development, marketing, and profit and loss management.

In the context of distributed systems like Intino, each business unit plays a crucial role in the overall architecture of the system. These units are akin to micro-organizations within the larger ecosystem, each equipped to handle specific domain-specific functions. Each business unit requires an [infrastructure](../infrastructure) in place to support its operational needs effectively. Both, the business units and the infrastructure, are deployed using Intino’s [DevOps](../devops) tools, which facilitate rapid deployment, scalability, and operational efficiency. These tools ensure that the infrastructure aligns perfectly with the specific requirements of each business unit, allowing them to focus on their strategic planning, product development, and market initiatives.

In Intino, business units are designed as modular components of the distributed system, each potentially utilizing hexagonal architecture to ensure flexibility and maintainability of their software solutions. They interact with centralized components like the Datahub through well-defined interfaces, adhering to a publisher-subscriber model. This model ensures that updates and data are efficiently propagated throughout the organization, maintaining system coherence and data integrity.

## Application Architecture

In Intino, business units are developed using the hexagonal architecture, a design pattern that emphasizes the separation of a system's core logic from external elements it interacts with, such as databases, user interfaces, or external services. This architecture, also known as the ports and adapters pattern, allows changes to these external elements without affecting the core logic.

<div style="text-align: center;">
  <img src="../../images/hexagonal.png" alt="Hexagonal Architecture" style="width: 50%;">
</div>


The hexagonal architecture organizes the application into a central model, surrounded by a layer of ports and adapters using the [Box pattern](Box_Pattern). The core contains the business logic, while the ports define points of interaction with external elements through interfaces. Adapters implement these interfaces to translate between the external technologies and the business logic. This architecture is supported in Intino by:

* [**Magritte**](magritte): Primarily focused on the business model layer, managing the core processes, rules, and operations at the heart of the application. It embodies the hexagonal architecture's principle of isolating business logic from external influences. This isolation ensures that business rules remain independent of external interfaces or data access methods.
* [**Konos**](konos): Responsible for managing the adapters, which are the implementations that connect the application's ports to external services such as web interfaces, databases, or external APIs. This role involves overseeing the flow of data between the business core and these services, handling tasks such as data translation, formatting, and adherence to communication protocols. Additionally, Konos may support broader infrastructure needs, including security measures, data storage solutions, and possibly messaging and event-handling systems, all crucial for enabling efficient scaling across various environments.

Intino automates code generation by transforming models created with [Proteo DSL](Proteo_DSL) and [Konos DSL](Konos_DSL) using their respective frameworks, Magritte and Konos. Proteo DSL is utilized to define the business model, enabling developers to specify the structure and relationships of data within the business domain concisely. By providing a clear model definition, Proteo ensures consistent application of all business rules and data structures across the application. On the other hand, Konos DSL is employed to define adapters that interact with the model. Konos facilitates the seamless integration of these components, ensuring adherence to the predefined business model and rules.

## Publisher & Subscriber

Integrating the hexagonal architecture with Intino’s [Datahub](../infrastructure/ness) requires the use of a publisher-subscriber model. This model is crucial for ensuring that changes within the business units are efficiently propagated across the system.

Business units within Intino can act as both publishers and subscribers, depending on the operational context. As publishers, they generate events. Conversely, as subscribers, they receive updates or data from other parts of the system, ensuring that each unit has access to the latest information necessary for its operations.

To support this dynamic interaction, the Datahub provides specialized accessors for both publishing and subscribing to the events that reach the Datahub. These events can be processed either in batch mode or in real time, following the principles of [lambda architecture](https://en.wikipedia.org/wiki/Lambda_architecture).

* **Batch Layer:** Processes large volumes of stored data in batches, creating comprehensive views that are ideal for in-depth analytics and reporting.
* **Speed Layer:** Handles real-time data processing as data arrives, ensuring immediate analysis and decision-making capabilities.

This mechanism ensures that all parts of the system remain synchronized and that data integrity is maintained across different units. To facilitate this interaction, the Datahub provides specific accessors for publishing and subscribing to events. These accessors enable business units to communicate changes in real-time or through scheduled batches, adapting to the needs of the system.

## Datamarts

[Datamarts](https://en.wikipedia.org/wiki/Data_mart) are a vital component in the architecture of data-driven businesses, acting as subsets of a company's data warehouse, tailored to meet the specific needs of individual business units or departments. In systems like Intino, where a centralized Datahub collects and organizes vast amounts of organizational data, datamarts provide a more focused view of this data, making it more accessible and useful for specific business purposes.

A datamart is essentially a specialized store of data that is derived from a larger data warehouse or datahub. It is designed to reflect the unique needs and priorities of a specific business unit, focusing on particular subjects or areas of business operations. This tailored approach not only simplifies the data management within individual departments but also enhances decision-making by providing data that is more relevant to the specific contexts of those departments.

In the context of Intino, each business unit can have its own datamarts which act as projections of the data collected and managed in the central Datahub. These datamarts are customized to support the specific data needs and analytical functions of each unit, providing streamlined access to data that is most relevant to their operational goals. For instance, a marketing business unit might have a datamart that focuses exclusively on customer interaction data and campaign results, while a finance department’s datamart might concentrate on financial transactions and budget allocations.

## Interfaces

Interfaces are crucial for the operability and user experience in any software system. In Intino, Konos enables business units to effectively design and implement these interfaces:

* **[Graphical User Interfaces (GUI)](https://en.wikipedia.org/wiki/Graphical_user_interface):** Konos helps design GUIs that are intuitive and user-friendly, providing visual interactions with the software. This includes layout design, navigation, and interactive elements that make the application accessible to end-users.
* **[Command-Line Interfaces (CLI)](https://en.wikipedia.org/wiki/Command-line_interface):** For more technical users or specific administrative tasks, CLIs designed with Konos offer a direct way to interact with the system through command prompts. This allows users to execute tasks, query data, or configure systems directly through a console.
* **[Application Programming Interfaces (API)](https://en.wikipedia.org/wiki/API):** APIs are essential for creating scalable, interoperable, and flexible systems. Konos assists in defining these APIs, ensuring that they are robust, secure, and compliant with current standards, facilitating easy integration with other systems or third-party services.

## Business Processes

[Business Process Management (BPM)](https://en.wikipedia.org/wiki/Business_process_management) is another critical aspect where Konos provides significant value. BPM involves designing, executing, monitoring, and optimizing business processes. With Konos, business units can define and automate these processes, integrating them seamlessly into the system’s architecture:

Konos allows for the detailed modeling of business processes, defining steps, decision points, and required actions clearly. This modeling helps in visualizing the entire process flow and making necessary adjustments to improve efficiency and effectiveness. By defining executable process descriptions, Konos enables the automation of routine tasks, reducing the need for manual intervention and minimizing human errors.
Integration: Konos ensures that these BPM tools integrate smoothly with other system components, such as data sources and interfaces, enhancing the overall system functionality and user experience.

There are scenarios where human intervention is essential, often referred to as manual tasks. These tasks require user input or decision-making that cannot be automated. To efficiently manage these manual tasks, Intino utilizes its infrastructure layer known as [Monet](Monet). Manual tasks within a BPM framework are operations that require human actions to complete. These can include decision-making, physical activities, or inputs that software alone cannot execute. Examples might be approving requests, performing physical checks, or entering unique data that varies by case. The necessity for manual tasks arises from the complexity and variability of business processes, where not every decision or action can be predicted and automated.
