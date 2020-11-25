# Loki

=========================

## Installation from [here](https://grafana.com/docs/loki/latest/installation/):

You need to follow these steps:

1. [Download](https://github.com/grafana/loki/releases/) binary package for loki and promtail (You can use alternate for promtail).
2. Download config file from the provided links . [loki](https://raw.githubusercontent.com/grafana/loki/master/cmd/loki/loki-local-config.yaml) and [promtail](https://raw.githubusercontent.com/grafana/loki/master/cmd/promtail/promtail-local-config.yaml)
3. Start with `--config.file=` argument

## Promtail Nginx conf

Link [Here](https://sbcode.net/grafana/nginx-promtail/)


## Dashboard

v2 dashboard [here](https://grafana.com/grafana/dashboards/12559)

### Converting nginx logs to JSON

1. Using **grok**. Blog link [here](https://medium.com/bolt-labs/using-json-for-nginx-log-format-793743064fc4)
2. From **nginx conf**. Blog link [here](http://www.continualintegration.com/miscellaneous-articles/how-do-you-get-nginx-logs-to-be-in-json-format/)

Configuration for different data source [here](https://grafana.com/docs/loki/latest/configuration/examples/)

## Alerting

Loki includes a component called the Ruler, adapted from our upstream project, Cortex. The Ruler is responsible for continually evaluating a set of configurable queries and then alerting when certain conditions happen, e.g. a high percentage of error logs. [more](https://grafana.com/docs/loki/latest/alerting/)

