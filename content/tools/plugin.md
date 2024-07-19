---
title: "Plugin"
date: 2024-07-18T15:00:00Z
draft: false
---
The Intino plugin integrates several tools to facilitate automated software development and deployment. This document provides a detailed overview of Intino's features, including its core components, supported DSLs, and lifecycle management capabilities.

## Main Features

Intino is designed with a range of functionalities. The key features include:

### Tara Languages Family Support

Intino provides comprehensive support for the Tara languages family. This includes all DSMLs derived from the Tara mother language. The unified environment developed for these languages offers essential features such as syntax highlighting, early error detection, and code auto-completion. Additionally, it supports version control integration, code generation, and automated refactoring, which collectively enhance the efficiency and accuracy of coding within the Tara language ecosystem.

### Archetype and Itrules Integration

Support for [Archetype](../infrastructure/archetype) and [Itrules](../sle/ItRules). The Archetype language is designed to provide a unified and consistent way to describe the organization of files and directories in a file system, thus facilitating data integration and management across various applications. Itrules is an engine for code generation based on templates, allowing for efficient and standardized development practices.

### Application Lifecycle Management with Legio

Legio DSL provides powerful tools for managing the entire lifecycle of applications. It supports dependency management, project structuring, and deployment operations, making it a comprehensive solution for application development and deployment.

## Legio

Legio is a specialized DSL of Tara's family designed specifically to define and manage the project model within [Intino](../Intino_Systems). It serves as the backbone for defining the [lifecycle](../intino-systems/devops#development-lifecycle). This DSL enables developers to specify and control various elements such as dependencies, build configurations, deployment, and other project-related parameters.

### Key Functions of Legio

* **Project Definition:** Legio DSL allows developers to clearly outline the structure of a project. This includes defining modules, components, and their interactions, ensuring that all parts of the project are well organized and systematically managed.
* **Dependency Management:** Through Legio DSL, projects can efficiently handle dependencies, specifying what libraries or external resources are needed, and managing their versions to ensure compatibility and stability across the project’s lifecycle.
* **Build Configuration:** It provides a framework for setting up build processes, including the specification of build steps, required scripts, and other automation processes necessary for compiling and preparing the software for deployment.
* **Environment Specification:** Legio DSL allows for the precise definition of environment settings, ensuring that the software behaves consistently in different development, testing, or production environments.

Legio is integrated with the [Intino plugin](.) in IntelliJ IDEA, so when Intino projects are created, it automatically incorporates the project and corresponding module configuration files. The creation of this code is guided by code suggestions and features live error checking for both syntax and semantics. This ensures that developers can write code more efficiently and with fewer errors, as they receive real-time guidance and corrections during the coding process.

### project.legio

An example of a project configuration is as follows:

<div style="text-align: center;">
  <img src="../images/legio-project.png" alt="Aspects" style="width: 80%;">
</div>

This project configuration defines a project named "foo-bar" with a detailed description. It includes a developer, John Doe, providing contact and organizational information. The project specifies multiple repositories, each with different release and snapshot URLs for artifact storage. Update policies for repositories can also be defined, such as daily updates for the "iceblue" and "lorem-maven" repositories. Maven central repository is automatically included.

Additionally, the project configuration outlines several server environments (Development, Production, Pre-production) with specific server names, ensuring that deployments are managed across different stages of the development lifecycle.

### artifact.legio

In Legio, an artifact is declared for each module of a project, ensuring that each module generates a software artifact. The concept of an artifact is central to the organization and management of the project’s components. Below is a detailed description of the artifact concept and its key elements.

The declaration of an Artifact in Legio serves as the primary definition for a module. It includes several attributes such as groupId, which identifies the group or organization responsible for the artifact, the version which specifies the version of the artifact, ensuring precise version control and management, and description that provides a brief description of the artifact, which is optional and can be left empty. The name of the artifact is necessary and it will be the artifactId in the Maven ecosystem.

**License:** Legio allows for the specification of a license for each artifact, ensuring compliance with legal and open-source requirements. The type of license can be selected from options such as GPL, BSD, or LGPL.

**DSL:** The artifact can have associated DSLs (Domain-Specific Languages), which include:
* **Name and Version:** These attributes specify the name and version of the DSL.
* **Builder:** This optional concept within DSL defines the build process, including attributes like groupId, artifactId, version, and generationPackage. It also allows the exclusion of certain code bases or language generations through specific tags.
* **Output DSL:** Defines the output DSL, including its name and any version check mechanisms for runtime and builder libraries, ensuring compatibility and consistency across versions.

**Imports:** Imports play a critical role in managing dependencies for an artifact. They include:
* **Java Dependencies:** This defines the external libraries required by the artifact, managing their versions, and scope (Compile, Runtime, Test or Provided).
* **Web Imports:** Specific to web components, this defines web directories, resolutions, and web artifacts needed by the project.

**Code and Plugin**

The Code concept allows for the specification of target packages for the generated code, while the IntinoPlugin defines various phases such as Export, PostCompilation, PrePackage, PostPackage, and PostDistribution.

The complete metamodel of Legio can be found [here](https://github.com/intino/plugin/blob/master/legio/src/io/intino/legio/model/Main.tara).

## Application Lifecycle

TODO