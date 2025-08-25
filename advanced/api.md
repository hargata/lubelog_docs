# API

LubeLogger provides API endpoints to retrieve and add records, full documentation of these endpoints can be found at `/api`.

## Authentication
If authentication is enabled, it implements Basic Auth based on RFC2617, which stipulates that the "token" is passed in as a Base64-encoded string comprising of a username and password separated by a colon(":"). Because of this, neither the username nor password can contain a colon(":") character.

### In-line URL Authorization
In-line authorization is supported as of 1.4.3 as it is necessary for authorization for the calendar endpoint. Use it as so:

`https://username:password@lubeloggerdomain/api/endpoint`

For the calendar endpoint, it will look something like this:

`https://test:1234@demo.lubelogger.com/api/calendar`

## POST/PUT Encoding
As of 1.4.2, LubeLogger supports bodies in both form-data, x-www-form-urlencoded, and JSON format.

Note that form-data and x-www-form-urlencoded will always convert any data into strings even if you are passing in a number. Post bodies in JSON if you wish to pass in numbers and integers.

## Locale-Invariant Formatting
By default, LubeLogger will return all data as strings for GET methods and it is locale-sensitive:

![](/Advanced/API/a/image-1735660075138.png)

Note the date and decimal formatting.

If you wish for locale invariant and type-rich formatting(numbers are returned as numbers instead of string), you can either inject the following environment variable:

`LUBELOGGER_INVARIANT_API=true`

Or add the following Header Key in your API request:

`culture-invariant`

No values are needed, the presence of the key is sufficient for LubeLogger to format the API response:

![](/Advanced/API/a/image-1735660354711.png)

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

![](/Advanced/API/a/image-1755538298273.png)


## Testing
You can utilize any REST API testing tool to test your use-case.

[Postman Collection](https://github.com/hargata/lubelog_scripts/blob/main/misc/LubeLogger.postman_collection.json)

## Example Use Cases
- Send Email Reminders, see [[Reminders|Records/Reminders#reminder-emails]]
- Insert Odometer Records, see [[Odometer|Records/Odometer#api-integration]]
- Create DB Backups, [Example BASH Script](https://github.com/hargata/lubelog_scripts/blob/main/bash/makebackup.sh) [Example DOS Script](https://github.com/hargata/lubelog_scripts/blob/main/dos/makebackup.bat)
