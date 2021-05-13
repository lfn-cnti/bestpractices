# Glossary

## Specification


### Community Definitions

**Cloud Native**: TBD

**Cloud Native Network Function (CNF)**: A network function that is a [cloud native application](https://github.com/cncf/glossary/blob/main/definitions/cloud_native_apps.md), i.e. developed using cloud native principles. 

**Kubernetes**: [Kubernetes.io](https://kubernetes.io/) is a portable, extensible, open-source platform for managing workloads and services, that facilitates both declarative configuration and automation. It has a large, rapidly growing ecosystem. Kubernetes services, support, and tools are widely available.

**Network function**: A functional block within a network infrastructure. Network functions may be components of network services.

**Network service**: TBD

**Physical Network Function (PNF)**: A network function distinguished by its encapsulation and isolation in discrete hardware. Internally it may use various technologies, including virtualization, containerization, cloud platforms, etc.

**Virtualized Network Function (VNF)**: A network function deployed entirely or primarily using virtualization technologies, which comprise both hardware and software features and include CPU, RAM, and GPU support, as well as bus features such as SR-IOV. Virtualization technologies are available in hypervised virtual machines as well as containers (see: Containerized network function). Note that a VNF is not necessarily a cloudified network function. Indeed, the history of NFV—the effort to virtualize network functions—predates the move to cloud platforms.


### CNF WG Specific Definitions

**Cloudified network function**: A network function that designed to be deployed on cloud platforms, including Kubernetes (see: Kubernetes Network Function). A cloudified network function can use virtualization features (in which case it would also be considered to be a VNF) as well as containers (in which case it is also be considered to be a containerized network function). A cloudified network function is not necessarily a Cloud Native Network Function (CNF). To be classified as a CNF it must adhere to cloud native design principles.

**Containerized network function**: A network function deployed entirely or primarily as one or more containers. Should not be referred to by the "CNF" acronym in order to avoid confusion with Cloud Native Network Function (CNF). Note that a containerized network function is not necessarily a Kubernetes Network Function (KNF) as it is possible to use containers in other and simpler platforms. Thus, it is also not necessarily a cloudified network function. Also note that some containerization technologies include virtualization features (see also: VNF).

**Kubernetes Network Function (KNF)**: A cloudified network function deployed on Kubernetes. Note that a KNF is not necessarily a containerized network function as there are ways to employ virtualization features in containers running in Kubernetes, and indeed to run full virtual machines.

**Kube-Native**: TBD

**Additional Definitions?**


## References

* CNCF Git [CNCF Cloud Native Definition](https://github.com/cncf/toc/blob/main/DEFINITION.md)
* Cloud Native Principles [Cloud Native Principles Preamble](https://github.com/cloud-native-principles/cloud-native-principles/blob/master/cloud-native-networking-preamble.md)
* Kubernetes.io [What is Kubernetes?](https://kubernetes.io/docs/concepts/overview/what-is-kubernetes/)
