---
title: "Box pattern"
date: 2024-07-18T15:26:15Z
draft: false
weight: 3
---
The **Box Pattern** is a software design pattern that focuses on centralizing and managing adapters within a hexagonal architecture. This pattern introduces a Box class that acts as a hub, interconnecting adapters and coordinating their interactions through itself. Additionally, it relies on application arguments to create a configuration object, BoxConfiguration, which serves as the entry point for configuration data for the adapters. The Box class also contains the application's model and includes methods to control the start and stop lifecycle of the adapters.

## Key Components

1. **Box Class**: This abstract class defines the central hub for the pattern. It provides the core functionality for managing the lifecycle of the adapters and interconnecting them. Each project implements its own version of this class.
2. **BoxConfiguration**: This class is responsible for handling the configuration of the adapters. It receives application arguments and sets up the necessary configuration data for the adapters.
3. **Adapters**: These are the components that connect to various external systems or services. The Box pattern manages these adapters through the Box class, ensuring they are started and stopped in a controlled manner.

## Box Class Definition

Here is the Box class definition:

```java
public abstract class Box {

    protected Box owner;

    public abstract void beforeStart();

    public abstract Box start();

    public abstract void afterStart();

    public abstract void beforeStop();

    public abstract void stop();

    public abstract void afterStop();

    public abstract Box put(Object object);

    public abstract BoxConfiguration configuration();

    public abstract void startServices();

    public abstract void stopServices();
}
```

### Lifecycle Management

The Box class provides several abstract methods to manage the lifecycle of the adapters:
* **beforeStart()**: Called before starting the adapters.
* **start()**: Starts the adapters and returns the Box instance.
* **afterStart()**: Called after starting the adapters.
* **beforeStop()**: Called before stopping the adapters.
* **stop()**: Stops the adapters.
* **afterStop()**: Called after stopping the adapters.

### Configuration Management

The `configuration()` method returns an instance of BoxConfiguration, which contains the configuration data necessary for the adapters.

### Adapter Management

The `put(Object object)` method allows adding objects (such as adapters) to the Box. The `startServices()` and `stopServices()` methods are used to control the starting and stopping of the adapters.

### Owner Relationship

The `owner` field and `owner()` method establish a hierarchical relationship between Box instances, allowing nested or dependent Box instances.

By centralizing the management of adapters in the Box, the application gains a structured and consistent way to handle configuration, startup, and shutdown processes, leading to better maintainability and scalability.

Both the Box and its configuration are generated automatically when using the **Konos language**. All adapters described in Konos are internally registered within the Box, and their lifecycle is managed by the Box. This automation simplifies the process of integrating and managing adapters, ensuring that they are configured, started, and stopped consistently and reliably as part of the application's overall lifecycle.