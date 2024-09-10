Running FediFetcher as a cron job is in many ways the best way of running FediFetcher if you already have a linux device somewhere. This could be a your mastodon server, or another device (such as a Raspberry Pi).

Tu run FediFetcher as a cron job:

1. [Get an Access Token, if you haven't done so already](https://github.com/nanos/FediFetcher/wiki/Getting-an-access-token-for-FediFetcher)
1. Clone this repository.
2. Install requirements: `pip install -r requirements.txt`
3. Create a `json` file with [your configuration options](https://github.com/nanos/FediFetcher/wiki/FediFetcher-configuration-options). You may wish to store this in the `./artifacts` directory, as that directory is `.gitignore`d
4. Then simply run this script like so: `python find_posts.py -c=./artifacts/config.json`.

If desired, all configuration options can be provided as command line flags, instead of through a JSON file. An [example script](https://github.com/nanos/FediFetcher/blob/main/examples/FediFetcher.sh) can be found in the `examples` folder.

When using a cronjob, we are using file based locking to avoid multiple overlapping executions of the script. The timeout period for the lock can be configured using `lock-hours`.

> [!TIP]
>
> If you are running FediFetcher locally, my recommendation is to run it manually once, before turning on the cron job: The first run will be significantly slower than subsequent runs, and that will help you prevent overlapping during that first run.

## Updating FediFetcher

It's important to stay up to with FediFetcher so you always get the latest features and bugfixes.

Please refer to the [Updating FediFetcher documentation](https://github.com/nanos/FediFetcher/wiki/Updating-FediFetcher) for more information.