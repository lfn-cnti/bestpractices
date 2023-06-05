<!-- Created from CBPP template v1.0
     Major: changes when we add or remove sections or demands for information
     Minor: changes when we alter formatting without changing content requirements
     Keep the first line of this comment in your best practice,
     to help us track formatting updates -->

# CBPP-0004: Do not run containers with the privilege flag

- [Release Signoff Checklist](#release-signoff-checklist)
- [Summary](#summary)
- [Motivation](#motivation)
  - [Goals](#goals)
  - [Non-Goals](#non-goals)
- [Proposal](#proposal)
- [Workload Context](#workload-context)
  - [User Stories](#user-stories)
  - [Notes/Constraints/Caveats](#notesconstraintscaveats)
  - [References](#references)
  - [Alternatives](#alternatives)
- [Test Plan](#testing-objectives)
- [Scoring](#scoring)
- [Implementation History](#implementation-history)

## **Release Signoff Checklist**

Items marked with (R) are required for the proposed best practice to be included in a release.

- [ ] (R) CBPP approvers have approved the CBPP status as `implementable`
- [ ] (R) CBPP summary, motivation and best practice details are appropriately documented
- [ ] (R) Test plan is in place, giving consideration to CNF Test Suite input
- [ ] (R) Scoring has been determined
- [ ]   "Implementation History" section is up-to-date
- [ ]    Supporting documentation—e.g., additional design documents, links to mailing list discussions/SIG meetings, relevant PRs/issues, release notes

## **Summary**

Privileged containers can potentially get unrestricted access to host's resources. Therefore, if the privileged container is compromised, an attacker would have full access to the server. Containers should be run with the privilege flag set to false to securely restrict the access to the host resources.

## **Motivation**

This best practice benefits the CNF consumer / operator (e.g. a Communication Service Provider [CSP]) by limiting the exposure to the host system and other workloads available to a compromised or misbehaving CNF.

Validating that a CNF is following this best practice can be verified by CNF operators as an acceptance test.

SE-Linux based environments will require dropping root privileges. Example: OpenShift

### **Goals**

- Improve the security and behaviour of applications.
- Add to the defense in depth strategy against external compromises.
- Avoid compromised applications from causing more damage.
- Restricting the Pod access to the host’s resources (e.g. memory, CPU, network)
- Limiting access to other workloads running on the host

### **Non-Goals**

- Denying access to the host entirely
- Fine-grained access control to the host

## **Proposal**

When creating the Pod definition, the privilege flag policy should be set to false. This tells the container runtime to disable privilege mode for the containers on that Pod when it runs.

The privileged policy is defined by an absence of restrictions. This type of policy is typically aimed at system- and infrastructure- level workloads managed by privileged, trusted users.

Privileged containers are defined as any container where the container uid 0 is mapped to the host's uid 0. A process within a privileged container can get unrestricted host access. Without proper settings, a process can also gain privileges from its parent. Application containers should not be allowed to execute in privileged mode and privilege escalation should not be allowed.

Running a pod in a privileged mode means that the pod can access the host's resources and kernel capabilities.

<https://kubernetes.io/docs/concepts/workloads/pods/#privileged-mode-for-containers>

For example, a potential issue can be an [RCE](https://www.netsparker.com/blog/web-security/remote-code-evaluation-execution/) (Remote Code Execution) Vulnerability in one of your third-party dependencies or even in your own code. Using this vulnerability, an attacker might gain access to the running container, and assuming the pod is privileged, the attacker can continue directly to the host.

In a virtual machine or a bare-metal server, you avoid running your applications with the root user for a simple reason: if the application is compromised, an attacker would have full access to the server. For the same reason, avoid using privileged containers. A privileged container is a container that has access to all the devices of the host machine, bypassing almost all the security features of containers.

## **Workload Context**

All non-system pod types should implement this best practice.

### **User Stories**

#### Supply chain attack user stories

[Supply chain attacks](../doc/user-stories/supply-chain-attacks.md) are a risk at any point in the supply chain. ‘Defence in depth’ says that we should (a) defend against supply chain attacks but also (b) add mitigations in the case that supply chain attacks happen.

Examples include

- [A CNF downloads compromised updates](../doc/user-stories/supply-chain-attacks.md#a-cnf-downloads-compromised-updates)
- [A CNF succumbs to code injection](../doc/user-stories/supply-chain-attacks.md#a-cnf-succumbs-to-code-injection)
- [A CNF succumbs to malicious instructions](../doc/user-stories/supply-chain-attacks.md#a-cnf-succumbs-to-malicious-instructions)
- [A CNF has a security-compromising bug](../doc/user-stories/supply-chain-attacks.md#a-cnf-has-a-security-compromising-bug)

In all of these examples, the CNFs using a non-root user for their container processes, have limited the scope of damage a compromised process may cause.

See main [defense in depth for supply chain attacks](../doc/user-stories/supply-chain-attacks.md) document for more information.

### **Notes/Constraints/Caveats**

If your deployment workload resource definition (eg. helm) pulls in external upstream container images during runtime, those images may have Pod definitions with the privilege flag policy set to true for one or more their Pods. It is recommended that the CNF developer audits and cleans up any upstream images to respect this rule ensuring the privilege flag is set to false when following this best practice.

Some Pods may need privileges to provide required functionality.  For example kube-proxy or the Envoy side-car.

It is the responsibility of the CNF developer to communicate the privileges needed by their CNF.

The CNF developer needs to be aware of how privileges of a container can be escalated, see <https://kubernetes.io/docs/tasks/configure-pod-container/security-context/>.

### **References**

- ["Do not run containers with the privilege flag" as a best practice · Issue #67 · cncf/cnf-wg](https://github.com/cncf/cnf-wg/issues/67)
- [Applying principle of least privilege to CNFs · Discussion #28 · cncf/cnf-wg](https://github.com/cncf/cnf-wg/discussions/28)
- [Configure a Security Context for a Pod or Container | Kubernetes](https://kubernetes.io/docs/tasks/configure-pod-container/security-context/)
- [Kubernetes No New Privileges design proposal: design-proposals-archive/no-new-privs.md](https://github.com/kubernetes/design-proposals-archive/blob/main/auth/no-new-privs.md)
- There are 2 [CIS Docker Benchmark](https://www.cisecurity.org/benchmark/docker/) (a reference document that used to establish a secure configuration baseline for Docker containers) guidelines that cover privileged pods:
  - Guideline 5.4: Ensure that privileged containers are not used (recommends not to use the privileged mode when running containers)
  - Guideline 5.22: Ensure that docker exec commands are not used with the privileged option (recommends not to use the privileged mode when using `docker exec`).
- Kubernetes Security: [Chapter 1. Approaching Kubernetes Security](https://www.oreilly.com/library/view/kubernetes-security/9781492039075/ch01.html)
- X-Factor CNFs: [XIII. Do not require privileges - X-Factor CNFs](https://x.cnf.dev/process-containers/)
- [Hack my mis-configured Kubernetes - privileged pods](https://www.cncf.io/blog/2020/10/16/hack-my-mis-configured-kubernetes-privileged-pods/) Synk CNCF blog post (2010)
- [10 Kubernetes Best Practices You Can Easily Apply to Your Clusters](https://nirmata.com/2020/02/19/10-kubernetes-best-practices-you-can-easily-apply-to-your-clusters/) (2020)
- [11 Ways (Not) to Get Hacked | Kubernetes](https://kubernetes.io/blog/2018/07/18/11-ways-not-to-get-hacked/#2-enable-rbac-with-least-privilege-disable-abac-and-monitor-logs) (2018)
- Google Cloud: [Best practices for operating containers](https://cloud.google.com/architecture/best-practices-for-operating-containers#avoid_privileged_containers) | Cloud Architecture Center
- tag-security/cloud-native-security-lexicon.md at main · cncf/tag-security · GitHub
- [Pod Security Standards | Kubernetes](https://kubernetes.io/docs/concepts/security/pod-security-standards/#privileged)
- [Apply Pod Security Standards at the Cluster Level | Kubernetes](https://kubernetes.io/docs/tutorials/security/cluster-level-pss/)
- Red Hat: [Podman in containers; specifically with regard to Kubernetes.](https://www.redhat.com/sysadmin/podman-inside-kubernetes) (2021)

### **Alternatives**

Role-based access control provides fine-grained policy management for user access to resources, such as access to namespaces.

## **Testing Objectives**

An application which follows this best practice will not have any privileged containers running.
This CBPP will be tested by the CNF Test Suite.

## **Scoring**

This best practice results in a pass/fail.

Static or runtime analysis (all items checked for a pass) - CNF developers (testing before delivery) or CNF operators (testing what is delivered):

The Pod definition or any running container manifest has the privilege flag policy set to false.

## **Implementation History**

First version: Feb 2023
