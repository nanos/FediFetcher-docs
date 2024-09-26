Running FediFetcher as a Scheduled Task in Windows is an option if you are a Windows User and your main device is (almost) always running.

## Install Python and PIP

FediFetcher requires Python 3 to run, and `pip` to manage dependencies. If you already have these installed, you should skip this section.

The best way to install Python on Windows is by downloading the official Python installer from the Python website at https://www.python.org/downloads/

After the Python installer file has finished downloading, launch it by double-clicking on it in order to begin the installation. Be sure to select, make sure the "Add python.exe to PATH".

![Python installer](https://github.com/user-attachments/assets/bb0257df-ff2d-4918-ae05-15a829559151)

Once install is finished, open the Windows Command Prompt by launching `cmd.exe`, type `pip` and hit Return. You should get the generic PIP help dialogs. If it shows an error, go through install processes again and make sure you choose to in Add Python to Path.

## Install FediFetcher

It is recommended to install FedFetcher using Git. This simplifies updating to the latest version.

This guide assumes you are installing FediFetcher at `C:\FediFetcher`. If you install it elsewhere, you need to adjust your paths throughout this document.

1. Install [Git for Windows](https://git-scm.com/download/win), if you don't already have it installed.
2. Open the Windows Command prompt to `C:\`
3. Download FediFetcher: 
   ```bash
   git clone https://github.com/nanos/FediFetcher
   ```
4. Change into the FediFetcher directory: 
   ```bash
   cd FediFetcher
   ```
5. Install depdendencies: 
   ```bash
   pip install -r requirements.txt
   ```

## Configure FediFetcher

1. [Get your Access Token](https://github.com/nanos/FediFetcher/wiki/Getting-an-access-token-for-FediFetcher), if you haven't already done so.
1. Create your configuration file at `C:\FediFetcher\artifacts\config.json`
2. Paste your desired [configuration options](https://github.com/nanos/FediFetcher/wiki/FediFetcher-configuration-options)

## Initial run

It's best to run FediFetcher once before you set it up on a schedule:

```bash
.\find_posts.py -c=.\artifacts\config.json
```

Make sure everything is working, and you don't encounter any errors. This first run may take several hours to complete, so be patient.

## Setup FediFetcher to run on a schedule via Task Scheduler

1. Open Task Scheduler by pressing the Windows key, typing 'Task Scheduler', and pressing Enter.
2. On the far right, choose 'Create basic task.'
3. Choose a name (e.g. FediFetcher), and optionally, enter a description so down the road you know what the task is about. Click next
4. For trigger choose 'When the Computer Starts.' Click Next.
5. Now, choose the Action. Select 'Start a Program.' Click Next.
6. In the Program/script box, put `C:\FediFetcher\find_posts.py`. Now add arguments. `c=.\artifacts\config.json`. It's important to start in `C:\FediFetcher`. Now click Next.<br>
   ![FediFetcher Scheduled Task setup](https://github.com/user-attachments/assets/b64a6c0f-40e0-487b-8f16-e0ac1e9d6a2f)
7. On the final screen double check your command, and be sure to tick "Open the properties dialog" as we need to set how often FediFetcher will run. Click 'Finish'.<br>
   ![Final confirmation dialog](https://github.com/user-attachments/assets/d2d25c42-6ad1-4c06-9947-763c9d7cb846)
8. On the 'Triggers' tab, select 'At Startup' and 'Edit'.<br>
   ![image](https://github.com/user-attachments/assets/eb280bf6-91cb-407f-9c31-fafc89aa0734)
9. Tick 'Repeat Task Every' and select your frequency (e.g. every 15 minutes). Change duration to 'Indefinitely'. Click 'OK'.<br>
   ![image](https://github.com/user-attachments/assets/2102fe61-11a6-4929-a3b5-0de0bb455f1b)

FediFetcher is now set up to run as a Scheduled Task. You can right click the task to run it now or the next time you restart your computer, it will be set to run on a schedule.

## Updating FediFetcher

It's important to stay up to with FediFetcher so you always get the latest features and bugfixes.

Please refer to the [Updating FediFetcher documentation](https://github.com/nanos/FediFetcher/wiki/Updating-FediFetcher) for more information.