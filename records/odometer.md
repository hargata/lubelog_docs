# Odometer

The Odometer tab is where you can log your current odometer reading without having to insert any Service/Repair/Upgrade/Fuel records. This odometer readings entered in this tab allows Reminder urgencies to be calculated as accurately as possible since it uses the maximum mileage reported in each of the tabs to determine the last reported mileage.

The Odometer tab is hidden by default and must be enabled by checking the "Odometer" switch under "Visible Tabs" in the Settings tab.

## Negative Distance Values

This tends to happen when odometer records are inserted out of chronological order, to fix this, all you have to do is select all of the records, right click on them, and select "Recalculate Distance" This will update all of the initial mileages to be in a chronological order.

## API Integration
As with the other tabs, odometer readings can be retrieved via a GET endpoint and inserted via a POST API endpoint.

Example use cases:
- An app to integrate with OBDII and insert odometer reading from the vehicle's computer onto LubeLogger.
- An app to keep track of distance traveled via GPS and incrementing the last reported odometer reading.

These are not functionalities provided out of the box by LubeLogger, and are just examples of the possibilities achievable via the API endpoints.

::: warning
# Experimental Feature
Feature describe below is in an experimental phase and may not be stable or available in current release.
:::

## Trip Recorder
New in 1.3.9, an experimental feature to tap into the users devices' GPS to update odometer and record routes while driving.

This feature requires the LubeLogger instance to be served via **HTTPS** to a device with a browser that supports **Geolocation** and **Wakelock API**. When a trip is being recorded, the app will prevent the screen/device from going to sleep, and will retrieve the user's coordinates every 5 seconds. 

This feature is not available for vehicles using engine hours instead of miles or kilometers for distance unit.

You will need to enable Precise Location for your browser in order for LubeLogger to retrieve your location accurately.

In iOS:

Settings > Privacy & Security > Location Services > Safari Websites > Precise Location

In Android(Depends on Device Manufacturer):

Settings > Location > App Location Permissions > Chrome > Precise Location

### Recording a Trip
Onec you have all the configurations above enabled, when you click on "Add Odometer Record", you will now see a red record button right next to the "Increment Odometer" button

![](/Records/Odometer/a/image-1729524292930.png)

Click on the record button and you will be taken to record trip modal:

![](/Records/Odometer/a/image-1729524325573.png)

Read the Disclaimer. Click "Start Recording" and drive around, you should see the odometer increment when you've driven about a mile or so(subject to device accuracy).

Clicking on the current odometer reading shows the sub-odometer reading. Note that the sub-odometer reading is never saved as LubeLogger does not support decimals for odometer reading. This display is purely for checking if the tracking functionality is working.

![](/Records/Odometer/a/image-1729524519130.png)

Do not close this window or exit out of the app when recording is in progress, PWAs are only allowed to query location information if it is in the foreground.

![](/Records/Odometer/a/image-1729525226080.png)

Once you are done recording your trip, click the "Stop Recording" button. If the final odometer reading is different from the initial odometer reading, then a "Save" button will be displayed:

![](/Records/Odometer/a/image-1729524758646.png)

Click "Save" and you will be brought back to the "Add Odometer Record" screen, the odometer reading field will be updated, and there will also be a file that is pending upload named "coordinates.csv". If you add this odometer record, the file will be uploaded.

![](/Records/Odometer/a/image-1729524891940.png)

The coordinates.csv file contains a list of coordinates saved from the trip in 0.1 mile or km increments. To visualize the file, simply upload it to a coordinate plotter such as GPS Visualizer and it will plot the coordinates out on a map.
