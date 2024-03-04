# Glossary

## Specification

### Community Definitions

**Cloud Native**: TBD

**Cloud Native Network Function (CNF)**: A network function that is a [cloud native application](https://glossary.cncf.io/cloud-native-apps/), i.e. developed using cloud native principles.

**Kubernetes**: [Kubernetes.io](https://kubernetes.io/) is a portable, extensible, open-source platform for managing workloads and services, that facilitates both declarative configuration and automation. It has a large, rapidly growing ecosystem. Kubernetes services, support, and tools are widely available.

**Network function**: An application that provides networking functionality. Network functions may be components of network services (a "functional block" according to ETSI) or themselves network services.

**Network service**: TBD

**Physical Network Function (PNF)**: A network function distinguished by its encapsulation and isolation in discrete hardware. Internally it may use various technologies, including virtualization, containerization, cloud platforms, etc.

**Virtualized Network Function (VNF)**: A network function deployed entirely or primarily using virtualization technologies, which comprise both hardware and software features and include CPU, RAM, and GPU support, as well as bus features such as SR-IOV. Virtualization technologies are available in hypervised virtual machines as well as containers (see: Containerized network function). Note that a VNF is not necessarily a cloudified network function. Indeed, the history of NFV—the effort to virtualize network functions—predates the move to cloud platforms.

### CNTI Specific Definitions

**Containerized network function**: A network function deployed entirely or primarily as one or more containers. Should not be referred to by the "CNF" acronym in order to avoid confusion with Cloud Native Network Function (CNF). Note that this definition specifies the runtime technology only, not the platform. Thus a containerized network function might not target Kubernetes nor indeed any cloud platform. Also note that some containerization technologies include virtualization features (see also: VNF).

**Kube-Native**: TBD

**Additional Definitions?**

## References

* CNCF Git [CNCF Cloud Native Definition](https://github.com/cncf/toc/blob/main/DEFINITION.md)
* Cloud Native Principles [Cloud Native Principles Preamble](https://github.com/cloud-native-principles/cloud-native-principles/blob/master/cloud-native-networking-preamble.md)
* Kubernetes.io [What is Kubernetes?](https://kubernetes.io/docs/concepts/overview/what-is-kubernetes/)
