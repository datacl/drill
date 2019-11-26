---
title: "Embedded Mode Prerequisites"
date: 2018-04-16 23:12:45 UTC
parent: "Installing Drill in Embedded Mode"
---
To use Drill on a single node, install Drill in embedded mode. Installing Drill in embedded mode installs Drill locally on your machine. Embedded mode is a quick way to install and try Drill without having to perform any configuration tasks. A ZooKeeper installation is not required. Installing Drill in embedded mode configures the local Drillbit service to start automatically when you launch the Drill shell. You can install Drill in embedded mode on a machine running Linux, Mac OS X, or Windows.

Before you install Drill, ensure that the machine meets the following prerequisites:

* Linux, Mac OS X, and Windows: Oracle or OpenJDK 8  
* Windows only:  
  * A JAVA_HOME environment variable that points to the JDK installation  
  * A PATH environment variable that includes a pointer to the JDK installation  
  * A utility for unzipping a tar.gz file 

Follow installation instructions in this documentation for your particular operating system.

提示：独立运行模式不支持用户认证，需用户认证请使用集群模式运行。
