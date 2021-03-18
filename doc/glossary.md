
Glossary
============================

Specification
-------------

### Community Definitions

**Cloud-Native** - Cloud native technologies empower organizations to build and run scalable applications in modern, dynamic environments such as public, private, and hybrid clouds. Containers, service meshes, microservices, immutable infrastructure, and declarative APIs exemplify this approach.

These techniques enable loosely coupled systems that are resilient, manageable, and observable. Combined with robust automation, they allow engineers to make high-impact changes frequently and predictably with minimal toil.

The Cloud Native Computing Foundation seeks to drive adoption of this paradigm by fostering and sustaining an ecosystem of open source, vendor-neutral projects. We democratize state-of-the-art patterns to make these innovations accessible for everyone.

**Cloud-Native Network Function** - A CNF is network functionality delivered in software via cloud native development and delivery practices. This functionality lives within the layers of the OSI Model [9], which is used to define a network's stack. The lower layers (layers 1 and in some cases, layer 2) are provisioned for the higher layers (2-7) to provide transport. These higher layers in this instance act as applications that act upon a network payload (frames, packets datagrams etc). A physical layer 1 networking device should be "flashed" with a complete replacement of its artifacts for updates. The configuration for physical layer 1 is done with an atomic application of a versioned configuration file, which replaces the configuration on the device at once. Virtual Layer 1 (and some layer 2) is managed via templated images and bootstrapping. In contrast, layers 2 through 7 are managed by higher-level orchestration or an established control plane (an orchestrator pushing configuration versus a network protocol modifying a route table).

**Kubernetes** - Kubernetes is a portable, extensible, open-source platform for managing containerized workloads and services, that facilitates both declarative configuration and automation. It has a large, rapidly growing ecosystem. Kubernetes services, support, and tools are widely available.

### CNF-WG Specific Definitions

**Kube-Native** - TBD

**Additional Definitions?**

References
----------

* CNCF Git [CNCF Cloud Native Definition](https://github.com/cncf/toc/blob/main/DEFINITION.md)
* Cloud Native Principles [Cloud Native Principles Preamble](https://github.com/cloud-native-principles/cloud-native-principles/blob/master/cloud-native-networking-preamble.md)
* Kubernetes.io [What is Kubernetes?](https://kubernetes.io/docs/concepts/overview/what-is-kubernetes/)
