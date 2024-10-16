# Getting Started
## Docker
The Docker Container Repository is the most reliable and up-to-date distribution channel for LubeLogger.
You need to have Docker installed and Virtualization enabled(typically a BIOS setting).

[Youtube Tutorial](https://www.youtube.com/playlist?list=PL2aZOA2wNP8tn-Py-XTF-B6nfx8l-4SwA)

You will then clone the following files onto your computer from the repository 
- docker-compose.yml(docker-compose-traefik.yml if using Traefik)

Create a file named `.env` in the same folder as the docker compose file and use the [LubeLogger Configurator](https://lubelogger.com/configure) to generate the contents for it.

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

## Linux Baremetal
Linux executables are provided and can be found under assets for the [latest release](https://github.com/hargata/lubelog/releases/latest)

[Youtube Tutorial](https://www.youtube.com/playlist?list=PL2aZOA2wNP8tR21myT_s0T0tneoRi0vdT)

To run the Linux executable, download the zip file named LubeLogger_vNNN_linux_x64.zip, extract it and run the following commands:

```
chmod 777 ./CarCareTracker
./CarCareTracker
```

## Test that It Works
Whichever path you choose, once you get the app up and running, just navigate to the IP address and port the server is listening to and you should be able to see the app
