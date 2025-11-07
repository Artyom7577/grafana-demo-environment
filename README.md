# CPU Usage Matrics 
## What You’ll Get

- **Prometheus** scraping demo metrics
- **Grafana** serving your dashboard
- **Test data** scripts to push synthetic CPU metrics

**Default local endpoints**
- Grafana: http://localhost:3000  
- Prometheus: http://localhost:9090  
- Pushgateway (if used by test scripts): http://localhost:9091  
- Alertmanager: http://localhost:9093

---
- For Grafana:

Copy environments/smpt.env.example to environments/smpt.env and set the appropriate environment variables values.

---

## Prerequisites

- **Docker** & **Docker Compose plugin**  
  - Check: `docker --version` and `docker compose version`
- **Node.js 18+** (for running the test data JS scripts)  
  - Check: `node -v`
- grafana-cpu-metrics.json

---

## Quick Start

1) **Clone the demo stack**
```bash
git clone https://github.com/grafana/demo-prometheus-and-grafana-alerts
cd demo-prometheus-and-grafana-alerts

mkdir -p dashboards

docker compose up -d
docker compose ps
```
- Open Grafana → http://localhost:3000
- Go to Dashboards → New → Import
- Upload JSON file: select /grafana-cpu-metrics.json
- Click Import

## Generate Demo Metrics
This demo uses Grafana k6 to generate test data for Prometheus and Loki.

The k6 tests in the testdata folder inject Prometheus metrics and Loki logs that you can use to define alert queries and conditions.

- Install k6 v1.2.0 or later.

- Run a k6 test with the following command:

- k6 run testdata/<FILE>.js

You can modify and run the k6 scripts to simulate different alert scenarios. For details on inserting data into Prometheus or Loki, see the xk6-client-prometheus-remote and xk6-loki APIs.

