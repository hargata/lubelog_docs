# Frequently Requested Feature Requests

This page contains a list of frequently requested feature requests for features that already exist in LubeLogger. If you create a feature request for a feature that already exists in this list your ticket will be closed with a comment that links to this page with no further explanation.

>| ### Change Wording on Buttons
>|
>| Create your own translation file and you can change the wording to whatever you like. See [[Translations|Misc/Translations]]

>| ### Notification for Reminders
>|
>| This can be accomplished by setting up a cron job for the send reminders API endpoint. When the API endpoint is hit all collaborators will receive an email. If a Default Reminder Email is configured, it will also be included as a recipient for all reminder emails. See [[Reminder Emails|Records/Reminders#reminder-emails]]
>| There are currently no plans to send out a notification the moment a reminder becomes due.

>| ### Imported Vehicle with Different Odometer Unit
>|
>| If you have an imported vehicle with different odometer units(i.e.: Kei trucks using KM in the US which uses Miles), you can configure the vehicle level Odometer Multiplier which will automatically adjusts all odometer inputs from your vehicle into your current units(i.e.: KM to Miles by multiplying the odometer input with 0.621) See [[Odometer Multiplier|Vehicles/Vehicle%20Management#odometer-multiplier]]

>| ### Display KM/L instead of L/100KM
>|
>| This is user-configurable, see [[Alternate Fuel Units|Records/Fuel%20Records#alternate-fuel-units]]

>| ### Add Support for Foreign Locale
>|
>| LubeLogger supports whichever locale is installed onto your system, please see [[Docker Installation|Installation/Getting%20Started#docker]] and [[Troubleshooting Locale Issues|Installation/Troubleshooting#locale-issues]]
