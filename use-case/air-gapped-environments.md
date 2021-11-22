# User stories: Employing Air Gapped Environments

Environments hosting critical infrastructure often deny access to the public internet, even via a proxy. This is done for several reasons as part of a defense in depth strategy, such as controlling the artifacts that come into the environment, controlling builds at the source, and ensuring malicious code is not able to call back to remote destinations. Beyond the security implications of air gapping an environment and utilizing private registries, upstream repositiory management becomes a centralized task that all internal stakeholders can take advantage of.

Note: Air gapped environments are not solely an issue for service providers/network operators. Other heavily regulated environments, such as US DoD networks, seeking to employ CNFs would be beholden to these constraints.

## A CNF utilizes a cloud based licensing model

A CNF running on a K8s cluster is downloaded from a centralized registry. Upon instantiation, the CNF validates that it has the required license tied to the desired functionality. If the license is valid, the functionality instantiates. If a valid license is not available, the desired behavior is often that the next available license in a pool is requested, or a new order is generated in real time.

In this case, if the operator does not allow for the CNF to access the remote licensing server, this method breaks down. If the licensing server is pulled into the locally hosted environments but requires licenses to be purchased in advance, then the dynamic nature of the CNF might be hindered due to a lack of available licenses in the pool. 

The goal for licensing best practices should be to find ways to allow operators to safely and securely deploy CNFs on-demand in air gapped environments. This means that CNF vendors and operators find a way to monetize CNFs that support cloud-based deployments in an environment that may break certain cloud native assumptions.

## An operator employs [GitOps](https://github.com/cncf/cnf-wg/blob/main/use-case/0001-UC-lifecycle-of-infrastructure-where-CNF-is-running.md) methodologies with defense in depth

In an air gapped environment, unique supply chain considerations arise. As discussed in [user-story supply-chain-attacks](https://github.com/cncf/cnf-wg/blob/main/user-stories/supply-chain-attacks.md), securing ones supply chain is paramount to a defense in depth strategy. In an operator's air gapped environment, this supply chain almost always enforces a centralized choke point for pulling, distributing and versioning artifacts. 

In this case, the operator would seek to ensure that artifacts are signed and deemed "trusted" before being released to the rest of the interal actors. Trust could be established in multiple ways, such as internal pipelines that pull untrusted artifacts and run vulnerability scans and automated testing or via an established software supply chain with a trusted vendor. All declarations supporting an operator's GitOps style approach would strictly build from these privately hosted repositories in fully air gapped development, stage, and production environments. Testing would include validation that a CNF is fully deployable and maintainable with zero reach to the internet.

## A vendor employs SaaS based services
A vendor provides a SaaS based solution hosted in a third-party cloud environment. This service could be related to licensing, streaming telemetry, or automated fault detection. In this instance, the provider and operator must come to an agreement as to how these services will be accessed. This could be accomplished via a VPN, by providing operators the ability to host these software solutions within their environments, or convincing operators that fully air gapped approaches are not feasible in the cloud native world.
