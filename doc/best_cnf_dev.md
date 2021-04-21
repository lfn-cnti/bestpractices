# Best Practices for CNF Developers

## Table of Contents

* [1.0 Installation and Upgrade](#1.0-installation-and-upgrade)
* [2.0 Configuration and Lifecycle](#2.0-configuration-and-lifecycle)
* [3.0 Hardware support](#3.0-hardware-support)
* [4.0 Microservices](#4.0-microservices)
* [5.0 Compatibility](#5.0-compatibility)
* [6.0 State](#6.0-state)
* [7.0 Security](#7.0-security)
* [8.0 Scaling](#8.0-scaling)
* [9.0 Observability and Diagnostics](#9.0-observability-and-diagnostics)

## 1.0 Installation and Upgrade

Best practices affecting the basic management of CNF software - the acceptance of CNFs from a development team, the installation onto the network, the creation of instances in clouds within the network, and the version management of running software.

## 2.0 Configuration and Lifecycle

Working with running CNFs: common patterns for setting and changing the behaviour of network functions.

### BEST_CNF_DEV_1001: Application is configured via standard way

**Description**: Some Description here

<!-- This is an example and therefore the link is broken. -->
<!-- markdown-link-check-disable-next-line -->
**Link to CBPP**: [CBPP-0001](../cbpps/xyz.md)

### BEST_CNF_DEV_1002: Application announces its own membership of the tier to its peers

**Description**: Some Description here

<!-- This is an example and therefore the link is broken. -->
<!-- markdown-link-check-disable-next-line -->
**Link to CBPP**: [CBPP-0002](../cbpps/xyz.md)

## 3.0 Hardware support

How to co-ordinate hardware to best enable CNF efficiency.  Low-level access to hardware such as NICs; access to acceleration technologies; efficient management of standard resources, including manipulation of lower-level system components such as CPU cores, CPU cache and memory.

## 4.0 Microservices

The best way to use microservice-based design patterns to deliver CNF functionality.

## 5.0 Compatibility

How to ensure CNFs work on as many platforms, in as many places, as possible; how to ensure that cloud platforms enable as many CNFs as possible; how to make CNFs work with each other and common elements in the operational stack.

## 6.0 State

Management of short-lived and long lived state, including state associated with network flows, configuration data, subscriber activity data and other data according to the varying requirements of resiliency, rate of change, access rate and persistence.

## 7.0 Security

How to ensure that components are protected against security issues, including security advisories on software components, defence against attacks, and defence in depth.

## 8.0 Scaling

Running of CNFs at a variety of different scales to manage different traffic requirements and subscriber counts.  Changing the scale of CNFs.

## 9.0 Observability and Diagnostics

How to get critical data about when things are going wrong and how to determine what must be done to put them right.  The detection and correction may be through the actions of an operator or via an automated system.  Using logs and metrics from all components in the system to narrow down the area where a problem exists, and to drill down into that area to determine a root cause and a fix.
