# Kubernetes Service Mesh with Istio

Istio is an open-source service mesh that layers transparently onto existing distributed applications. It's used to connect, monitor, and secure microservices within Kubernetes clusters.

## Concepts

An Istio service mesh is logically split into a **data plane** and a **control plane**.

- The **data plane** is composed of a set of intelligent proxies (Envoy) deployed as sidecars, mediating and controlling all network communication between microservices.

- The **control plane** manages and configures the proxies to route traffic, and configures Mixer to enforce policies and collect telemetry.

## Istio Components

- **Pilot**: provides service discovery for the Envoy sidecars, traffic management capabilities, and resiliency features such as circuit breakers, timeouts, retries, and fault injection.

- **Mixer**: enforces access control and usage policies across the service mesh, and collects telemetry data from the Envoy proxy and other services.

- **Citadel**: provides strong service-to-service and end-user authentication with built-in identity and credential management.

## Deployment Example

Deploy Istio using Helm:

```bash
$ helm install istio.io/istio
```

Deploy an application:

```bash
$ kubectl apply -f <(istioctl kube-inject -f samples/bookinfo/platform/kube/bookinfo.yaml)
```

Here, `istioctl kube-inject` modifies the application's pods to include an Envoy sidecar.

## Traffic Management

Istio allows you to direct traffic based on rules. An example of a simple routing rule:

```yaml
apiVersion: networking.istio.io/v1alpha3
kind: VirtualService
metadata:
  name: reviews-route
spec:
  hosts:
  - reviews.prod.svc.cluster.local
  http:
  - match:
    - headers:
        end-user:
          exact: jason
    route:
    - destination:
        host: reviews.prod.svc.cluster.local
        subset: v2
  - route:
    - destination:
        host: reviews.prod.svc.cluster.local
        subset: v1
```

This rule sends all traffic for the 'reviews' service to version v1, unless the end-user header is 'jason', in which case it goes to version v2.

## Conclusion

With Istio, Kubernetes gets a powerful service mesh. It adds traffic management, service identity and security, policy enforcement and telemetry all without requiring any changes to your application code.