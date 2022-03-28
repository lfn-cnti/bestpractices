# User stories: Employing Air Gapped Environments

Environments hosting critical infrastructure often deny access to the public internet, even via a proxy. This is done for several reasons such as controlling the artifacts that come into an environment, controlling builds at the source, and ensuring malicious code is not able to call back to remote destinations. Beyond the security implications of air gapping an environment and utilizing private registries, upstream repository management becomes a centralized task that all internal stakeholders can take advantage of. Internal developers and operations teams can rely on their SREs to ensure that the images, packages, etc... they require are available and secure.

Note: Air gapped environments are not a challenge solely for service providers/network operators. Other operators of heavily regulated environments, such as US DoD networks, seeking to employ CNFs would be beholden to these constraints.

## A CNF utilizes a cloud based licensing model

A CNF running on a K8s cluster is downloaded from a centralized repository. Upon instantiation, the CNF validates that it has the required license tied to a suite of desired functionality. If the license is valid, the functionality is enabled. If a valid license is not available, the desired behavior is often that the next available license in a pool is requested, or a new order is generated in real time.

In this case, if the operator does not allow for a CNF to access a remote licensing server, this method breaks down. Additionally, if the licensing server is hosted locally in the environment but requires licenses be purchased in advance, then the desired behavior of dynamically deploying CNFs might be hindered due to a lack of available licenses in the pool.

The goal for licensing best practices should be to find ways that allow operators to safely and securely deploy CNFs on-demand in air gapped environments. This means that CNF vendors and operators must find a way to monetize CNFs that support cloud-based deployments in an environment that may break certain cloud native assumptions.

## An operator employs [GitOps](https://github.com/cncf/cnf-wg/blob/main/use-case/0001-UC-lifecycle-of-infrastructure-where-CNF-is-running.md) methodologies with defense in depth

In an air gapped environment, unique supply chain considerations arise. As discussed in [user-story supply-chain-attacks](https://github.com/cncf/cnf-wg/blob/main/user-stories/supply-chain-attacks.md), securing one's supply chain is paramount to a defense in depth strategy. In an operator's air gapped environment, this supply chain almost always enforces a centralized choke point for pulling, distributing, and versioning artifacts.

In this case, the operator would seek to ensure that artifacts are signed and deemed "trusted" before being released to the rest of the internal actors. Trust could be established in multiple ways, such as internal pipelines that pull untrusted artifacts and run vulnerability scans and automated testing or via an established software supply chain with a trusted vendor. All declarations supporting an operator's GitOps style approach would strictly build from these privately hosted repositories in fully air gapped development, stage, and production environments. Testing would include validation that a CNF is fully deployable and maintainable with zero reach to the internet.

## A vendor employs SaaS based services

A vendor provides a SaaS based solution hosted in a third-party cloud environment. This service could be related to licensing, streaming telemetry, or automated fault detection. In this instance, the provider and operator must come to an agreement as to how these services will be accessed.

This could be accomplished via a VPN, by providing operators the ability to host these software solutions within their environments, or convincing operators that fully air gapped approaches are not feasible in the cloud native world. Best practices that explore how to consume SaaS based offers in air gapped environments must be explored in the future.

## Glossary

- Air gapped environment: A physically and logically isolated environment that disallows direct network access/connectivity. These environments are created to protect infrastructure from bad actors either attempting to gain access to the environment remotely, or for malicious software to reach outside of the isolated environment. Given these constraints, standard cloud software consumption models where users and software pull, clone, or download required resources from public repositories are blocked. All new software bound for this environment must first be introduced through the operator’s secure source control mechanisms. 
- Source: For the context of this user story, references to an air gapped environment’s "source", with regards to controlling builds, software ingest, and other topics, is specifically referring to a private source repository accessible through private network connectivity. Specifically, the intention is that this entity acts as a single source of truth for all operators in this environment. Any software, tooling, or configuration files leveraged in this environment must be made accessible here. **Note:** The source control tooling can be federated, and this definition does not imply that there is a requirement for a single entity hosting all images and source code. It is a logical construct that acts as a control mechanism to strictly enforce what is made available in an air gapped environment.
- Upstream: For the context of this user story, upstream refers to any repository sitting "North" of the private repository. Air gapped environments, if built to be truly isolated, are prevented from pulling directly from upstream repositories. To access upstream software in an air-gapped environment, software should be validated and then hosted in a private repository. Mechanisms, such as VPNs and proxies can be leveraged as part of a secure source control strategy as well, but implies implicit trust to the additional “sources” you are pulling from.
