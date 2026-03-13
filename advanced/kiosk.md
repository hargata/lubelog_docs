# Kiosk

## Kiosk View
Navigating to `https://yourlubeloggerdomain/kiosk` will bring up the Kiosk view.

If [[Web Socket|Advanced/Webhook#websocket]] is enabled, this is a real-time dashboard, otherwise it falls back to refreshing every 60 seconds.

By default(without any parameters), it will default to the Vehicle view.

![](/Advanced/Kiosk/a/image-1730648591244.png)

Modify view by adding `kioskMode` to the URL, such as: `https://yourlubeloggerdomain/kiosk?kioskMode={mode}`

Possible views:
- Vehicle - shows overview information of vehicles.
- Plan - shows all plans for vehicles, sorted by the priority and progress.
- Reminder - shows all reminders for vehicles, sorted by urgency.
- Cycle - cycles through all of the view above.

## Excluding Vehicles

By default, the dashboard will display all vehicles the user has access to; however, vehicles can be excluded by appending `exclusions` to the URL, such as `https://yourlubeloggerdomain/kiosk?exclusions={vehicleIds}`

The vehicleId refers to the Id of the vehicle, visible in the address bar when viewing details for a specific vehicle, e.g.:

![](/Advanced/Kiosk/a/image-1730649089838.png)

In the example above, the vehicleId is `1`. To exclude multiple vehicles, list them separated by `,` 

e.g.: `https://yourlubeloggerdomain/kiosk?exclusions=1,3,5` will exclude vehicles with Ids 1, 3, and 5 from having their information displayed on the view.

## Full URL Example

`https://yourlubeloggerdomain/kiosk?kioskMode=Cycle&exclusions=1,3,5` will cycle through different views and exclude data from vehicle Ids 1, 3, and 5.

## Setting Access Token

If your use-case for the Kiosk involves a full-time display, you will need to set up an access token as the user session cookie set by LubeLogger expires in either 24 hours or 7 days(depending if `Remember Me` was selected during Login). Setting up an access token allows the kiosk to continue functioning even if the user session has long expired.

1. Generate a readonly [[API Key|Advanced/API#api-keys]]
2. You will need to login at least once before navigating to your Kiosk URL
4. Open up the developer's console(F12 on most browsers)
5. Some browsers will require you to acknowledge what you're doing.
6. Type in `setAccessToken('{API Key you generated in step 1}')`
7. Hit enter and you should get a response stating the access token was set.

E.g.: If the generated API key is `abcde` You would then type in `setAccessToken('abcde')` in the developer's console.

Test this by navigating to your LubeLogger instance in a different tab and logging out. Your kiosk dashboard should continue functioning.
