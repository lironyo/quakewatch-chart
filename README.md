# QuakeWatch Helm Chart ⎈

Helm chart for deploying QuakeWatch, a Flask-based earthquake data visualization application on Kubernetes.

## ✨ Features

-  Horizontal Pod Autoscaling based on memory metrics
-  Health checks with liveness and readiness probes
-  Resource management and limits
-  Development and production configurations
-  Automated CI/CD integration

## 📦 Installation

```bash
helm repo add quakewatch https://lironyo.github.io/flask_quakeqatch-chart
helm repo update
helm install quakewatch quakewatch/quakewatch
```

Production deployment:

```bash
helm install quakewatch quakewatch/quakewatch -f values-prod.yaml
```

## ⚙️ Configuration

**Development**: Single replica, no resource limits, autoscaling disabled.

**Production**: Optimized for high availability and production workloads:
-  3 replicas for redundancy
-  Horizontal Pod Autoscaling (1-3 pods) at 40% memory utilization
-  Resource limits: 128Mi requests, 256Mi limits
-  Health checks: 20s liveness probe, 15s readiness probe
-  Automatic version updates via CI/CD

## 🚀 Usage

Access the application:

```bash
kubectl port-forward svc/quakewatch 5000:5000
```

Upgrade:

```bash
helm upgrade quakewatch quakewatch/quakewatch -f values-prod.yaml
```

Uninstall:

```bash
helm uninstall quakewatch
```

## 🔄 CI/CD

The chart automatically syncs with the main application repository. Version tags trigger GitHub Actions to update the Docker image reference in production values.

## 🔗 Links

- [Application Repository](https://github.com/lironyo/quakewatch)
- [Docker Image](https://hub.docker.com/r/lironyo98/flask_quakeqatch)
