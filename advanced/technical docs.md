# Technical Documentation

This is pretty much a list of notes and whatnot that offers the insight of how things operate under the hood(pun intended).

## Locale
Locale is decided based on either the locale defined in the .env file or if running on bare metal, the system locale. Locale should stay consistent once the LubeLogger instance is set up, switching locales on the fly can result in numerical data not being parsed properly, especially between North American/British locales that use "." as decimal separator to European locales that use "," as decimal separator.

LubeLogger supports numerical data input that uses either "," or "." as decimal separators as long as the locale is set up properly. i.e.: 18,99 will only be parsed as 18.99 if you're in a locale that uses "," as a decimal separator. Trying to parse 18,99 in an American locale will be treated as 1899.

## Max File Size Upload
Pre 1.1.3, the maximum attachment size you can upload to LubeLogger's records is 28.6MB, the reason for this is due to the [default request size limit set by .NET](https://learn.microsoft.com/en-us/iis/configuration/system.webserver/security/requestfiltering/requestlimits/), attempting to upload files larger than this will yield a 413 HTTP error and an error message on the front end.

These limits have been removed for versions post 1.1.3, if you still encounter 413 HTTP errors, it could be due to a limitation imposed by a reverse proxy such as NGINX, see below.

### Uploading Larger Files
Without upgrading to 1.1.3, there are a few approaches to uploading larger files:
1. Compressing the file into .zip archives(only works up to a certain extent).
2. Uploading the file to a different service and include the link in the Notes section.
3. Uploading the file in parts.

### Reverse Proxy(NGINX Request Limit)
On top of the Kestrel file size limits, LubeLogger might also be subjected to request size limits set by reverse proxies such as NGINX. These need to be configured separately, the default file size in NGINX is 1MB.

## Default Allowed File Formats
By default, the file selector filters out of files that aren't in the following formats
- png
- jpeg/jpg
- pdf
- xlsx/xls
- docx

However, you can always select "All Files" in the file selector and it will allow you to upload files of all formats. You can also inject the environment variable LUBELOGGER_ALLOWED_FILE_EXTENSIONS to configure your own acceptable file extensions. If the environment variable is left blank, it defaults to `.png,.jpg,.jpeg,.pdf,.xls,.xlsx,.docx`

::: danger
# Security
The following sections describes how security is handled internally.
:::

## User Credentials
User passwords are hashed using SHA256 and only stored in hashed forms for non-root users. The usernames and emails are stored in plain text. What this means is that in the event of a data breach, the user passwords are still secure since they cannot be reversed.

## Root User Credentials
Root user credentials are hashed using SHA256 for both username and password. These credentials are not stored in the database and instead are stored in a separate config json file. What this means is that in the event of a data breach, the root user credentials are still going to be very secure.

## OpenID Connect(OIDC) User Credentials
If a user registered via OIDC by logging in via the OIDC Provider and then providing a registration token, a randomized hashed password is generated on their behalf. See [[OpenID|Advanced/OpenID]]

## Email/SMTP Credentials
LubeLogger does not store SMTP credentials and in fact should NOT be responsible for storing SMTP credentials. SMTP credentials can only be injected via environment variables or appsettings.

### Why We Don't Store SMTP Credentials
Unlike user credentials which can be hashed one-way, SMTP credentials need to be encrypted and then decrypted in order to authenticate with the SMTP server, which necessitates a two-way encryption/decryption algorithm. 

LubeLogger is not, and will never be a cryptography software, as there is simply no point in tryin to roll our own cryptography algorithm when there are so many services out there that can provide peace of mind secret vaults such as Bitwarden and Hashicorp. The best practice would be to set up a secrets vault and then inject those variables into LubeLogger upon deployment.

::: warning
# Potential Scalability Issues
The following sections describes potential scalability and bottlenecking issues.
:::

## Database

LubeLogger utilizes LiteDB, a sqlite-like noSQL file-based database. Generally this is a non-issue due to how efficient the DB is at indexing, but relying on a file database means that LubeLogger can potentially be subjected to file locks and access issues if there are enough concurrent requests made to the database. 

If you find yourself needing more scalability for the database backend, consider configuring LubeLogger to utilize a [[PostgreSQL backend|Advanced/Postgres]].

## Reminder Urgencies
Reminder urgencies are calculated at every tab load. i.e.: whenever a tab is loaded in the vehicle details page, an async method retrieves the reminders, calculates their urgencies and automatically refresh past due reminders(if enabled). This can potentially present scalability issues if a vehicle has a large amount of recurring reminders.

## Recurring Taxes
Recurring taxes are checked every single time the user clicks into the vehicle details page. It retrieves and checks if any recurring tax records are past due and automatically "refreshes" them by cloning the record. This can potentially present scalability issues if a vehicle has a large amount of recurring taxes.
