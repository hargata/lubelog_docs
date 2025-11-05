# Webhook

To add a webhook to LubeLogger, you just have to add the WebHook URL in the Server Settings Configurator

Example payload:

![](/Advanced/Webhook/a/image-1735659450213.png)

Triggers:

- Vehicle - Create/Edit/Delete
- Service Record/Repair/Upgrade - Create/Edit/Delete/Move/Adjust Odometer/Duplicate
- Odometer - Create/Edit/Delete/Adjust Odometer/Duplicate
- Fuel/Tax/Supply/Notes/Reminders - Create/Edit/Delete/Duplicate

Adding records via the API will also trigger the above webhook.

## Discord Webhook

LubeLogger supports using Discord Chatrooms as a webhook as of 1.4.2, to use Discord as a webhook, change the `https://` in the beginning of the webhook URL to `discord://`

`https://discord.com/api/webhooks/...` 

will turn into 

`discord://discord.com/api/webhooks/...`

Example Discord Webhook Payload:

![](/Advanced/Webhook/a/image-1735659580169.png)
