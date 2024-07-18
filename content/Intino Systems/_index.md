---
title: "Intino Systems"
date: 2024-07-18T15:00:00Z
draft: false
weight: 3
---

## The ultimate goal of Intino

The ultimate goal of Intino is to develop a distributed system following [big data](https://en.wikipedia.org/wiki/Big_data) and [service-oriented architecture](https://en.wikipedia.org/wiki/Service-oriented_architecture) (SOA) principles. Every Intino software system should begin with a clear definition of its structure. By doing it, organizations can lay the groundwork for a successful project. This approach ensures that all subsequent development aligns with the desired architecture, leading to a cohesive and maintainable solution.

This development [lifecycle](Devops) is enabled by the [Intino plugin](plugin) available, providing a seamless integration with the [IntelliJ IDEA](https://www.jetbrains.com/es-es/idea), which enhances the developer experience by offering tools and features tailored to the Intino framework.

The system is structured as a collection of services that communicate through well-defined interfaces. These services are designed to be loosely coupled yet functionally cohesive, allowing for greater flexibility and scalability. In line with this architectural strategy, Intino provides a series of frameworks that serve as foundational tools for extending functionality across its distributed system architecture. These frameworks are inherently extensible, offering a base structure and a suite of functionalities that specific services can customize and build upon according to their unique requirements. This approach not only facilitates the modular development of services but also enhances the ability of the system to integrate and adapt to changing business needs, thereby embodying the core characteristics of SOA.

From a big data perspective, Intino follows the [lambda architecture](https://en.wikipedia.org/wiki/Lambda_architecture) and [event-driven architectures](https://en.wikipedia.org/wiki/Event-driven_architecture). The lambda architecture enables the processing of both real-time and batch data by combining batch processing and stream processing. Event sourcing principles focus on capturing all changes to application state as a sequence of events, which can then be replayed to reconstruct past states or analyze data trends over time. By integrating these principles into its distributed system architecture, Intino aims to effectively handle large volumes of data, support real-time processing, and maintain a comprehensive record of application state changes for analysis and insight generation.

## Infrastructure Services

The essential services that conform the infrastructure of every distributed system include:

* **Federation:** supported by [Amidas framework](amidas), this service provides the infrastructure and tools necessary for implementing robust federation services, including user registration, authentication, and authorization processes.
* **Analytics:** supported by [Sumus framework](sumus), this service is specifically designed to handle the complexities of business intelligence services.
* **Taskhub:** supported by the [Monet framework](monet), this service addresses the need for handling manual tasks within automated workflows.
* **Datahub:** supported by [Ness framework](Ness), this service is a central component that acts as the backbone for data management within the distributed system. The Datahub is supported by a [message broker](https://en.wikipedia.org/wiki/Message_broker) that manages events, efficiently handling the ingestion, processing, and routing of events across the system. Additionally, it incorporates a [datalake](https://en.wikipedia.org/wiki/Data_lake) where these events are stored. This datalake serves as a repository for structured and unstructured data.


<div style="text-align: center;">
  <img src="../images/architecture.png" alt="Architecture" style="width: 50%;">
</div>


## Business Units

A [business unit](../Business_Units) is an operational service that is responsible for specific functions. It serves as a self-contained division focused on delivering particular functions to meet the needs of the business. Essentially, a business unit acts as a smaller, specialized unit within a company, often with its own leadership, resources, and strategic objectives.

The development of [business units](../Business_Units) follows the [Hexagonal architecture](https://en.wikipedia.org/wiki/Hexagonal_architecture_(software)), a software design pattern aimed at organizing application logic while maintaining a clear separation between core functionalities and external interfaces. This architecture is composed of:

* Business Model, supported by [Magritte Framework](magritte), managing the core processes, rules, and operations at the heart of the application. It embodies the hexagonal architecture's principle of isolating business logic from external usages. This isolation ensures that business rules remain independent of external interfaces or data access methods. Magritte likely defines what are known as ports—interfaces through which the core business logic interacts. These ports are designed to communicate with external services or applications via adapters, which are managed by the Konos framework.

* [Box](Box_Pattern), supported by [Konos Framework](konos), is responsible for managing the adapters, which are the implementations that connect the application's ports to external services such as web interfaces, databases, or external APIs. This role involves overseeing the flow of data between the business core and these services, handling tasks such as data translation, formatting, and adherence to communication protocols. Additionally, Konos may support broader infrastructure needs, including security measures, data storage solutions, and possibly messaging and event-handling systems, all crucial for enabling efficient scaling across various environments.

## Archetype

Additionally, every distributed system should include the definition of the [archetype](archetype), containing the structure of directories and files within a software environment. It serves as a model for organizing data, resources, and configurations, providing a standardized definition of the system. Its utility lies in streamlining development, maintenance, and scalability efforts by offering clear guidelines for organizing files, facilitating collaboration among team members, simplifying troubleshooting and updates, ensuring consistency across deployments, and enabling the system to adapt and evolve over time to meet changing requirements. Essentially, it's a practical tool for efficiently managing complex software systems.

## DevOps

At Intino, the management of service lifecycles is seamlessly integrated into the [DevOps](Devops) vision, ensuring a smooth transition from development to deployment and beyond. DevOps practices, which emphasize collaboration, automation, and continuous improvement, are fundamental to how Intino handles the lifecycle of its services.

Central to this approach is the management of software artifacts—the building blocks of the services. Intino leverages robust tools like [Maven](https://maven.apache.org/) and [Artifactory](https://jfrog.com/artifactory/) to optimize artifact management, enabling efficient package handling and distribution throughout the development lifecycle.

Artifact management includes the storage, versioning, and retrieval of binaries and libraries generated during software builds. These artifacts play a fundamental role in continuous integration and deployment pipelines, facilitating consistency and agility in software delivery. However, Intino's approach extends beyond just application code and configurations. It includes the entire technological stack, including infrastructure components and the diverse needs of different business units. Whether it's managing [docker](https://www.docker.com/) images or orchestrating complex service dependencies, Intino's tools provide a comprehensive solution for versioning, storing, and retrieving all essential artifacts.

This integrated approach ensures that both the infrastructure and each business unit can consistently deploy and operate with the latest and most stable versions of software. By promoting reliability, scalability, and continuous improvement across the organization, Intino's DevOps-driven lifecycle management strategy underscores its commitment to delivering high-quality services efficiently.

## DSLs

A significant aspect of Intino's vision is its reliance on Domain-Specific Languages (DSLs). A DSL is a programming language customized to a specific application domain. Unlike general-purpose programming languages, which are designed to be versatile and applicable to various tasks, DSLs focus on solving particular problems or tasks.

Intino provides a suite of specialized DSLs designed to streamline different facets of its technology framework, enhancing both development and operational efficiency.

* **[Ness DSL](Ness#dsl):** Ness focuses on creating the structure for the datalake, which is crucial for supporting big data analytics and real-time data processing. It also defines the taxonomy of events within the system, ensuring that events are categorized and managed effectively for easy retrieval and analysis.
* **[Proteo DSL](Proteo_dsl):** Proteo is used for defining the business model, providing clear specifications of data structures and relationships critical for consistent application across platforms.
* **[Konos DSL](Konos_dsl):** Konos facilitates the integration of business logic with external services by defining layers that handle interactions, such as APIs, user interfaces, and business processes.
* **[Legio DSL](Plugin#legio):** Legio orchestrates the project model, handling dependencies and lifecycle akin to a project object model.