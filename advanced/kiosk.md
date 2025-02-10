# Kiosk

## Kiosk View
Navigating to `https://yourlubeloggerdomain/kiosk` will bring up the Kiosk view. This is a pseudo real-time dashboard that refreshes approximately every minute(indicated by the progressbar at the very top of the page)

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

1. Ensure that your user's password does not contain `:` in it
2. Encode `{yourusername}:{yourpassword}` in Base64
3. You will need to login at least once before navigating to your Kiosk URL
4. Open up the developer's console(F12 on most browsers)
5. Some browsers will require you to acknowledge what you're doing.
6. Type in `setAccessToken('{Base64 Encoded token generated in step 2}')`
7. Hit enter and you should get a response stating the access token was set.

E.g.: If the username is `test` and the password is `1234` the base64 encoded token would be `dGVzdDoxMjM0` You would then type in `setAccessToken('dGVzdDoxMjM0')` in the developer's console.

Test this by navigating to your LubeLogger instance in a different tab and logging out. Your kiosk dashboard should continue functioning.
