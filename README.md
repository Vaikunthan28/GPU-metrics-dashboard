# GPU-metrics-dashboard
Simulate a real GPU workload on Kubernetes and monitor it using Prometheus, Grafana, and NVIDIA DCGM Exporter.

🧱 Architecture Diagram

```
                      ┌──────────────────────────────┐
                      │        Kubernetes Cluster     │
                      │                              │
                      │  ┌────────────────────────┐  │
                      │  │  GPU Workload Pod      │  │
                      │  │  (PyTorch Loop)        │  │
                      │  └────────┬───────────────┘  │
                      │           │                  │
                      │  ┌────────▼──────────┐       │
                      │  │ NVIDIA DCGM Exporter│─────┐│
                      │  └────────┬───────────┘     ││
                      │           │                 ││
                      │      ┌────▼────┐            ││
                      │      │Prometheus│───────────┘│
                      │      └────┬────┘             │
                      │           │                  │
                      │      ┌────▼────┐             │
                      │      │ Grafana │─────────────┘
                      │      └─────────┘
                      └──────────────────────────────┘

```

📁 GitHub Repo Structure

```
gpu-metrics-dashboard/
├── terraform/                # (optional later)
│   └── main.tf               # AWS GPU instance or EKS
├── docker/
│   └── Dockerfile            # Runs PyTorch GPU workload
├── k8s/
│   ├── gpu-workload.yaml     # GPU Pod Deployment
│   ├── dcgm-exporter.yaml    # NVIDIA metrics exporter
│   ├── prometheus.yaml       # Prometheus config
│   └── grafana.yaml          # Grafana deployment & dashboard
├── monitoring/
│   └── sample-dashboard.json # Optional custom dashboard
├── .gitlab-ci.yml / .github/ # CI/CD pipeline (optional)
└── README.md

```
