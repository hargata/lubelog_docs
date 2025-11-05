# Troubleshooting
Common issues and steps you can take to fix them.

## General Issues

>| ### Feature(s) Stopped Working After Updating to Latest Version
>| Your browser might have cached an older version of a JavaScript(JS) file which is no longer compatible with the current version of LubeLogger. Try the following steps:
>| 
>| 1. Verify - Try navigating to LubeLogger in Incognito mode or on another device
>| 2. If everything functions as expected in Incognito, you have a caching issue.
>| 3. Clear your browser's cache or perform a hard reload(hit CTRL+SHIFT+R multiple times on most browsers)
>| 4. Check if the site works as intended on the [demo site](https://demo.lubelogger.com)

>| ### Can't Send Email via SMTP
>| Note that for most email providers, you can no longer use your account password to authenticate and must instead generate an app password for LubeLogger to be able to authenticate on your behalf to your email provider's SMTP server.

>| #### Gmail SMTP Authentication Error
>| 
>| Use port 587 instead of 465, LubeLogger only supports TLS.

>| ### Console shows Authentication Errors
>| 
>| Those are purely informational, add this line in your environment variables to prevent information logs from showing up in the console.
>| 
>| `LOGGING__LOGLEVEL__DEFAULT=Error`

>| ### Data Missing after Update to Latest Version
>|
>| You didn't persist your docker volumes for, check your docker-compose file. All your data should still be there however, they might just be anonymous volumes that you have to re-link back to the container.

## Locale Issues

>| ### Can't input values in "," format / shows up as 0.
>| 
>| Ensure that your locale is configured correctly in the Server Settings Configurator

>| ### Locale Not Updating/¤ Currency Symbol/Date Format Issues
>| 
>| You will need to restart the docker container/executable after configuring locale

## Postgres Issues

>| ### Schema Does Not Exist
>| 
>| Make sure that there is a schema named "app" in the database as specified in the Postgres connection string. For more information, see [[Postgres|Advanced/Postgres]]

## OpenID Connect(OIDC) Issues

>| ### No Option to Login via OIDC
>| 
>| Make sure Authentication is enabled, check "Enable Authentication" in Settings tab and set up root user credentials

>| ### Logging-in via OIDC Requires Token
>| 
>| LubeLogger operates on an invite-only basis, a token will need to be generated for the user logging in via OIDC if it is their first time. Once an account for the user exists they will no longer be prompted for the token in subsequent login attempts.

>| ### No Auto-Redirect to OIDC Provider
>| 
>| A LogOutURL must be provided for the OIDC provider otherwise the OIDC login flow will not be auto-initiated.

>| ### Expected id_token, received {...}
>| 
>| Add `openid` to the OpenIDConfig__Scope environment variable

>| ### Issues with OpenID Provider
>| 
>| If none of the above troubleshooting steps worked, the problem might exist on the OpenID Provider side of things, LubeLogger has a built-in OpenID debugger which can be used to identify what key information might be missing from the OpenID Provider's Authorization Response. See [[Advanced Troubleshooting|Advanced/OpenID#advanced-troubleshooting]] for more information.

## Server Issues

>| ### ERR_TOO_MANY_REDIRECTS
>| 
>| If you encounter this error in your browser while attempting to navigate to your LubeLogger instance and it is accompanied by the following console error in your Docker Container:
>| 
>| `The configured user limit (128) on the number of inotify instances has been reached`
>| 
>| You have reached the maximum limit of file watchers across all your Docker Containers. In LubeLogger, file watchers are crucial for detecting changes to configuration files. To fix this, you will need to increase the inotify limit above 128.

## API Issues

>| ### Input Object Invalid
>| 
>| This error is either caused by a missing field in the input object or if the API client is passing the payload in as json. If all fields are already provided, check and make sure that the payload is passed in as either form-data or x-www-urlencoded

>| ### Can't Access LubeLogger Instance from Other Devices
>| 
>| This problem is specific to the Windows Standalone Executable, the problem stems from the fact that Kestrel is configured by default to listen on and only on localhost. In order to get around this, you will need to retrieve the IPv4 address of your local machine, and add configure the HTTP Endpoint via the Server Settings Configurator. Additionally, see [[Setting up HTTPS|Advanced/HTTPS]] for HTTPS/SSL Cert Configuration

### NGINX / Cloudflare 
LubeLogger is a web app that runs on Kestrel, it literally doesn't matter if it's deployed behind a reverse proxy or Cloudflare tunnel. As long as the app can receive traffic on the port it's configured on, it will run.

Here's a sample Nginx reverse proxy configuration courtesy of [thehijacker](https://github.com/thehijacker)
```
server
{
    listen 443 ssl http2;
    server_name lubelogger.domain.com;

    ssl_certificate /etc/nginx/ssl/acme/domain.com/fullchain.pem;
    ssl_certificate_key /etc/nginx/ssl/acme/domain.com/key.pem;
    ssl_dhparam /etc/nginx/ssl/acme/domain.com/dhparams.pem;
    ssl_trusted_certificate /etc/nginx/ssl/acme/domain.com/fullchain.pem;

    location /
    {
        proxy_pass http://192.168.28.53:8289;
        client_max_body_size               50000M;
        proxy_set_header Host              $http_host;
        proxy_set_header X-Real-IP         $remote_addr;
        proxy_set_header X-Forwarded-For   $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
        proxy_http_version 1.1;
        proxy_set_header   Upgrade    $http_upgrade;
        proxy_set_header   Connection "upgrade";
        proxy_redirect off;
    }
}
```

#### Troubleshooting Issues with Reverse Proxies

No support will be rendered by the maintainers for issues relating to reverse proxies because we are not going to spin up an instance of a reverse proxy with similar or identical configuration to yours just to figure out what's wrong. Any issues submitted on GitHub related to reverse proxies will be assigned an `unsupported` label, the issue will remain open for 15 days for others to chime in, and then it will be closed regardless of whether the issue is resolved or not.
