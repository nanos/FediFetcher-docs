Running FediFetcher as a GitHub Action is probably the simplest way of running FediFetcher if you don't have Linux admin experience. You do not need any 'server' or other hardware to use GitHub Actions, as everything runs on GitHub's servers.

The disadvantage is that you have limited control over this, and that you cannot run FediFetcher more frequently than every 10/15 minutes.

**To run FediFetcher as a GitHub Action:**

1. [Get an Access Token, if you haven't done so already](https://github.com/nanos/FediFetcher/wiki/Getting-an-access-token-for-FediFetcher)
1. [Fork this repository](https://github.com/nanos/FediFetcher/fork)
2. Add your access token as a Secret:
   1.  Within your newly created fork, go to Settings > Secrets and Variables > Actions
   2.  Click New Repository Secret
      ![github actions setup](https://github.com/user-attachments/assets/eacfd716-abe7-45de-87f7-68e5c61e2912)
   3.  Supply the Name `ACCESS_TOKEN` and provide the Token generated above as Secret
3. Create a file called `config.json` with your [configuration options](https://github.com/nanos/FediFetcher/wiki/FediFetcher-configuration-options) in the repository root. **Do NOT include the Access Token in your `config.json`!**
4. Finally go to the Actions tab and enable the action. The action should now automatically run approximately once every 10 min.

> [!CAUTION]
>
> **Do not include the `access-token` from the `config.json`** when running FediFetcher as GitHub Action. When running FediFetcher as GitHub Action **ALWAYS** set the Access Token as an Action Secret, as described above. If you have accidentally saved the token in the `config.json`, consider it compromised and regenerate it immediately.

> [!NOTE]
>
> Keep in mind that [the schedule event can be delayed during periods of high loads of GitHub Actions workflow runs](https://docs.github.com/en/actions/using-workflows/events-that-trigger-workflows#schedule).

## Updating FediFetcher

It's important to stay up to with FediFetcher so you always get the latest features and bugfixes.

Please refer to the [Updating FediFetcher documentation](https://github.com/nanos/FediFetcher/wiki/Updating-FediFetcher) for more information.
