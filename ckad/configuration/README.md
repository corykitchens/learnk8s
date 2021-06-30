# Configuration

Kubernetes provides advanced configuration options for Pods and containers. Many of those options are represented as primitives, and others simply blend in with the YAML configuration from the previous chapter.

These primitives are known as the following..

- ConfigMaps
- Secrets
- SecurityContexts
- Resource Requirements
- Service Accounts

ConfigMaps and Secrets allow developers to inject configuration data as environment varables.

ConfigMaps and secrets can be injected as string literals, or a configuration file mounted as a volume, or configured via the `spec.containers[0].envFrom.configMapRef`

Secrets build off of ConfigMaps and are used to store sensitive data like database connection strings, API keys, etc.
Secrets storedi in YAML manfiest must be bas64-encoded. It will automatically be decoded.

By default, containers run as the `root` user. That means full access to the filesystem and the ability to run any process. Security Contexts allow developers to specify the container to run as a non-root user.

Note - Container-level defintions for the user/group permissions will take precedence over Pod-level security definitions.

A ResourceQuota defines the soft/hard limits of computing resources (CPU, RAM, disk space) within a namespace. You can also limit the number of resource types (number of Pods) that are allowed to be created.

Pods must declare their min/max resource expections in the form of `resource requests` and `resource limits`

Service Accounts defines the permissions for a Pod that needs to communicate with the API server. This is much like an AWS IAM Role. If none is defined, the `default` service account is assigned to the Pod. Service Accounts can be assigned via the `spec.serviceAccountName` key.

## Exam Essentials

**Know how to create and consume ConfigMaps and Secrets**

- Create imperatively/declaritively
- Assign using literals
- Assign as config files
- Assign as files/directories
- Creating secrets imperatively automatically base64-encoded the value. Declaritive requires prior-encoding

**Experiment with options available to security context**

- PodSecurityContext vs SecurityContext
- User/Group permissions

**Understand resource boundaries**

- Define soft/hard limits on computing resources
- Know how to list hard requirements and whats currently in use in the namespace

**Know how to create and assign a custom Service Account**

- Know how to create/assign Service Accounts
