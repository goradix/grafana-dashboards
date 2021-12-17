<div align="center">
	<br>
	<br>
  <img width="360" src="media/goradix-transparent.png" alt="vnode">
  <p>
    To support this project, please stake with our <a href="https://goradix.io">validator node</a>.
  </p>
	<br>
	<br>
</div>

## radix-node-multi-job

This is a fork of the ["offical" grafana dashboard](https://github.com/radixdlt/node-runner/blob/main/monitoring/grafana/provisioning/dashboards/sample-node-dashboard.json) but with added support for multiple jobs.

This dashboard is useful if you want to run one Prometheus/Grafana installation monitoring several Radix nodes.

<img width="100%" src="media/radix-node-multi-job.png" alt="multi-job">

### Installation

Either put the [radix-node-multi-job.json](dashboards/radix-node-multi-job.json) dashboard file in your grafana dashboards folder, or do a direct import of the [json file](dashboards/radix-node-multi-job.json) in the Grafana UI.

### Configurating Promethus to scrape multiple nodes

Once you have installed the dashboard, you need to configure Prometheus to scrape multiple Radix nodes using unique job names.

This is a sample `prometheus.yaml` with scrape configuration for two nodes:

```yaml
global:
  evaluation_interval: 30s
  scrape_interval: 30s
  scrape_timeout: 20s
scrape_configs:
  - basic_auth:
      password: ...
      username: ...
    job_name: radixnode-a
    scheme: https
    static_configs:
      - targets:
          - 10.1.0.50
    tls_config:
      insecure_skip_verify: true
  - basic_auth:
      password: ...
      username: ...
    job_name: radixnode-b
    scheme: https
    static_configs:
      - targets:
          - 10.2.0.50
    tls_config:
      insecure_skip_verify: true
```
