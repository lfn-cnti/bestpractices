# UC-NNNN: Short descriptive title of your use case (TEMPLATE)

## Glossary

> Provide definitions for technical terms and acronyms.

## Involved processes

- [ ] Development
- [x] Deployment
- [x] System integration
- [x] Network integration
- [ ] Lifecycle management
- [ ] Operations

## Involved actors / personas

CNF Vendor
CNF DevOps
Cloud Native Platform DevOps (CNPD)
CSP Network Ops

## Involved system entities

Data Center Network
Wide Area Network
Cloud Native Platform
CNF
CICD

## Situation

CNF DevOps teams in CSP are responsible for the introduction and lifecycle of the network functions under their management. They are typically not developing those network functions, but rely on deployment and integration of products of CNF vendors. As the transformation of network functions from PNF/VNFs to CNFs is gaining momentum, CNF DevOps teams and their selected CNF vendors are getting relatively new task - onboarding of CNF onto the generic Kubernetes based platform of CSP. It is relatively new task because in case of PNF entire function was delivered pre-integrated by vendor and in VNF case the prevalent practice was that VNF vendor brings its own NFVi blueprint or requires a 3rd party blueprint that is certified by that vendor for that CNF.

In CNF case the assumption is that the platform is already there, that it is in its core Kubernetes based without special forks as well as that different components needed by CNF could be installed via Kubernetes API.

This creates the situation in which CNF and CSP platform, both of which have their requirements and pre-conditions, meet each other as such for the first time. The process of getting the CNF deployed on the platform in aforementioned scenario is colloquially called "onboarding". In this process CNF vendor, CNF DevOps and CNPD work together to reach common gloal of having production grade deployment of CNF supported with appropriate SLA which factors-in the fact that CNF runs on CSP platform.  

## Expected behaviour

CNF vendor expects that CSP platform and environment (e.g. Network) are fulfilling certain requirements and preconditions for CNF to be able to achieve production grade deployment. These requirements are different from CNF to CNF.

CNPD expects that all requirements are well documented with and provided in such form before onboarding starts. The docummentation shall enable CNPD team to verify readiness and prepare the platform (e.g. configure necessary kernel modules, SR-IOV interfaces and similar). In practically all deployments that are meant for production environment the deployment artifacts are stored in private on-prem artifacts and registries. Therefore CNPD expects that CNF vendor provides its artefacts in a form that is typical for cloud native applications (Helm charts, containers, yaml manifests) which could be easily replicated to CSP's on-prem environment (e.g. CNF vendor's registry accessible via Internet from CSPs caching registry).

CNF DevOps team expects to deploy and configure the CNF application on their own, preferably directly via automation pipelines and in interaction and cooperation with CNPD and CSP Network teams. For that they expect to receive well documented installation procedures, references for typical continuous deployment realisations with that particular or similar CNFs as well as comprehensive deployment troubleshooting guide. As already mentioned in (UC0001)[0001-UC-lifecycle-of-infrastructure-where-CNF-is-running.md], CNF DevOps team also expects to get suite of tests from CNF vendor. Tests could then be deployed in continuous testing pipeline to automatically verify that CNF is running properly (production grade) on the platform and that the deployment qualifies for SLA.

The starting point of onboarding shall be extension of platform with any requirements and dependencies that are coming from CNF. When all conditions on the platform level are met, the deployment of CNF shall proceed.

## Challenges and limitations with Kube-native approach

Most of the CNFs today, especially complex ones, are packaged in such way that only trained professional service teams of the CNF vendor can reasonably deploy them. The documentation and manuals that come with those CNFs are giving same impression. The onboarding today usually requires intensive interation between CNF vendor, CNF DevOps and CNPD teams and lots of trial/error tuning and manual adaptations on both platform and CNF side.

The CNFs are also regularly packaged to be suitable for opinionated installers that are typically part of vendor's own platform offering or particular platform blueprint. The onboarding on CSP's own platform in such cases frequently involves sort of reverse engineering of CNF vendor's installer to come to basic cloud native artefacts and derive requirements from installer's code with the help of vendor's engineers.

Finally, the CNFs are frequently delivered as Helm charts. However, these Helm charts often do not cover all dependencies that enables reconciling the deployments in proper way. They also install CRDs which are not managed well by Helm.

This situation is in most cases not blocking the onboarding, but is making it laborious and not repeatable.

### Established practices to overcome challenges and limitations

The practices already exist outside of CNF world, but are not very well followed by CNF vendors. Some of the practices are here:

- [The Chart Best Practices Guide](https://helm.sh/docs/chart_best_practices/)
- [GitOps](https://www.gitops.tech/)
- [Kubernetes production best practices](https://learnk8s.io/production-best-practices)

### What needs to be done differently in order to overcome challenges and limitations

CNF vendors need to start preparing CNFs for shipping as regular cloud software that is well docummented and that can be deployed and configured by CNF DevOps team. Following established best practices for cloud native software distribution and deployment would improve the situation significantly.
