# Authenticating via OpenID Connect

Configure OpenID Connect(OIDC) for LubeLogger via the following environment variables

```
OpenIDConfig__Name=Name of the OpenID Connect Provider
OpenIDConfig__ClientId=Client Id to Authenticate with the Provider
OpenIDConfig__ClientSecret=Client Secret to Authenticate with the Provider
OpenIDConfig__AuthURL=Authorization URL to the Provider's Login Page
OpenIDConfig__TokenURL=URL to retrieve user JWT from the Provider
OpenIDConfig__RedirectURL=https://<yourlubeloggerdomain.com>/Login/RemoteAuth(must be HTTPS)
OpenIDConfig__Scope=The scope for retrieving the user's email claim(usually it's just 'email')
OpenIDConfig__ValidateState=true/false(default: false) - whether LubeLogger should validate state.
OpenIDConfig__UsePKCE=true/false(default: false) - whether LubeLogger should use PKCE
OpenIDConfig__DisableRegularLogin=true/false(default: false) - auto re-direct user to OIDC login.
OpenIDConfig__LogOutURL=Log Out URL for OIDC Provider, required if DisableRegularLogin=true.
```

If you're using the Windows Standalone executable, add the following section into `appsettings.json`

```
  "OpenIDConfig": {
    "Name": "",
    "ClientId": "",
    "ClientSecret": "",
    "AuthURL": "",
    "TokenURL": "",
    "RedirectURL": "",
    "Scope": "",
    "ValidateState": true/false,
    "UsePKCE": true/false,
    "DisableRegularLogin": true/false,
    "LogOutURL": ""
  }
 ```

The following sample shows how to set up OIDC with Google as the provider with the LubeLogger instance running on `https://localhost:5011`

```
OpenIDConfig__Name=Google
OpenIDConfig__ClientId=xxx.apps.googleusercontent.com
OpenIDConfig__ClientSecret=<your Google API Client Secret>
OpenIDConfig__AuthURL=https://accounts.google.com/o/oauth2/auth
OpenIDConfig__TokenURL=https://oauth2.googleapis.com/token
OpenIDConfig__RedirectURL=https://localhost:5011/Login/RemoteAuth
OpenIDConfig__Scope=email
OpenIDConfig__ValidateState=true
OpenIDConfig__UsePKCE=false
OpenIDConfig__DisableRegularLogin=false
```

## State Validation
The ValidateState environment variable determines if LubeLogger should validate the state token echoed back by the OIDC provider. This is set to false by default, if enabled, LubeLogger will fail any login attempts where the state token is not identical to what it sent to the provider. Leave this disabled if you wish to have IdP-initiated SSO.

## Proof of KeyCode Exchange(PKCE)
The UsePKCE environment variable determines if LubeLogger should generate and pass in a SHA-256-hashed challenge code to the OIDC provider.

## Testing
Once you have all these environment variables injected correctly, you should see the ability to login via your OIDC provider. Note: Currently LubeLogger only supports one OIDC provider.

![](/Advanced/OpenID/a/image-1726781322923.png)

![](/Advanced/OpenID/a/image-1726781326911.png)

LubeLogger uses the user's email address to authenticate against a registered user, the email address provided by the OIDC provider must match the email address of the user in the system.

If the user is attempting to login via OIDC but does not have an account with LubeLogger, they will be prompted for a registration token and to set up a username which will then allow them to log in. Note that the registration token is only required for their first time logging in.
