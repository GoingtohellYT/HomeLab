## Services used for resource monitoring

### Prometheus

Prometheus manages the data collected by its connectors or by itself. It also introduces the PromQL query language, which allows you to retrieve specific information.

Without it, there’s no Node Exporter, no cAdvisor, and no Grafana dashboard!

### Node Exporter

Node Exporter scrapes all data relevant to my server’s hardware status, making it a critical part of my monitoring strategy. This data is then sent to Prometheus.

### cAdvisor

cAdvisor lets me visualize the Docker containers running on the homelab and the resources they use, making it essential for monitoring since most hosted services run in Docker. It acts as a Prometheus connector.

### Grafana

Grafana displays metrics scraped by the services above — such as RAM usage, CPU load, available disk space, and swap usage.
It also sends alerts via Discord when there’s an issue requiring my attention, so I can either shut the server down or fix the problem, depending on the situation.
