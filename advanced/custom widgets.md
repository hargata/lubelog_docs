# Custom Widgets

::: danger
# Security
This feature can expose your instance of LubeLogger to XSS and other security vulnerabilities if you don't fully understand what you are doing. We(the maintainers of LubeLogger) are not responsible for the consequences that result from utilizing this feature. Zero support will be provided. You have been warned.
:::

The Custom Widgets Feature allows users to craft widgets that consumes from the API within LubeLogger itself. Only the Root(SuperAdmin) user can modify custom widgets, but once configured it is visible to every user.

## How It Works

When LubeLogger loads the Dashboard view, it will check if there is a `widgets.html` located within the `/data` directory. If this file exists, a button with the text `Additional Widgets` will be displayed

![](/Advanced/Custom%20Widgets/a/image-1730740032073.png)

Clicking on this button will bring up a dialog/modal which will render everything in `widgets.html` (JavaScripts included)

## Configuring Custom Widgets

This feature requires the user to be comfortable with the following paradigms:
- JavaScript and jQuery syntaxes
- Consuming JSON data from API Endpoints
- Displaying data in DOM elements

To get started, Set Environment Variable `LUBELOGGER_CUSTOM_WIDGETS` to `true`

1. Navigate to the Settings tab and open up your Developer's Console(F12)
2. Run command `showCustomWidgets()`
3. You will be greeted by a warning and notice, read carefully.

![](/Advanced/Custom%20Widgets/a/image-1730740633388.png)

4. You now have access to the Custom Widgets Editor

![](/Advanced/Custom%20Widgets/a/image-1730740828897.png)

## Example Configuration

The following code sample will tally up all service, repair, and upgrade records with the custom field `Days Out of Service` and display it in the Custom Widgets window in the Dashboard

```
<script>
var apiEndpoints = [
	'/api/vehicle/servicerecords',
	'/api/vehicle/repairrecords',
	'/api/vehicle/upgraderecords'
]
var dataArray = [];
var dataEndpointsLoaded = 0;
apiEndpoints.forEach(apiUrl => { 
	$.get(`${apiUrl}?vehicleId=${GetVehicleId().vehicleId}`, function(result) {
		if (result.length > 0){
			result.map(x=> {dataArray.push(x);});
		}
		dataEndpointsLoaded++;
		checkAllDataLoaded();
	})
})
function checkAllDataLoaded() {
	if (dataEndpointsLoaded == apiEndpoints.length){
		var extraFieldName = 'Days Out of Service';
		var totalDaysOutOfService = 0;
		dataArray.filter(x=>x.extraFields.length > 0).map(x=>x.extraFields).map(x=>x.filter(y=>y.name == extraFieldName).map(x=>{totalDaysOutOfService += parseInt(x.value)}));
		$("#daysOutOfServiceLabel").html(totalDaysOutOfService);
	}
}
</script>
<div class="modal-header">
<h5 class="modal-title">Additional Widgets</h5>
<button type="button" class="btn-close" onclick="hideCustomWidgetsModal()" aria-label="Close"></button>
</div>
<div class="modal-body" style="max-height:50vh; overflow-y:auto;">
	<div class="row row-cols-1 row-cols-md-3 g-4 justify-content-center">
		<div class="col text-center">
			<span class="lead">Day(s) Out of Service</span><br/>
			<span id="daysOutOfServiceLabel" class="display-7"></span>
		</div>
	</div>
</div>
```

![](/Advanced/Custom%20Widgets/a/image-1730740764919.png)
