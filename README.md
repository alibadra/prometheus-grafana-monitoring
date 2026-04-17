# Prometheus + Grafana Monitoring Stack

Full observability stack deployable with a single `docker compose up`. Includes pre-wired dashboards, alert rules, and an Alertmanager config ready for Slack/PagerDuty.

## Components

| Service | Port | Purpose |
|---------|------|---------|
| Prometheus | 9090 | Metrics collection & alerting |
| Grafana | 3000 | Dashboards & visualization |
| Alertmanager | 9093 | Alert routing |
| Node Exporter | 9100 | Host metrics |
| cAdvisor | 8080 | Docker container metrics |
| Blackbox Exporter | 9115 | HTTP/TCP endpoint probing |

## Quick Start

```bash
cp .env.example .env
# Edit .env with your Slack webhook and credentials

docker compose up -d

# Grafana: http://localhost:3000 (admin/changeme)
# Prometheus: http://localhost:9090
```

## Dashboards Included

- **Node Overview** — CPU, memory, disk, network per host
- **Docker Containers** — Resource usage per container
- **Nginx** — Request rate, latency, error rate
- **Blackbox** — Uptime and SSL expiry per endpoint

## Alert Rules

- Host down > 1 minute
- CPU > 85% for 5 minutes
- Memory > 90% for 5 minutes
- Disk > 85% (any mount)
- SSL certificate expiring < 30 days
- HTTP endpoint returning non-2xx
