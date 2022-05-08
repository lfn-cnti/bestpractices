# Kubernetes API server security best practices!

## Disabling anonymous requests 
The Kubernetes API server must be configured to reject requests from unauthenticated/anonymous sources; the default configuration allows such requests. Only authenticated users should be able to make requests to the API server. Set `--anonymous-auth` to `false`.
## Enabling audit logging 
API server audit logging is the functionality that enables operators to keep a record of requests to the cluster. It records the requests together with the initiator identity, therefore, enabling security teams to track events happening in the system.
API server configuration enables versatile configuration of audit logs which can be delivered to a file or a webhook. See `--audit-log-path` or `--audit-policy-file` configuration.
## API authorization configuration
Kubernetes API server supports multiple authorization plug-ins:
* Attribute-Based Access Control (ABAC) allows you to configure fine-grained access control policies per user, environment or resource attributes. The ABAC policies are specified in files; can't be managed using APIs. This means that in order to change these policies, the operator needs to be able to access these files.
* Role-based access control (RBAC) mode allows you to configure `Role` objects and grant them authorizations while enabling them to be associated with users and groups via `RoleBinding` objects. These objects are Kubernetes API objects as opposed to ABAC policies.
* Webhook is an HTTP callback mode that allows you to manage authorization using a remote REST endpoint and practically defer access control decisions to a non-K8s entity 
* Node authorization is a special-purpose authorization mode that specifically authorizes API requests made by Kubelets.
* AlwaysAllow allows all requests to be accepted (practically bypass access control)
AlwaysAllow is a bad choice.
The recommended way is to use “Role-based access control” since it gives a rich and manageable way to define access control in Kubernetes. Beyond the security perspective, this also makes the cluster compatible with applications requiring special authorization setup.

## Extending API access control limits with admission controllers
Kubernetes role based access control has its limitations. For example, if an entity has rights to create PODs it eventually gets full control over nodes running the cluster. This happens due to the fact that RBAC does not differentiate between a common POD and a privileged POD which has direct access to the host resources.
Admission controllers are optional components in a cluster enabling a more complex limitation strategy over the cluster. They are important security tool, especially in multi user environments.
## API server client authentication
API server supports multiple client authentication technologies. These technologies answer different authentication needs. There is not a single choice that can be considered a “best practice”. However, there are best practices that can be applied to multiple authentication technologies. These settings are paramount to the security of the API server and to the cluster in general.

### Anonymous users
Allowing anonymous (unauthenticated users) is a bad practice in any production environment. Make sure `--anonymous-auth` is set to false in the API server configuration.

### Authentication credentials confidentiality
All authentication methods require some kind of client credentials to authenticate against. Known credential are:
* Private key (client certificate authentication)
* Tokens 
* Passwords

These credentials need to be kept private in every case since they are the single factor for an attacker to access Kubernetes API resources.

### Revocation and rotation of authentication credentials
An operator must be able to manage authentication credentials and be able to revoke and rotate them. This is a must best security practice. Rotation reduces the risk of misuse of long unchanged credentials (become widely available),  while revocation of credentials needs to be performed for users who no longer need them.

Different authentication methods support this functionality at different levels. Static token authentication requires restarts to the API server every time a token is revoked. Client certificate authentication revocation is not supported, but client certificates can have limited expiration periods therefore they can be “implicitly revoked” after some time and can be rotated regularly. The re-generation of newly signed client certificates makes operations more complex therefore operators tend to give longer expiration dates, which is not a good practice.

OpenID Connect tokens can be easily configured to have short expiration time and due to the fact of the interactive nature of OpenID protocol it is simple to tackle the key rotation problem. 

It is very important for the operator to prepare the system with this requirement in mind and prepare for these.

## References
- [kube-apiserver configuration reference](https://kubernetes.io/docs/reference/command-line-tools-reference/kube-apiserver/)
- [securing Kubernetes system components](https://www.cncf.io/blog/2021/08/20/how-to-secure-your-kubernetes-control-plane-and-node-components/)
- [kube-apiserver access security blog 1](https://goteleport.com/blog/kubernetes-api-access-security/)
- [kube-apiserver access security blog 2](https://developer.okta.com/blog/2021/12/02/k8s-security-best-practices)
  
