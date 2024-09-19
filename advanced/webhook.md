# Webhook

To add a webhook to LubeLogger, you just have to inject the environment variable "LUBELOGGER_WEBHOOK" with the Webhook URL.

Example payload:

![](/Advanced/Webhook/a/image-1726781444936.png)

Triggers:

- Vehicle - Create/Edit/Delete
- Service Record/Repair/Upgrade - Create/Edit/Delete/Move/Adjust Odometer/Duplicate
- Odometer - Create/Edit/Delete/Adjust Odometer/Duplicate
- Fuel/Tax/Supply/Notes/Reminders - Create/Edit/Delete/Duplicate

Adding records via the API will also trigger the above webhook.
