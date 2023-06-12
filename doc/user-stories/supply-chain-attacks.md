# User stories: Defense in Depth against Supply Chain Attacks

Supply chain attacks are a risk at any point in the supply chain.  In a supply chain attack, a malicious actor sneaks code into the application that serves their nefarious purposes.  It can happen for many reasons: for instance, because they managed to modify the registry, they managed to modify the image before it was placed in the registry, or they managed to get illicit code into an open source project that is built into the container.

'Defence in depth' says that we should (a) defend against supply chain attacks but also (b) add mitigations in the case that supply chain attacks happen - that is, we should not assume that a single line of defence will hold.

## A CNF downloads compromised updates

A CNF running on a K8s cluster is downloaded from a centralized registry.  Updates also come from this registry.  The operator installs new images in the centralised repository as they receive them from the CNF developer.

In this case, if the operator ensures that processes in the container will be run as a normal container user without extra rights, the malicious code will have a very limited ability to do dangerous things.  It will be harder for it to try to escalate its privileges, it has no rights outside of the container, it cannot change files within the container that could cause more damage (such as root-owned settings files in /etc).

Thus: limiting the privilege of container processes makes the system safer to use.

## A CNF succumbs to code injection

As above, a CNF runs malicious code, in this case introduced into the process through a code injection attack on its internal or external interfaces by a bad actor within the operator's organisation or by anyone on the network, respectively.  In this instance, limiting the power wielded by processes in the container again prevents the attack from going further.

## A CNF succumbs to malicious instructions

As an example: the configuration of a CNF might allow the operator to determine paths where a log file is written.  If this path is set to a protected file, then the container root user has the rights necessary to overwrite that file.  This could be exploited to change configuration and settings files within the container image and subvert it.

A CNF such as a programmable forwarder might receive rules updates from a central system.  Maliciously crafted rules might cause the process to attempt to do operations within its container that would compromise the container's security.  While it takes a successful attack to get malicious rules into the feed of updates, this means that such an attack can escalate to container control and perhaps further.  This can be limited if the process in the container is an unprivileged process running as a normal user without any capabilities, meaning that it cannot write files owned by other users.

## A CNF has a security-compromising bug

A CNF unwittingly has a bug where an appropriately crafted packet will write a file at a location on the disk dependent on the packet's content.  This can lead to compromise.  Many possibilities for compromise are prevented if the process in question does not have privileges to write in the filesystem, as is typically available to a container root user.

A CNF may also have a bug where it attempts to rewrite settings files that keep the CNF secure (e.g. files containing credentials).  If the file is not owned by the process and the process is not itself a root process it has no privilege to change those files.
