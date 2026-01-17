# Online Shop (On-Prem Kubernetes)

Production-style on-prem deployment of a microservices-based "Online Shop" application on a single-node Kubernetes cluster running on a persistent USB Ubuntu laptop.

## Architecture

### Platform Architecture
![Platform Architecture](docs/diagrams/01-platform-architecture.png)

### Network Topology
![Network Topology](docs/diagrams/02-network-topology.png)

## Repository Structure
- docs/            Documentation and diagrams
- platform/        Cluster bootstrap, ingress, storage, namespaces
- apps/online-shop Application manifests/values
- environments/    dev/prod environment configuration
- scripts/         Setup/teardown/verify scripts

## Edge Gateway (On-Prem Front Door)

The platform uses a host-level NGINX reverse proxy as an on-prem edge gateway.

This is required because Kubernetes ingress controllers do not bind directly
to host ports 80/443 in on-prem environments.

The edge gateway:
- Listens on 80/443 on the host
- Terminates HTTPS
- Forwards traffic to Kubernetes ingress via NodePort

See:
platform/edge-nginx/
