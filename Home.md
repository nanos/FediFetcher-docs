This documentation outlines how to run and configure FediFetcher:

1. Regardless of how you want to run FediFetcher, you must first get an access token:<br>
   [Getting an Access Token for FediFetcher](https://github.com/nanos/FediFetcher/wiki/Getting-an-access-token-for-FediFetcher)

2. Once you have to your access token, there are multiple ways of running FediFetcher. None of these require you to have CLI/SSH access to your mastodon server. Pick one of the following options:<br>

   - [Running FediFetcher as a cron job](https://github.com/nanos/FediFetcher/wiki/Running-FediFetcher-as-a-cron-job)<br>
     Ideal if you already have a linux device, and want to simply run FediFetcher on there.
   - [Running FediFetcher from a container](https://github.com/nanos/FediFetcher/wiki/Running-FediFetcher-from-a-container)<br>
      Ideal if you are familiar with containers.
   - [Running FediFetcher as a systemd timer](https://github.com/nanos/FediFetcher/wiki/Running-FediFetcher-as-a-systemd-timer)<br>
     Ideal if you have a linux device somewhere, but don't like cron jobs.
   - [Running FediFetcher as a Scheduled Task in Windows](https://github.com/nanos/FediFetcher/wiki/Running-FediFetcher-as-a-Scheduled-Task-in-Windows)<br>
     Ideal if you are a Windows User and your main device is (almost) always running.


> [!IMPORTANT]  
> Running FediFetcher as GitHub Action is deprecated since May 2025. If you are running FediFetcher as GitHub Action it will cease running by 20th June.
>
> If you are currently running FediFetcher as GitHub Action please see [Migrating From GitHub Actions](https://github.com/nanos/FediFetcher/wiki/Migrating-From-GitHub-Actions) for migration details.

3. Configure FediFetcher:<br>
   FediFetcher has quite a few configuration options, so here is my quick configuration advice, that should probably work for most people:<br>   
   
   ```json
   {
     "access-token": "Your access token.",
     "server": "your.mastodon.server",
     "home-timeline-length": 200,
     "max-followings": 80,
     "from-notifications": 1
   }
   ```
  
   To find all available configuration options, read [FediFetcher configuration options](https://github.com/nanos/FediFetcher/wiki/FediFetcher-configuration-options)

4. It's really important you keep FediFetcher up to date. Please check the [Updating FediFetcher documentation](https://github.com/nanos/FediFetcher/wiki/Updating-FediFetcher), for details on how to be notified of new releases, and how to install updates.

5. Want to contribute? Amazing! Have a look at [Contribute To FediFetcher](https://github.com/nanos/FediFetcher/wiki/Contribute-To-FediFetcher)