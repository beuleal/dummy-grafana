# Dummy Grafana

This is the Grafana project, responsible to query Loki and also show the logs, metrics, dashboards, alerts etc

## Adding Data sources

### Prometheus

The Prometheus IP must be the host IP. Just run `ifconfig` or `ip addr show` to find it.

And the port must be the one exposed by the compose. By default, its port is 9090.

Example:

```txt
http://12.168.0.XXX:9090
```

## Query LogQL

LogQL is Grafana Loki's PromQL-inspired query language.

Examples:

1. Return all POST requests

```logql
{app="dummy-python-api"} | json method="method" | method = "POST"
```

2. If you have the labels `method` and `response_code` set in Vector, you can run the following query to get all logs with Delete and Patch that has error code 404:

```logql
{app="dummy-python-api",method=~"DELETE|PATCH",response_code="404"}
```
