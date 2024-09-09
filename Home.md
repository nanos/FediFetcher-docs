This wiki outlines how to run and configure FediFetcher.

1. Regardless of how you want to run FediFetcher, you must first get an access token:<br>
   [Getting an Access Token for FediFetcher](https://github.com/nanos/FediFetcher/wiki/Getting-an-access-token-for-FediFetcher)

2. Once you have to your access token, there are multiple ways of running FediFetcher. None of these require you to have CLI/SSH access to your mastodon server. These include, but aren't limited to:<br>

-  [Running FediFetcher as a GitHub Action](https://github.com/nanos/FediFetcher/wiki/Running-FediFetcher-as-a-GitHub-Action)<br>
   Ideal if you don't have your own hardware, and/or have little experience running servers. This is all point and click within GitHub's interface.
- [Running FediFetcher as a cron job](https://github.com/nanos/FediFetcher/wiki/Running-FediFetcher-as-a-cron-job)<br>
   Ideal if you already have a linux device, and want to simply run FediFetcher on there.
- [Running FediFetcher from a container](https://github.com/nanos/FediFetcher/wiki/Running-FediFetcher-from-a-container)<br>
   Ideal if you are familiar with containers.
- [Running FediFetcher as a systemd timer](https://github.com/nanos/FediFetcher/wiki/Running-FediFetcher-as-a-systemd-timer.)<br>
   Ideal if you have a linux device somewhere, but don't like cron jobs.
- Running FediFetcher as a Scheduled Task in Windows<br>
   Ideal if you are a Windows User and your main device is (almost) always running.

3. To find all available configuration options, read [FediFetcher configuration options](https://github.com/nanos/FediFetcher/wiki/FediFetcher-configuration-options)