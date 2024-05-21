# Best Practices for CNF Developers

## Table of Contents

* [1.0 Compatibility, Installability & Upgradability](#10-compatibility-installability--upgradability)
* [2.0 Configuration](#20-configuration)
* [3.0 Microservices](#30-microservices)
* [4.0 State](#40-state)
* [5.0 Security](#50-security)
* [6.0 Observability and Diagnostics](#60-observability-and-diagnostics)
* [7.0 Reliability, Resilience & Availability](#70-reliability-resilience--availability)

### 1.0 Compatibility, Installability & Upgradability

Best practices affecting the basic management of CNF software - the acceptance of CNFs from a development team, the installation onto the network, the creation of instances in clouds within the network, version management of running software and the compatibility of CNFs on many cloud platforms and with other CNFs.

### 2.0 Configuration

Working with running CNFs: common patterns for setting and changing the behaviour of network functions.

### 3.0 Microservices

The best way to use microservice-based design patterns to deliver CNF functionality.

#### CBPP-0005: A CNF's containers should handle a single concern and service (normally mapping to one process type) per container

**Description:**
A CNF with multiple concerns should split services (or process types) for each of its concerns into separate containers. Service dependencies should be handled between containers through well-defined interfaces.

Pod specs for the CNF should provide scaling and monitoring information for each service running in different containers.

**Reference:** [CBPP-0005](cbpps/0005-single-concern-per-container.md)

### 4.0 State

Management of short-lived and long lived state, including state associated with network flows, configuration data, subscriber activity data and other data according to the varying requirements of resiliency, rate of change, access rate and persistence.

### 5.0 Security

How to ensure that components are protected against security issues, including security advisories on software components, defence against attacks, and defence in depth.

#### CBPP-0002: Container should execute process(es) as non-root user

**Description:**
Containers have a list of their own users independent of the host system, one of which is UID 0, the root user. Containers should run processes as a user other than root which makes it easier to run the container images securely.

**Reference:** [CBPP-0002](cbpps/0002-no-root-in-containers.md)

#### CBPP-0004: Do not run containers with the privilege flag

**Description:**

Privileged containers can potentially get unrestricted access to host's resources. Therefore, if the privileged container is compromised, an attacker would have full access to the server. Containers should be run with the privilege flag set to false to securely restrict the access to the host resources.

**Reference:** [CBPP-0004](cbpps/0004-do-not-run-containers-with-privilege-flag.md)

### 6.0 Observability and Diagnostics

How to get critical data about when things are going wrong and how to determine what must be done to put them right. The detection and correction may be through the actions of an operator or via an automated system. Using logs and metrics from all components in the system to narrow down the area where a problem exists, and to drill down into that area to determine a root cause and a fix.

### 7.0 Reliability, Resilience & Availability

How to ensure CNFs are resilient to failures that are inevitable in cloud environments.
