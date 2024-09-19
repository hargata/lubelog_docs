# Reminders

Reminders are future tasks where the urgency are based on how close the user is to the due date or odometer reading.

![](/Records/Reminders/a/image-1726780085550.png)

## Adding Reminders
Reminders can either be added directly on the Reminders tab by clicking the "Add Reminder" button or via adding a new [[Service/Repair/Upgrade Record|Records/Service Records#adding-reminders]].

## Reminder Metrics
Similar to the maintenance schedule outlined in your vehicle's user manual, the urgency of a Reminder can be set either via a due date, a future odometer reading, or whichever comes first.

![](/Records/Reminders/a/image-1726780090370.png)

## Reminder Urgency
Depending on the metric selected, reminder urgency is calculated either via the server's current date, the max odometer reading across the Odometer/Service/Repair/Upgrade/Fuel tabs, or whichever comes first.

| Urgency    | Due Date      | Future Odometer Reading |
| ---------- | ------------- | ----------------------- |
| Not Urgent | > 30 days out | > 100 miles out         |
| Urgent     | < 30 days out | < 100 miles out         |
|  Very Urgent          |     < 7 days out         |        < 50 miles out                 |
|   Past Due         |   > 0 days past            |     > 0 miles past                    |

The Root User can also set up custom reminder urgency thresholds in the Settings tab

![](/Records/Reminders/a/image-1726780097886.png)

## Recurring Reminders
Reminders can be set to become recurring so that you don't have to create a new reminder for recurring maintenance such as oil changes. When you have completed the task set by the reminder, you can either have it automatically refresh when it lapses or by manually refreshing it. Refreshing a reminder effectively pushes out the due date or the odometer reading based on the recurring interval, i.e.: if a Reminder is due at 10000 miles and the interval is set at every 5000 miles, refreshing the Reminder will push the future odometer reading out to 15000 miles.

### Automatically Refresh Past Due Reminders
There is a setting within the Settings tab that allows users to automatically refresh past due reminders. Note that with this setting enabled, any reminder that becomes Past Due will be automatically refreshed, this requires a lot of diligence from the user to heed their reminders and stay on top of it.

![](/Records/Reminders/a/image-1726780105434.png)

### Manually Refresh Reminders
When a recurring reminder falls into Very Urgent or Past Due status, there will be a button on the Reminders page that will allow the user to manually refresh the reminder.

![](/Records/Reminders/a/image-1726780113529.png)

This reminder is set to be recurring every 1 year, so when the "Done" button is clicked, it will push the due date of this reminder to 1/31/2025.

![](/Records/Reminders/a/image-1726780128504.png)

## Reminder Emails
If SMTP is configured within LubeLogger, the Root User can set up a cron / scheduled task that runs at an interval to send out emails to collaborators of vehicles with reminders. The API endpoint allows the user to specify what level of urgencies should the user be notified of.

Sample bash script: https://github.com/hargata/lubelog_scripts/blob/main/bash/sendreminders.sh

The sample provided above will send email reminders out for reminders of all urgencies.

## Shop Calendar
The shop calendar accessible on the homepage allows users to view all reminders with date metrics in a calendar view.

![](/Records/Reminders/a/image-1726780138036.png)

Clicking on the individual reminder item brings up a simplified, readonly prompt displaying additional information for the reminder. If it's a recurring reminder, you will also have to option to postpone / mark the reminder as done if it's in either past due or very urgent status.

![](/Records/Reminders/a/image-1726780142496.png)

### Inconsistent Reminder Urgency
This tends to happen with reminders that have both a date and odometer metric. Since the Calendar is only concerned about the date metric, it calculates the urgency of the reminder based solely on the date metric. Which means that a reminder can be in "Very Urgent" status when viewed in the Reminders tab but is displayed as "Urgent" in the Calendar.
