---
title: "Infrastructure"
date: 2024-07-18T15:00:00Z
draft: false
weight: 1
---
The infrastructure is a fundamental component of an [Intino System](../Intino_Systems). It refers to the services needed for the operation of a system. In the context of distributed systems, infrastructure is pivotal as it supports the technological framework and operational processes. It is essentially the backbone that connects, supports, and enables the flow of information and services across the entire system. The infrastructure provides support to [business units](../Business-Units), enabling them to operate efficiently and effectively.

<div style="text-align: center;">
  <img src="../../images/architecture.png" alt="Architecture" style="width: 50%;">
</div>

All services, both infrastructure and business units, are constructed and deployed using Intino's [DevOps](devops) tools, which streamline the development, testing, and deployment processes. This integration ensures that the infrastructure is always aligned with the business objectives, promoting agility and innovation across the organization. By leveraging these DevOps practices, Intino ensures that its infrastructure not only meets the current demands but is also scalable and adaptable to future needs, supporting the continuous evolution of its business units.

## Core Services

The infrastructure is composed of several services that together create a secure, and efficient environment for managing data and processes. Each component is designed to not only meet the current needs of the system but also to anticipate future demands, ensuring that Intino remains at the forefront of technology innovation.

### Datahub

The Datahub service, supported by [Ness framework](Ness), is a central repository designed to manage data efficiently. This component is crucial for the collection, organization, and access provision to the data accumulated across the system. It supports efficient data ingestion, transformation, and distribution, ensuring that data flows seamlessly across the system, making it accessible where and when it is needed.

### Federation

The Federation service, supported by [Amidas framework](Amidas), provides user registration and management. It plays a critical role in governing user identity by providing unified access control across different business units. This framework ensures data security and adheres to privacy standards, thus maintaining a secure environment for data handling and access within the system.

### Analytics

The Analytics service, supported by [Sumus framework](Sumus), empowers users to analyze and visualize data effectively, transforming raw data into actionable insights. By doing so, Sumus aids in driving better decision-making and enhancing operational efficiency across the organization.

### Taskhub

Taskhub, supported by [Monet framework](Monet), is envisioned as the central platform where manual, human-centric tasks are managed and integrated into the automated business processes. The primary purpose of Taskhub is to facilitate human interactions that are necessary for completing certain business processes that cannot be fully automated. This involves tasks that require human judgment, decision-making, or physical actions. Examples might include reviewing and approving complex documents, handling exceptions in automated workflows, or performing physical verifications that software cannot execute.