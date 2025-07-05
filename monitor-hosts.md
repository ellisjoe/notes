Install node-exporter on each node:
```
sudo apt install prometheus-node-exporter
```

Update Prometheus config:
```
  - job_name: "nodes"
    scrape_interval: 30s
    static_configs:
    - targets: ['node1.tailnet.ts.net:9100', 'node2.tailnet.ts.net:9100']
```

Node exporter grafana dashboard:
https://grafana.com/grafana/dashboards/1860-node-exporter-full/
