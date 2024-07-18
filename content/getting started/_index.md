---
title: "Getting Started"
weight: 1
date: 2024-07-18T15:00:00Z
draft: false
---
Intino's architectural vision is brought to life using [IntelliJ IDEA](https://www.jetbrains.com/idea/) as the integrated development environment (IDE) and Java as the primary programming language. This setup allows developers to work within a powerful and flexible environment. Intino acts as a software factory, automating developer workflows and streamlining the system's development process through a custom [IntelliJ plugin](plugin). This plugin automates various tasks, such as project configuration, module management, and deployment strategies.

By leveraging the plugin's features, developers can quickly set up, build, and maintain a modular distributed system aligned with the architectural vision. This approach reduces the complexity of manual configuration, providing a seamless workflow that integrates coding, testing, and deployment into a unified process. Thus, Intino empowers teams to focus on crafting business logic and domain-specific functionality while the automated tools handle much of the infrastructure work.

## Setup the environment
### Install IntelliJ
Download and install the IntelliJ IDEA IDE, ensuring it's the most recent version to access the latest features and enhancements.

### Set Up Java Development Kit (JDK)
Install the appropriate version of the Java Development Kit (JDK) required for your project and configure IntelliJ to recognize it as the primary development environment.

### Install the [Intino Plugin](plugin)
Access IntelliJ's plugin marketplace and search for the Intino plugin. Install and enable it to gain access to features that automate the development workflow, such as project setup and module management.

## Create a New Project
Start by creating a new project in IntelliJ, which will represent the entire distributed system. Ensure that the project structure is flexible enough to accommodate multiple modules.

## Define the [Infrastructure](../infrastructure)
Each module will correspond to a specific service. Configure each module to contain the necessary code, resources, and configurations specific to that service.

### [Archetype](../infrastructure/archetype) Module
Make sure each module follows the project's archetype, ensuring consistent organization of code, resources, and configurations. This will help keep the entire system modular, maintainable, and scalable.

### [Datahub](../infrastructure/ness) Module
Include all code and configurations related to data ingestion, transformation, and distribution. This module will interact with external data sources and handle the centralized data processing pipeline.

### [Federation](../infrastructure/amidas) Module
This module represents the federation layer for managing user registration and identity. It includes the configurations for secure user access and compliance with data security standards.

### [Analytics](../infrastructure/sumus) Module
Incorporate tools and logic needed for data analysis and visualization, enabling users to transform raw data into insights.

## Define [Business Units](../Business-Units)
Each business unit can be a service, with its own logic and specific dependencies. These modules should align with the business functions they represent.

## Plan your [Devops](../devops)
### Configure Dependencies
Use the project's configuration language to specify dependencies, ensuring that each module has access to the required libraries and services.

### Define Deployment Strategies
In each module's build configuration, define how the resulting artifacts will be published and specify the deployment environments or servers. This ensures a consistent, reliable deployment process.