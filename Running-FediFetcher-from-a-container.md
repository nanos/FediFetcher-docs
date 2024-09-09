FediFetcher is also available in a pre-packaged container.

1. [Get an Access Token, if you haven't done so already](https://github.com/nanos/FediFetcher/wiki/Getting-an-access-token-for-FediFetcher)
1. Pull the container from `ghcr.io`, using Docker or your container tool of choice: `docker pull ghcr.io/nanos/fedifetcher:latest`
2. Run the container, passing the configurations options as command line arguments: `docker run -it ghcr.io/nanos/fedifetcher:latest --access-token=<TOKEN> --server=<SERVER>`, or using Environment variables.

See the [configuration options docs](https://github.com/nanos/FediFetcher/wiki/FediFetcher-configuration-options) for full details on how to configure FediFetcher.

> [!IMPORTANT]
>
> The same rules for running this as a cron job apply to running the container: don't overlap any executions.

Persistent files are stored in `/app/artifacts` within the container, so you may want to map this to a local folder on your system.

An [example Kubernetes CronJob](https://github.com/nanos/FediFetcher/blob/main/examples/k8s-cronjob.md) for running the container is included in the `examples` folder.

An [example Docker Compose Script](https://github.com/nanos/FediFetcher/blob/main/examples/docker-compose.yaml) for running the container periodically is included in the `examples` folder.
