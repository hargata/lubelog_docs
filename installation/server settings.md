# Configuring Server Settings

The Server Settings Configurator allows you to configure server-wide settings such as Postgres, Locale, SMTP, OIDC, etc.

You can access the Server Settings Configurator from within the Settings tab or via `/setup` 

![](/Installation/Server%20Settings/a/image-1759526061777.png)

## Skipped Settings

Server settings are saved in `/data/config/serverConfig.json` and are included in the backups created in the Settings tab.

![](/Installation/Server%20Settings/a/image-1759526684792.png)

Certain settings such as the Postgres connection string, have a "Skip" option. Check this for settings that you want to be injected via Environment Variables and it will not save the specific setting within the `serverConfig.json` file.

## Locale Overrides

This is the primary way of configuring locale in LubeLogger and serves as an alternative to injecting LANG and LC_ALL in the environment variables. It allows you to set a locale that LubeLogger uses along with a date override. This will allow you to mix and match different locales and their date formats i.e.: using en-US locale for currency and number formats but you wish to use ISO-8601(yyyy-MM-dd) for date formats instead of MM/dd/yyyy

![](/Installation/Server%20Settings/a/image-1759526492218.png)

Changing locale settings will require LubeLogger to be restarted, for docker this means restarting the container, for Windows/Linux executable this means closing out the console app and re-opening it.

## SMTP

You can configure and test the SMTP settings within the Server Settings Configurator

![](/Installation/Server%20Settings/a/image-1759526761383.png)

## Root User OIDC

You can enable OIDC authentication for the Root User in the Miscellaneous section of the Server Settings Configurator

![](/Installation/Server%20Settings/a/image-1759526914056.png)

The Root User Email Address will be used to identify which email coming from the IdP will be used to authenticate the user as the Root User. This email is also used as the default reminder email address for when the `/api/vehicle/reminders/send` is called.

See [[Authentication via OIDC|Advanced/OpenID]] for more information regarding setting up OpenID Connect in LubeLogger
