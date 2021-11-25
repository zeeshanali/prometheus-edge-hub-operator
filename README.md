# prometheus-edge-hub-operator

## Description

Prometheus Edge Hub is a replacement of the Prometheus Pushgateway which allows for the pushing of 
metrics to an endpoint for scraping by prometheus, rather than having Prometheus scrape the metric 
sources directly. This differs from the Prometheus Pushgateway in several ways, the most important 
of which being that it does not overwrite timestamps and that metrics do not persist until updated. 
When the hub is scraped, all metrics are drained.

This project is a Juju charm to deploy Prometheus Edge Hub on Kubernetes.


## Usage

For now, you have to build the charm yourself before deploying it. Please refer to CONTRIBUTING.md
for more information on the build itself. Once it is built, you can deploy the charm using 
`juju deploy`: 

```bash
juju deploy ./prometheus-edge-hub_ubuntu-20.04-amd64.charm \
 --config grpc-port=9092 \
 --config limit=500000 \
 --resource prometheus-edge-hub-image=facebookincubator/prometheus-edge-hub:1.1.0
```

## Configs

Note that config for `port` and `grpc-port` have to be set at the deploy time. Trying to change 
them at a further time won't change the Kubernetes service exposed port.

## OCI Images

Default image: facebookincubator/prometheus-edge-hub:1.1.0

## Contributing

Please see the `CONTRIBUTING.md` for developer guidance.
