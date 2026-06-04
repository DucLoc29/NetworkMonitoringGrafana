# Grafana Monitoring Project

## Overview

This project implements a simple monitoring and visualization platform using Grafana, Prometheus, and Node Exporter on Ubuntu through Docker containers.

The system collects real-time operating system metrics such as CPU usage and node status, stores them in Prometheus, and visualizes them through Grafana dashboards.

---

## Features

* Real-time system monitoring
* Prometheus metrics collection
* Grafana dashboard visualization
* Node status monitoring
* CPU usage monitoring
* Historical CPU trend analysis
* Interactive time range selection

---

## System Architecture

```text
Ubuntu Host
      │
      ▼
Node Exporter
      │
      ▼
 Prometheus
      │
      ▼
  Grafana
      │
      ▼
 Dashboard
```

### Components

| Component     | Purpose                   |
| ------------- | ------------------------- |
| Ubuntu        | Operating System          |
| Docker        | Container Platform        |
| Node Exporter | System Metrics Collection |
| Prometheus    | Monitoring & Data Storage |
| Grafana       | Data Visualization        |

---

## Dashboard Components

### 1. Node Status (Stat)

Displays node operational status.

PromQL:

```promql
up
```

Example Output:

```text
UP
```

---

### 2. CPU Usage (Gauge)

Displays current CPU utilization percentage.

PromQL:

```promql
100 - (avg(rate(node_cpu_seconds_total{mode="idle"}[5m])) * 100)
```

---

### 3. CPU Usage Over Time (Time Series)

Displays CPU utilization trends over time.

PromQL:

```promql
100 - (avg(rate(node_cpu_seconds_total{mode="idle"}[5m])) * 100)
```

---

## Requirements

Before running this project, ensure the following software is installed:

* Ubuntu 24.04 LTS
* Docker Engine
* Docker Compose
* Git

Verify Docker installation:

```bash
docker --version
```

---

## Project Structure

```text
grafana-project/
│
├── docker-compose.yml
├── prometheus.yml
└── README.md
```

---

## Installation

### Clone Repository

```bash
git clone https://github.com/YOUR_USERNAME/grafana-monitoring-project.git

cd grafana-monitoring-project
```

---

### Start Services

```bash
sudo docker-compose up -d
```

---

### Verify Containers

```bash
sudo docker ps
```

Expected output should include:

```text
grafana
prometheus
node-exporter
```

---

## Access Services

### Grafana

```text
http://localhost:3000
```

Default credentials:

```text
Username: admin
Password: admin
```

---

### Prometheus

```text
http://localhost:9090
```

---

### Node Exporter Metrics

```text
http://localhost:9100/metrics
```

---

## Data Verification

To verify dashboard accuracy, execute the same PromQL query directly in Prometheus and compare it with the value displayed in Grafana.

Example:

Prometheus:

<img width="838" height="386" alt="image" src="https://github.com/user-attachments/assets/627ec2b8-9eca-4d63-9893-52418dee4ed2" />


Grafana:

<img width="765" height="459" alt="image" src="https://github.com/user-attachments/assets/13372652-61bb-4aa3-880e-4f8b142b507a" />


The difference is only due to display rounding.

---

## Testing

The project successfully demonstrates:

* Prometheus data collection
* Grafana visualization
* Node monitoring
* Real-time dashboard updates
* Time range interaction
* Data consistency verification

---

## Future Improvements

Potential future enhancements include:

* RAM monitoring dashboard
* Disk usage monitoring
* Network traffic monitoring
* Alert notifications
* Multi-node monitoring
* Email or Telegram alerts

---

## Screenshots

### Prometheus Target Status

<img width="945" height="416" alt="image" src="https://github.com/user-attachments/assets/7dfbbe62-09d6-416b-a246-d07763a5ef8a" />


### Grafana Data Source Connection

<img width="945" height="170" alt="image" src="https://github.com/user-attachments/assets/b0ae2a42-9370-4390-9b8e-08da8fdb69ad" />


### Monitoring Dashboard

<img width="945" height="510" alt="image" src="https://github.com/user-attachments/assets/fad88cb2-27c0-461d-a0ea-92814e67d4e9" />



