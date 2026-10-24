# Kubernetes Task 2 — Deploy NGINX on Amazon EKS

## Project objective

Create an Amazon EKS cluster, deploy an NGINX application with two replicas,
and access the application from outside the Kubernetes cluster.

## Architecture

Browser
  |
    v
    AWS Load Balancer
      |
        v
        Kubernetes Service (LoadBalancer)
          |
            v
            NGINX Deployment
              |
                +-- NGINX Pod 1
                  |
                    +-- NGINX Pod 2

## Technologies

- Amazon EKS
- Amazon EC2 managed node groups
- Kubernetes
- eksctl
- kubectl
- NGINX
- AWS Load Balancer

## Configuration

- Cluster name: nginx-eks-demo
- AWS region: ap-south-1 (Mumbai)
- Kubernetes version: 1.36
- Worker nodes: 2 x t3.medium
- Worker-node storage: 20 GiB gp3 per node
- NAT gateway: Disabled
- EKS API access: Public and private
- Public API CIDR: Restricted to the configured CloudShell IP
- Application replicas: 2
- Application port: TCP 80
- Service type: LoadBalancer

## Project files

- `eks-cluster.yaml` — EKS cluster and worker-node configuration
- `nginx-deployment.yaml` — NGINX Deployment with two replicas
- `nginx-service.yaml` — LoadBalancer Service for external access
- `screenshots/` — Evidence captured during project execution

## Deployment status

The configuration files have been created and the eksctl dry-run preview
has succeeded. AWS resource creation and application deployment have not
yet been performed.

## Deployment steps

Run these commands only after reviewing the configuration, estimated costs,
and explicitly approving AWS resource creation.

### 1. Create the EKS cluster

```bash
eksctl create cluster --config-file=eks-cluster.yaml
