# Configuration best practices of Kubernetes system components

## Kubernetes API server security best practices!

### Disabling anonymous requests 
Kubernetes API server must be configured to reject requests from unauthenticated/anonymous sources; the default configuration allows such requests. Only authenticated users should be able to make requests to the API server. Set `--anonymous-auth` to `false`.
This is a bad practice and only authenticated users should be able to make requests to the API server. Set `--anonymous-auth` to `false`.
### Enabling audit logging 
API server audit logging is the functionality that enables operators to keep a record of requests to the cluster. It records the requests together with the initiator identity, therefore, enabling security teams to track events happening in the system.
API server configuration enables versatile configuration of audit logs which can be delivered to a file or a webhook. See `--audit-log-path` or `--audit-policy-file` configuration.
### API authorization configuration
Kubernetes API server supports multiple authorization plug-ins:
* Attribute-Based Access Control (ABAC) mode allows you to configure policies using local files.
* Role-based access control (RBAC) mode allows you to create and store policies using the Kubernetes API.
* Webhook is an HTTP callback mode that allows you to manage authorization using a remote REST endpoint and practically defer access control decisions to a non K8s entity 
* Node authorization is a special-purpose authorization mode that specifically authorizes API requests made by kubelets.
* AlwaysAllow allows all requests to be accepted (practically bypass access control)
AlwaysAllow is a bad choice.
The recommended way is to use “Role-based access control” since it gives a rich and manageable way to define access control in Kubernetes. Beyond the security perspective, this also makes the cluster compatible with applications requiring special authorization setup.

### Extending API access control limits with admission controllers
Kubernetes role based access control has its limitations. For example, if an entity has rights to create PODs it eventually gets full control over nodes running the cluster. This happens due to the fact that RBAC does not differentiate between a common POD and a privileged POD which has direct access to the host resources.
Admission controllers are optional components in a cluster enabling a more complex limitation strategy over the cluster. They are important security tool, especially in multi user environments.
### API server client authentication
API server supports multiple client authentication technologies. These technologies answer different authentication needs and therefore there is not a single choice which can be considered a “best practice”, however there are best practices which can be applied to multiple choices and paramount the security of the API server and to the cluster in general.

#### Anonymous users
Allowing anonymous (unauthenticated users) is a bad practice in any production environment. Make sure `--anonymous-auth` is set to false in the API server configuration.

#### Authentication credentials confidentiality
All authentication methods require some kind of client credentials to authenticate against. Known credential are:
Private key (client certificate authentication)
Tokens 
Passwords

These credentials need to be kept private in every case since they are the single factor for an attacker to access Kubernetes API resources.
Revocation and rotation of authentication credentials
An operator must be able to manage authentication credentials and be able to revoke or rotate them. This is a must since different human errors can lead to leaks or theft, or simply access needs to be revoked.

Different authentication methods support this functionality at different levels. Static token authentication requires restarts to the API server every time a token is revoked. Client certificate authentication revocation is not supported, but client certificates can have limited expiration periods therefore they can be “implicitly revoked” after some time and can be rotated regularly. The re-generation of newly signed client certificates makes operations more complex therefore operators tend to give longer expiration dates, which is not a good practice.

OpenID Connect tokens can be easily configured to have short expiration time and due to the fact of the interactive nature of OpenID protocol it is simple to tackle the key rotation problem. 

It is very important for the operator to prepare the system with this requirement in mind and prepare for these.
