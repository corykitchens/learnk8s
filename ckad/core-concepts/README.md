# CKAD Core Concepts

## Summary

Kubernetes represents its functionality for deploying and operating cloud-nation applications with the help of primitives. Each primitive follows a general structure,

- API Version
- The Kind
- Metadata
- Spec/Desired state of resources

Upon creation or modification of the object, Kubernetes scheduler automatically tries to ensure that the actual state of the object follows the defined specification. Every live object can be inspected, edited, and deleted.

The portion of "Core Concepts" of the curriculum puts a strong emphasis on the concept of a Pod. The Pod is a Kubernetes primitive responsible for running an application in a container. Kubernetes uses Docker as its default container runtime technology. A Pod can define one or many containers that use a container image. Upon its creation, the container image is resolved and used to bootstrap the application. Every Pod can be further customized with the relevant YAML configuration.

## Exam Essentials

- Manage Kubernetes objects
  - Imperative vs declaritive approach to creating objects
  - For simple pods, use `kubectl run` for imperative approach, other objects use `kubectl create`
  - For declarative approach use `kubectl apply -f <object.manifest>`
