# Environment Variables

These are all of the environment variables you can pass into LubeLogger and what they do

> [!NOTE]
> Save time and effort using the [LubeLogger Configurator](https://lubelogger.com/configure)
> to generate your .env file

```
LC_ALL=en_US.UTF-8 <- Locale and Language Settings, this will affect how numbers, currencies, and dates are formatted.
LANG=en_US.UTF-8 <- Same as above. Note that some languages don't have UTF-8 encodings.
MailConfig__EmailServer="" <- Email SMTP settings used only for configuring multiple users(to send their registration token and forgot password tokens)
MailConfig__EmailFrom="" <- Same as above.
MailConfig__Port=587 <- Same as above.
MailConfig__Username="" <- Same as above.
MailConfig__Password="" <- Same as above.
POSTGRES_CONNECTION="" <- Postgres Connection String
OpenIDConfig__Name=Name of the OpenID Connect Provider
OpenIDConfig__ClientId=Client Id to Authenticate with the Provider
OpenIDConfig__ClientSecret=Client Secret to Authenticate with the Provider
OpenIDConfig__AuthURL=Authorization URL to the Provider's Login Page
OpenIDConfig__TokenURL=URL to retrieve user JWT from the Provider
OpenIDConfig__RedirectURL=https://<yourlubeloggerdomain.com>/Login/RemoteAuth(must be HTTPS)
OpenIDConfig__Scope=The scope for retrieving the user's email claim(usually it's just 'email')
OpenIDConfig__ValidateState=true/false(default: false) - whether LubeLogger should validate state.
OpenIDConfig__UsePKCE=true/false(default: false) - whether LubeLogger should use PKCE
EnableAuth=true/false(default: false) - Allows users to configure whether if authentication is enabled via environment variable.
UserNameHash="" - SHA256 Hash of the root username.
UserPasswordHash="" - SHA256 Hash of the root password.
LUBELOGGER_ALLOWED_FILE_EXTENSIONS="" - Allowed file extensions for document uploads, use '*' to allow all file types.
LUBELOGGER_LOGO_URL="" - Custom Logo URL.
LUBELOGGER_MOTD="" - Message of The Day displayed in Login page if configured.
LUBELOGGER_WEBHOOK="" - WebHook URL
LUBELOGGER_CUSTOM_WIDGETS=true/false(default: false) - Allow Custom Widgets to be configured
LUBELOGGER_INVARIANT_API=true/false(default: false) - whether API response should be invariant
LUBELOGGER_OPEN_REGISTRATION=true/false(default: false) - Allow users to generate their own registration token
```
