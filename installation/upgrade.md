# Upgrade Guide

Comprehensive upgrade guide for Docker and Standalone Windows/Linux Executables.

Regardless of how your LubeLogger instance is installed/configured, we highly recommend that you create a backup before updating, it will take less than two minutes of your time and save you a lot of headache if something goes wrong.

## Create A Backup

### Manual Method

Login as the root/superuser to your LubeLogger instance, navigate to the Settings tab and create a backup

![](/Installation/Upgrade/a/image-1735849586472.png)

A zip file will be downloaded to your computer.

### Automated Method

Use a script to hit the API endpoint for creating backups, see [[API|Advanced/API#example-use-cases]]

You can automate the script using a cron job to create daily or weekly backups.

## Docker

1. Create a backup
2. Verify your Docker Volumes
3. Run the command `docker compose pull`
4. The, run the command `docker compose up` to start the container

If your Docker Volumes are bound and persisted correctly, you should have no loss of data.

## Windows/Linux Standalone

1. Create a backup
2. Download the latest version of LubeLogger from the Release section
3. Extract the archive over your existing LubeLogger installation.
4. Restore the backup if there is data loss
