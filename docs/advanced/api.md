# API

LubeLogger provides API endpoints to retrieve and add records, full documentation of these endpoints can be found at `/api`.

## Authentication
The following authentication methods are supported:

- Basic Auth(RFC2617)
- API Keys

### Basic Auth
Basic Auth is implemented based on RFC2617, which stipulates that the "token" is passed in as a Base64-encoded string comprising of a username and password separated by a colon(":"). Because of this, neither the username nor password can contain a colon(":") character. The "token" is passed in via either through the request headers or in-line authorization for clients that support it.

Examples:

- Request Headers: `Authorization: Basic dGVzdDoxMjM0`

- In-line authorization: `https://test:1234@demo.lubelogger.com/api/calendar`

Note: Single Sign On(SSO) users should not use Basic Auth for API integrations and should instead rely on API Keys.

### API Keys
API keys are randomly-generated tokens that allow integrations to access and modify data on behalf of the user, they are equivalent to user credentials thus it is important to store them safely and only be provided to applications you trust. Unlike Basic Auth, API keys can only be used to access `/api` endpoints.

API Keys can be scoped to the following roles:
- Viewer(view only)
- Editor(view, add, and edit)
- Manager(view, add, edit, and delete)

#### Generating API Keys

![alt text](images/1773784587974-image.png)

![alt text](images/1773784625817-image.png)

![alt text](images/1773784664586-image.png)

![alt text](images/1773784691106-image.png)

![alt text](images/1773784713193-image.png)

#### Using API Keys

API keys can be passed in via request headers or appended to the URL(in-line authorization).

Examples:

- Request Headers: `x-api-key: 3f757919f42548cebec90a692815e048`

- In-line authorization: `https://demo.lubelogger.com/api/vehicles?apiKey=3f757919f42548cebec90a692815e048`

## POST/PUT Encoding
As of 1.4.2, LubeLogger supports bodies in both form-data, x-www-form-urlencoded, and JSON format.

Note that form-data and x-www-form-urlencoded will always convert any data into strings even if you are passing in a number. Post bodies in JSON if you wish to pass in numbers and integers.

## Locale-Invariant Formatting
By default, LubeLogger will return all data as strings for GET methods and it is locale-sensitive:

![alt text](images/1773784732157-image.png)

Note the date and decimal formatting.

If you wish for locale invariant and type-rich formatting(numbers are returned as numbers instead of string), you can either inject the following environment variable:

`LUBELOGGER_INVARIANT_API=true`

Or add the following Header Key in your API request:

`culture-invariant`

No values are needed, the presence of the key is sufficient for LubeLogger to format the API response:

![alt text](images/1773784750450-image.png)

## GET Parameters
As of 1.4.8, you can now pass in additional parameters to filter down results from the following GET API endpoints:

- Plan
- Odometer
- Service Record
- Repair
- Upgrade
- Fuel
- Tax

The parameters that you can pass in are:

```
Id: Id of the record
StartDate: Find records after this date (not inclusive)
EndDate: Find records before this date (not inclusive)
Tags: Find records that contains these tags(separated by white space, not applicable to Plans)
```

![alt text](images/1773784765264-image.png)

## Cleaning up Temp/Unlinked Files
The clean up endpoint: `/api/cleanup` will clear up any temp files created by LubeLogger. Adding the `deepClean=true` parameter will also clear out any unlinked attachments(files where the record it is associated with no longer exists). You need to have access to the root user credentials to access this endpoint.

## Testing
You can utilize any REST API testing tool to test your use-case.

[Postman Collection](https://github.com/hargata/lubelog_scripts/blob/main/misc/LubeLogger.postman_collection.json)

## Example Use Cases
- Send Email Reminders, see [Reminders](/Records/Reminders#reminder-emails)
- Insert Odometer Records, see [Odometer](/Records/Odometer#api-integration)
- Create DB Backups, [Example BASH Script](https://github.com/hargata/lubelog_scripts/blob/main/bash/makebackup.sh) [Example DOS Script](https://github.com/hargata/lubelog_scripts/blob/main/dos/makebackup.bat)