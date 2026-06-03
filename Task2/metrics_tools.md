Was done in task1:
- switch to clickhouse instead of prometheus
- multiple metrics workers collect metrics directly from Pods in Kubernetes cluster
- Clickhouse connected to grafana for simple reports
- Analytical streaming processed with flink as before
- Pricing Ml model use analytical data and counts prices for rides on flow