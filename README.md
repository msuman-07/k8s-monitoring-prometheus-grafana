# Kubernetes Monitoring on AWS EKS  
### Prometheus + Grafana + Alertmanager Setup

## Overview

This project demonstrates an end-to-end monitoring setup on **Amazon EKS** using:

- Amazon EC2 (Bastion Host)
- IAM Role (Administrator access for cluster operations)
- Amazon EKS (Kubernetes Cluster)
- Managed Node Group
- Helm
- Prometheus
- Grafana
- Alertmanager

The setup provisions a Kubernetes cluster and deploys the `kube-prometheus-stack` for cluster observability.

---

## What This Project Does

- Creates an EC2 bastion server with IAM role attached
- Installs required CLI tools (AWS CLI, kubectl, eksctl, Helm)
- Provisions an Amazon EKS cluster
- Creates a managed node group
- Deploys Prometheus, Grafana, and Alertmanager using Helm
- Configures port-forwarding to access monitoring dashboards
- Demonstrates dashboard import in Grafana
- Includes full cleanup steps to stop AWS billing

---

## Technologies Used

- AWS EC2
- AWS IAM
- Amazon EKS
- Kubernetes
- Helm
- Prometheus
- Grafana
- Alertmanager
- Ubuntu 22.04

---

## Prerequisites

- AWS Account
- Region set to `us-east-1` (or modify commands accordingly)
- EC2 instance with IAM role attached (AdministratorAccess)
- SSH key pair

---

## Monitoring Stack

The project deploys:

- **Prometheus** – Metrics collection
- **Grafana** – Visualization dashboards
- **Alertmanager** – Alert handling
- **Node Exporter & kube-state-metrics** – Cluster metrics

Deployment is done using:


prometheus-community/kube-prometheus-stack


---

## Accessing Services

After deployment:

- Grafana → `http://<ec2-public-ip>:8080`
- Prometheus → `http://<ec2-public-ip>:9090`
- Alertmanager → `http://<ec2-public-ip>:9093`

Grafana default credentials:


Username: admin
Password: prom-operator


---

## Cleanup

To avoid AWS charges:

helm uninstall monitoring --namespace monitoring
kubectl delete ns monitoring
eksctl delete cluster --name observability6 --region us-east-1

Then terminate the EC2 instance from the AWS Console.

Purpose

This project demonstrates practical knowledge of:

Kubernetes cluster provisioning

Cloud infrastructure management

Observability stack deployment

Production-style monitoring setup on AWS

## Author

Suman M
