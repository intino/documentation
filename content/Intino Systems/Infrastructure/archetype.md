---
title: "Archetype"
date: 2024-07-18T15:00:00Z
draft: false
---
The Archetype language is designed to provide a unified and consistent way to describe the organization of files and directories in a file system, thus facilitating data integration and management across various applications. This document provides a detailed description of the syntax and functionalities of the Archetype language, illustrated with a practical example.

## Main Features

Archetype is designed with a range of functionalities that support access to the filesystem. The key features include:

* **Unification:** Archetype allows for the uniform description of directory and file structures across multiple applications.
* **Flexibility:** It offers customized methods for constructing file paths based on dynamic parameters, increasing flexibility in data handling.
* **Maintainability:** Facilitates updating and maintaining directory structures without modifying the source code of the applications that access these data.
* **Scalability:** Assists applications in efficiently scaling by consistently managing data structures across different environments or platforms.

## DSL

The syntax of Archetype is based on the definition of blocks representing directories and subdirectories, as well as specific files within those directories. Below is a detailed example that illustrates the main features of the language.
```

 TARGETS:{bussiness-unit, business-unit2}
 
 + datavault in "datavault"
   + logs
    - of(server, app, name) in "{server}/{app}/{name}.log"
 
 + repository in "documents"
   + employees
     - getPhoto(employee) in "{employee}"
     - getSignature(employee) in "signatures/{employee}.png"
   + workorders
     - getStoreDirectory(id) in "{id}"
   + workreports
     - workReports(date as timetag: day) in "{date}" with ".pdf"
     - workReport(date as timetag: day, employee, instant) in "{date}/{employee}.{instant}.pdf"
 * configuration in "configuracion"
   + business-unit
     - dbConfiguration in "db.conf"
   + business-unit2
     - mobileAppVersions in "mobileAppVersions.txt"
``` 

* **datavault** Directory: This main directory has a logs directory where it can access log files, allowing dynamic specification of the server, application, and log file name, structured in a way that facilitates the organization and retrieval of specific logs.

* **datalake** Directory: Represents massive data storage, structured without additional subdirectories.

* **repository** Directory: This item, stored in the "documents" directory, is used for storing documents and includes several subdirectories such as employees, workorders, workreports, and uploads, each with specific methods for accessing related documents or reports. The workReports method takes a date parameter, labeled as a timetag with a format of day. It retrieves all files in a directory named according to this date parameter, and these files must include a .pdf pattern in their names.

* **configuration** Directory: This item, stored in the "configuracion" directory, is used to store the configuration of each target. Each child directory defined with '\*' must match a target specified at the beginning of the archetype. Within these directories, exclusive files and directories for the specific target will be defined.

The definition of the archetype is completed with the inclusion of a plugin in the module artifact to generate accessory libraries for each target. The code to include in the artifact to incorporate the archetype-plugin would be:

```
  IntinoPlugin("io.intino.archetype", "archetype-plugin", "2.0.0", Export)
```

To generate the archetype, it will need to be exported using [Intino Factory](Legio), thereby distributing the various targets of the archetype to the artifactory described in the artifact. Alternatively, it can be installed by using the shift modifier when executing the action.