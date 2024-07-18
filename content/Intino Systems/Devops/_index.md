---
title: "Devops"
date: 2024-07-18T15:00:00Z
draft: false
weight: 3
---

DevOps practices streamline the lifecycle of software creation, from development to deployment. A critical aspect of this process in an [Intino System](../Intino_Systems) is the management of software artifacts—components or resources used during the development process. Intino employs a sophisticated approach using [Maven](https://maven.apache.org/) and [Artifactory](https://jfrog.com/artifactory/) to enhance these practices, ensuring efficient package management and distribution.

Artifact management involves handling the various binaries and libraries produced during software builds. It includes storing, versioning, and retrieving build artifacts, which are essential for continuous integration and deployment pipelines. Effective artifact management helps in maintaining consistency and efficiency in software deployment and updates.

It is not limited to application code or service configurations; it extends to managing the entire technological stack. Whether it’s handling the underlying [infrastructure](../infrastructure) or the specific needs of different [business units](../Business-Units), or even docker images, these tools provide a robust mechanism for versioning, storing, and retrieving all necessary artifacts. This integrated approach ensures that both the infrastructure and each business unit can consistently deploy and operate with the most up-to-date and stable versions of software, thereby enhancing reliability and facilitating continuous improvement across all facets of the organization.

## Development Lifecycle

The development lifecycle model leverages modern CI/CD practices and tools to streamline the software development process, ensuring quick integration, testing, and deployment of new code. This approach enhances the efficiency and reliability of delivering software updates to end-users. It integrates various tools and services to ensure smooth and efficient software development and deployment:

<div style="text-align: center;">
  <img src="../../images/Lifecycle.png" alt="Lifecycle" style="width: 50%;">
</div>

### Binary Repository

This is where build artifacts and binaries are stored. It serves as a safe and accessible storage location for all versions of build files, such as libraries and Docker images. It could be [Artifactory](https://jfrog.com/artifactory) or [Dockerhub](https://hub.docker.com/) among others.

### Code Repository

This is a version control system that manages and tracks changes to the source code. It allows multiple developers to collaborate effectively by keeping a history of changes and enabling code merging. It could be [GitHub](https://github.com/) or [GitLab](https://gitlab.com/) among others.

### CI/CD Tools

These are automation tools used for Continuous Integration (CI) and Continuous Delivery (CD). They automate the processes of code integration, testing, packaging, delivery, and deployment, ensuring consistency and reliability. It could be [Ansible](https://www.ansible.com/) or [Jenkins](https://www.jenkins.io/) among others.

### Intino Workflow Phases

* **Import:** The process begins by importing the source code from the Binary Repository. This step ensures that the development environment has the latest version of the libraries or frameworks.
* **Build & Test:** Once the code is imported, it is built and tested. Automated tests are run to verify the code’s functionality and detect any bugs early in the development process. This phase is crucial for maintaining code quality.
* **Package:** After successful building and testing, the code is packaged into a deployable format, such as a binary or Docker image.
* **Delivery:** The packaged code is then delivered to the deployment environment. This step is automated to ensure that the delivery process is consistent and error-free. This package is stored in the Binary Repository.
* **Deployment:** Finally, the delivered package is deployed to the production environment, making it available to end-users.

### CI / CD

Using tools like Ansible and Jenkins, new code changes are frequently integrated into the main codebase. This process includes building and testing the changes to ensure that the software remains in a deployable state. This process, also automated by Ansible and Jenkins, ensures that the packaged code is continuously delivered to the deployment environment. This allows for quick and reliable releases.

## Project Model

In Intino, [Legio DSL](Plugin#Legio) orchestrates the build process, dependency management, and the deployment of artifacts. It allows the definition of a project model to manage project builds, dependencies, plugins, and other configurations. An integral part of this process involves utilizing Maven coordinates to uniquely identify every artifact, which are then managed within an internal Artifactory.

### Maven Coordinates

Maven coordinates are a set of properties used to uniquely identify a project or a module in a repository. They are critical for artifact deployment and dependency management. The coordinates include:

* **Group ID:** The identifier for the organization or group that created the project, often resembling a reversed domain name.
* **Artifact ID:** The specific name of the project, which is usually the project's base name.
* **Version:** The version of the artifact under which it is released or being developed.
* **Scope:** The scope of a dependency defines its visibility and lifespan in different phases of the project lifecycle. The most common scopes are:
  * **compile:** Default, available in all phases.
  * **provided:** Needed at compile time but not included in the final package.
  * **runtime:** Needed at runtime but not at compile time.
  * **test:** Only available during testing.
  * **system:** Similar to provided but requires a specific path in the file system.

These scopes ensure that dependencies are available only when needed, optimizing the build and execution process.

### Integration with Artifactory

In Intino, all artifacts created during the software development process are managed through an internal Artifactory, a repository manager that serves as a centralized hub for handling these artifacts. Each artifact, identified by its unique Maven coordinates, is stored in the internal Artifactory. This centralization provides a single source of truth for all artifacts and their respective versions, enhancing control over distribution and reducing redundancy.

**Efficient Retrieval:** Developers can retrieve any version of an artifact using its Maven coordinates, simplifying the process of managing dependencies and ensuring that builds are reproducible and consistent across different development environments.

**Secure and Scalable:** The internal Artifactory supports secure access controls, ensuring that artifacts are accessible only to authorized users and systems. It also scales to accommodate the growth in artifact volume as the project expands.

**Benefits in DevOps Practices:** Artifactory acts as a repository manager that fully integrates with Maven, providing a robust solution for managing binary repositories. As a key component in Intino’s DevOps infrastructure.