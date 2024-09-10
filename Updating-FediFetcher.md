It's really important to stay up to with FediFetcher so you always get the latest features and bugfixes. 

## Getting notified of new releases.

You may subscribe to new releases using GitHub's 'Watch' feature:

1. Navigate to the [FediFetcher repository](https://github.com/nanos/FediFetcher)
2. In the top bar click 'Watch' then 'Custom'<br>
<img width="462" alt="image" src="https://github.com/user-attachments/assets/6c4b9612-59df-4f01-b2fe-ec0651f0bd2a">
3. Tick 'Releases' then press 'Apply'<br>
<img width="446" alt="image" src="https://github.com/user-attachments/assets/3aadaf2c-afb8-497a-9124-23c51c4ecc6f">

You should now get an email for every new release.

How you update depends on how you are running FediFetcher:

## Update your GitHub Action

Simply navigate to your fork of FediFetcher, then click 'Sync Fork', and then 'Update Branch':

<img width="928" alt="image" src="https://github.com/user-attachments/assets/976bc500-910c-4776-ba5a-d8b983bd58f1">

## Update FediFetcher, if running as a cron job

1. Update your copy of FediFetcher:
   ```bash
   git pull
   ```
2. Update your dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## Upate FediFetcher, if running as a system timer:

1. Navigate to your FediFetcher directory:
   ```bash
   cd /opt/FediFetcher
   ```
3. Update your copy of FediFetcher:
   ```bash
   git pull
   ```
4. Update your dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## Update FediFetcher, if running as a Windows Scheduled Task:

1. Open your command prompt
2. Navigate to `C:\FediFetcher`
3. Update your copy of FediFetcher:
   ```bash
   git pull
   ```
4. Update your dependencies:
   ```bash
   pip install -r requirements.txt
   ```