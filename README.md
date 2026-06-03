# Grafana Monitoring Project

## Overview

This project implements a basic monitoring and visualization system using Grafana and Prometheus on Ubuntu through Docker containers.

The system collects real-time operating system metrics such as CPU usage and node status, stores them in Prometheus, and visualizes them through Grafana dashboards.

This project was developed as part of a Network Management course assignment focusing on data visualization and monitoring infrastructure.

---

## Objectives

* Deploy Grafana Monitoring Server
* Collect system metrics using Node Exporter
* Store metrics using Prometheus
* Visualize monitoring data using Grafana
* Implement required dashboard components:

  * Gauge Panel
  * Time Series Panel
  * Stat Panel
* Verify data consistency between Prometheus and Grafana

---

## System Architecture

Node Exporter collects system metrics from the Ubuntu host.

Prometheus periodically scrapes metrics from Node Exporter.

Grafana retrieves data from Prometheus and displays it through dashboards.

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

---

## Technologies Used

| Component     | Purpose                     |
| ------------- | --------------------------- |
| Ubuntu        | Operating System            |
| Docker        | Container Platform          |
| Node Exporter | System Metrics Collection   |
| Prometheus    | Monitoring and Data Storage |
| Grafana       | Data Visualization          |

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
git clone <repository-url>
cd grafana-project
```

### Start Services

```bash
sudo docker-compose up -d
```

### Verify Running Containers

```bash
sudo docker ps
```

Expected containers:

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

## Dashboard Components

### 1. Stat Panel

Metric:

```promql
up
```

Purpose:

Display node operational status.

Output:

```text
UP
```

---

### 2. Gauge Panel

Metric:

```promql
100 - (avg(rate(node_cpu_seconds_total{mode="idle"}[5m])) * 100)
```

Purpose:

Display current CPU utilization percentage.

---

### 3. Time Series Panel

Metric:

```promql
100 - (avg(rate(node_cpu_seconds_total{mode="idle"}[5m])) * 100)
```

Purpose:

Display CPU utilization trends over time.

---

## Data Verification

To verify dashboard accuracy, the same PromQL query is executed directly in Prometheus and compared against the values displayed in Grafana.

Example:

Prometheus:

```text
20.93
```

Grafana:

```text
20.9%
```

The difference is only due to display rounding, confirming data consistency.

---

## Testing and Validation

The following requirements were successfully completed:

* Grafana Server Deployment
* Prometheus Data Source Integration
* Gauge Visualization
* Time Series Visualization
* Stat Visualization
* Data Verification
* Time Range Interaction Testing

---

## Results

The monitoring dashboard successfully provides:

* Real-time CPU monitoring
* Historical CPU trend analysis
* Node operational status monitoring
* Interactive dashboard visualization

---

## Future Improvements

* Memory monitoring dashboard
* Disk usage monitoring
* Network bandwidth monitoring
* Alerting system integration
* Multi-node monitoring

---

## Author

Network Management Course Project

Grafana Monitoring Dashboard using Prometheus and Docker on Ubuntu
