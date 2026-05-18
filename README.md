# Kubernetes Guestbook Monitoring with Pulumi

## Overview

This project deploys the Kubernetes Guestbook application using Pulumi and TypeScript.

Monitoring is integrated using:
- Prometheus
- Grafana

The monitoring stack collects Kubernetes and application metrics and visualizes them through Grafana dashboards.

---

## Prerequisites

Install the following tools:

- Node.js
- Docker Desktop
- Kubernetes enabled in Docker Desktop
- Pulumi CLI
- kubectl
- Helm

---

## Deployment Steps

Clone repository:

```bash
git clone <repo-url>
cd kubernetes-ts-guestbook/simple
```

Install dependencies:

```bash
npm install
```

Login locally to Pulumi:

```bash
pulumi login --local
```

Create stack:

```bash
pulumi stack init dev
```

Deploy infrastructure:

```bash
pulumi up
```

---

## Verify Guestbook Application

Check pods:

```bash
kubectl get pods
```

Check services:

```bash
kubectl get svc
```

Port forward frontend:

```bash
kubectl port-forward svc/frontend 8080:80
```

Open browser:

http://localhost:8080

---

## Verify Grafana

Port forward Grafana:

```bash
kubectl port-forward -n monitoring svc/grafana 3000:80
```

Open browser:

http://localhost:3000

Credentials:

Username: admin

Password: admin123

---

## Verify Prometheus

Port forward Prometheus:

```bash
kubectl port-forward -n monitoring svc/prometheus-server 9090:80
```

Open browser:

http://localhost:9090

Run query:

```promql
up
```

Additional query:

```promql
kube_pod_info
```

This verifies Prometheus metrics scraping.

---

## Monitoring Components

- Prometheus
- Grafana
- Alertmanager
- kube-state-metrics
- node-exporter

---

## Cleanup

```bash
pulumi destroy
```