---
title: "Amidas"
date: 2024-07-18T15:00:00Z
draft: false
---
**Latest version**: [https://github.com/intino/amidas/releases/latest](https://github.com/intino/amidas/releases/latest).

Amidas is an [infrastructure](infrastructure) framework designed to implement the federation service. A Federation is a collaborative environment through which disparate systems, services, and identities can interact and collaborate while maintaining their autonomy and security boundaries. With advanced identification and authentication capabilities, as well as the ability to integrate various third-party services, the platform offers a complete solution for managing security and communication in the organizational environment.

## Main Features

Amidas is designed with a range of functionalities that support the federation in an organization. The key features include:

### Identification and Authentication

The platform provides a robust identification and authentication system to ensure user and data security.
Different authentication methods can be implemented, such as passwords, OAuth, two-factor authentication (2FA), and certificate authentication, according to the organization's needs.

### Third-Party Connectors

The platform offers the flexibility to integrate third-party services to obtain relevant information from the organization.
Connectors for systems such as LDAP (Lightweight Directory Access Protocol) or Microsoft Azure can be added, facilitating secure access to user data and organization resources.

### Communication Management

The platform facilitates effective communication among users by integrating with popular messaging applications such as Rocket.Chat or MS Teams.
Users can collaborate, share information, and coordinate activities efficiently, improving productivity and collaboration within the organization.
With these features, the organizational federation platform provides a robust solution for managing security and communication within the organization.

## Step-by-Step Configuration Example

By using the Intino plugin, users can enhance the configuration of the platform. The plugin facilitates the import of Amidas dependencies along with the necessary connectors for the specific use case. An example of usage can be found at [https://github.com/intino/example.amidas.git](https://github.com/intino/example.amidas.git).

Here are the startup parameters for the application, which must be provided in the format "name"="value" in the run configuration:

* `home`: Directory for storing the application's own information necessary for its operation.
* `port`: Port for starting the user interface and API.
* `title`: Title of the organization. It will appear in the login interface and user profiles.
* `subtitle`: Slogan of the organization.
* `logo`: Logo of the application.
* `background`: Background image used for the login page. It is an absolute path to a file.
* `background_mode`: UI theme. The allowed values are light or dark.
* `authentication_secret`: Secret key used in OAuth authentication process.
* `photo_directory` (optional): Directory where user photos are stored. If not specified, a directory within the one specified in the "home" parameter is used.
* `apps_directory_filename` (optional): Defines the catalog of applications declared in an organization. It is useful to create an application directory view where applications are accessible by clicking on any of those.
* `apps_tokens_filename` (optional): File describing the connection tokens with the organization's applications.
* `apps_directory_federation_name` (optional): Defines the name for the federation in the organization that is used for the application directory.

The connectors are configured using a properties file. Each connector requires specific properties, which are as follows:

### Microsoft Azure

* `federation.connectors.microsoft.azure.tenantId`: The ID of the Azure tenant.
* `federation.connectors.microsoft.azure.clientId`: The client ID used for authentication with Azure.
* `federation.connectors.microsoft.azure.clientSecret`: The client secret used for authentication with Azure.

### Microsoft Teams

* `federation.connectors.microsoft.teams.store.directory`: The directory where Teams store information.
* `federation.connectors.microsoft.teams.app.url`: The URL of the Teams application.
* `federation.connectors.microsoft.teams.app.cliPath`: The CLI (Command Line Interface) path for the Teams application.
* `federation.connectors.microsoft.teams.tenantId`: The ID of the Teams tenant.
* `federation.connectors.microsoft.teams.clientId`: The client ID used for authentication with Teams.
* `federation.connectors.microsoft.teams.clientSecret`: The client secret used for authentication with Teams.
* `federation.connectors.microsoft.teams.botName`: The name of the bot associated with Teams.
* `federation.port`: The port used for federation.

### LDAP

* `federation.connectors.ldap.servers`: The LDAP servers to connect to.
* `federation.connectors.ldap.admin.name`: The username of the LDAP admin.
* `federation.connectors.ldap.admin.password`: The password of the LDAP admin.
* `federation.connectors.ldap.dc`: The domain component for LDAP.
* `federation.connectors.ldap.filters.user`: Filters for LDAP users.

### Rocket.Chat

* `federation.connectors.rocketChat.url`: The URL of RocketChat.
* `federation.connectors.rocketChat.app.url`: The URL of the RocketChat application.
* `federation.connectors.rocketChat.app.cliPath`: The CLI path for the RocketChat application.
* `federation.connectors.rocketChat.bot.user`: The username of the bot associated with RocketChat.
* `federation.connectors.rocketChat.bot.password`: The password of the bot associated with RocketChat.