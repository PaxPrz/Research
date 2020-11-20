# Prometheus
===================

### Main Component: Prometheus Server

<img src="./images/prometheus_server.png" width="600px">


### Metrics:

- Format: **Human-readable** text-based
- Metrics entries: **TYPE** and **HELP** attributes

**HELP** : Description of what the metrics is

**TYPE**: One of 3 following type:

    - 1. **Counter**: How many times x happened?
    - 2. **Gauge**: What is the current value of x now?
    - 3. **Histogram**: How long or how big?


### Collecting Metrics Data from Targets

<img src="./images/collecting_metric_data_from_targets.png" width="600px">


## Target Endpoints and Exporters

- Collects metrics using HTTP request (PULL method).
- Many have build in promethus endpoint.
- For those service not having endpoint, use exporters

### Exporter

These are script or services that:

1. Fetches metrics
2. Converts to correct format
3. Expose /metrics

Exporter list [Here](https://prometheus.io/docs/instrumenting/exporters/). Exporter are also available as docker images:

- Download exporter
- Untar and execute
- converts metrics of the server
- exposes /metrics endpoint
- configure Prometheus to scrape this endpoint

### Monitoring your own applications

Using [client libraries](https://prometheus.io/docs/instrumenting/clientlibs/) you can expose /metrics endpoint



### Pushgateway:

For **"short-lived job"**: push metrics at exit


## Configuring Prometheus

> prometheus.yml


## Alert Manager

- push alerts to **Alertmanager** which notifies users through *email*, *slack channel*, etc..

## Data Storage

- Stores metrics data in disk
- Stored in custom time series format

## PromQL

- Query target directly

e.g.: 

`http_requests_total{status!="4.."}` : Query all HTTP status codes except 4xx ones

`rate(http_requests_total[5m])[30m:]` : Returns the 5-minute rate of the http_requests_total metric for the past 30mins




