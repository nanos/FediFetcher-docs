FediFetcher is also available in a pre-packaged container.

1. [Get an Access Token, if you haven't done so already](https://github.com/nanos/FediFetcher/wiki/Getting-an-access-token-for-FediFetcher)
2. Pull the container from `ghcr.io`, using Docker or your container tool of choice: `docker pull ghcr.io/nanos/fedifetcher:stable`
3. Run the container, passing the configurations options as command line arguments: `docker run -it ghcr.io/nanos/fedifetcher:stable --access-token=<TOKEN> --server=<SERVER>`, or using Environment variables.

See the [configuration options docs](https://github.com/nanos/FediFetcher/wiki/FediFetcher-configuration-options) for full details on how to configure FediFetcher.

## Choosing a tag

| Tag | What you get |
| --- | --- |
| `stable` | The latest stable release. **Use this unless you have a reason not to.** |
| `latest` | The latest release of any kind, including release candidates and betas. |
| `v8` | The latest stable release in the 8.x series. Pin to this to receive updates without ever being moved to version 9. |
| `v8.1` | The latest stable release in the 8.1.x series, so bug fixes only. |
| `v8.1.0` | That exact release. This tag never moves. |

Pre-releases are only ever published as `latest` and as their own exact version tag. They will never move `stable`, `v8`, or `v8.1`, so pinning to any of those will not land you on a release candidate.

> [!NOTE]
>
> Every tag except the exact version tags is a *floating* tag: it is repointed at a new image each time there is a release. If you use one, make sure your setup actually pulls again — `docker run` will keep using an image you have already pulled unless you `docker pull` first, and Kubernetes will do the same unless you set `imagePullPolicy: Always`.

> [!IMPORTANT]
>
> The same rules for running this as a cron job apply to running the container: don't overlap any executions.

Persistent files are stored in `/app/artifacts` within the container, so you may want to map this to a local folder on your system.

An [example Kubernetes CronJob](https://github.com/nanos/FediFetcher/blob/main/examples/k8s-cronjob.md) for running the container is included in the `examples` folder.

An [example Docker Compose Script](https://github.com/nanos/FediFetcher/blob/main/examples/docker-compose.yaml) for running the container periodically is included in the `examples` folder.
