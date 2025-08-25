# Getting Started
## Docker
The Docker Container Repository is the most reliable and up-to-date distribution channel for LubeLogger.
You need to have Docker installed and Virtualization enabled(typically a BIOS setting).

[Youtube Tutorial](https://www.youtube.com/playlist?list=PL2aZOA2wNP8tn-Py-XTF-B6nfx8l-4SwA)

You will then clone the following files onto your computer from the repository 
- docker-compose.yml(docker-compose-traefik.yml if using Traefik)

Note for Portainer: some users might run into an issue with `build: .` in the docker-compose file, this line can be safely removed if it's causing issues.

Create a file named `.env` in the same folder as the docker compose file and use the [LubeLogger Configurator](https://lubelogger.com/configure) to generate the contents for it.

Note that the environment variables `LANG` and `LC_ALL` file is what will configure locale(currency, decimal, and date formats) that LubeLogger will use. Without these environment variables LubeLogger will default to 

```
InvariantCulture
Currency: ¤ 0.00
Date: MM/dd/yyyy
Decimal: 0.00
````

See [[Environment Variables|Advanced/Environment Variables]] for additional configuration

Once you're happy with the configuration, run the following commands to pull down the image and run container.
```
docker pull ghcr.io/hargata/lubelogger:latest
docker compose up -d
```
By default the app will start listening at localhost:8080, this port can be configured in the docker-compose file.

### Kubernetes Deployment
[Helm Chart](https://artifacthub.io/packages/helm/anza-labs/lubelogger) provided by [Anza-Labs](https://github.com/anza-labs)

### Docker Manual Build(For Advanced Users)
1. Install Docker
2. Clone the repo
3. CHECK culture in .env file, default is en_US, also setup SMTP for user management if you want that.
4. Run docker build -t lubelogger -f Dockerfile .
5. CHECK docker-compose.yml and make sure the mounting directories look correct.
6. If using traefik, use docker-compose.traefik.yml
7. Run docker-compose up

### Edge-tagged Image
The `:edge` tagged Docker image may contain features that are considered experimental/not fully tested but have been merged into the main branch, use at your own risk. If you're building the Docker image manually and are cloning directly from the main branch of the repository, your local copy of the repository will contain those experimental features.

## Windows Standalone Executable
Windows Standalone Executables(EXE) are provided, and can be found under assets for the [latest release](https://github.com/hargata/lubelog/releases/latest)

![](/Installation/Getting%20Started/a/image-1727553838581.png)

To run the server, you just have to download the zip archive attached to the release, usually named LubeLogger_vNNN_win_x64.zip, extract the archive and double click on CarCareTracker.exe

Occassionally you might run into an issue regarding a missing folder, to fix that, just create a "config" folder where CarCareTracker.exe is located.

If you wish to set up SMTP when using this approach, you will have to configure the environment settings in appsettings.json located in the same folder as CarCareTracker.exe
You just have to add the MailConfig section into it, but I provided the full appsettings.json anyways as an example.
```
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.AspNetCore": "Warning"
    }
  },
  "AllowedHosts": "*",
  "UseDarkMode": false,
  "EnableCsvImports": true,
  "UseMPG": true,
  "UseDescending": false,
  "EnableAuth": false,
  "HideZero": false,
  "EnableAutoReminderRefresh": false,
  "EnableAutoOdometerInsert": false,
  "UseUKMPG": false,
  "UseThreeDecimalGasCost": true,
  "VisibleTabs": [ 0, 1, 4, 2, 3, 6, 5, 8 ],
  "DefaultTab": 8,
  "UserNameHash": "",
  "UserPasswordHash": "",
  "MailConfig": {
    "EmailServer": "",
    "EmailFrom": "",
    "UseSSL": true,
    "Port": 587,
    "Username": "",
    "Password": ""
  }
}

```
When using this approach, the default port the app will be listening on is 5000, so you will navigate to localhost:5000

### Run Executable in Background

The following steps describes how to run LubeLogger as a pseudo-service that is started whenever Windows is booted up.

Note that LubeLogger cannot run as a true Windows Service as that will break cross-platform compatibility; however, it can run in the background with similar behaviors to a Windows Service.

1. Launch `Task Scheduler` - should come with every copy of Windows
2. Create a Task, note `Hidden` and `Run whether user is logged on or not` in `General` tab

![](/Installation/Getting%20Started/a/image-1744758727023.png)

3. In `Triggers` tab, create a new trigger for `At startup`

![](/Installation/Getting%20Started/a/image-1744758748520.png)

4. In `Actions` tab, create an action to launch `path\to\lubelogger\CarCareTracker.exe` and set the `Start in` to the folder the executable is in i.e.: `path\to\lubelogger`

![](/Installation/Getting%20Started/a/image-1744758763587.png)

5. Click `Ok` to create the task, then right click on the task and click `Run`
6. LubeLogger should now run in the background

![](/Installation/Getting%20Started/a/image-1744758777847.png)

![](/Installation/Getting%20Started/a/image-1744758809425.png)

7. To stop LubeLogger, right click on the Task and select `End`

## Linux Baremetal
Linux executables are provided and can be found under assets for the [latest release](https://github.com/hargata/lubelog/releases/latest)

[Youtube Tutorial](https://www.youtube.com/playlist?list=PL2aZOA2wNP8tR21myT_s0T0tneoRi0vdT)

To run the Linux executable, download the zip file named LubeLogger_vNNN_linux_x64.zip, extract it and run the following commands:

```
chmod 777 ./CarCareTracker
./CarCareTracker
```

Depending on your Linux distro, locale may or may not be passed in automatically by the OS, if you receive an Invariant Locale warning, run these commands instead:

```
chmod 777 ./CarCareTracker
LANG=en_US
./CarCareTracker
```

**Note:** `chmod 777` above is only used to rule out permission quirks/issues, please restrict the permissions to the lowest acceptable level once you have verified that LubeLogger can be executed on your machine. `LANG=en_US` is an example to configure LubeLogger to use English(United States) as a locale.

## Test that It Works
Whichever path you choose, once you get the app up and running, just navigate to the IP address and port the server is listening to and you should be able to see the app
