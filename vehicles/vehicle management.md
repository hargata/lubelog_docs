# Vehicle Management

## Adding a Vehicle
To add a vehicle, simply click on the green "+" button in the "Garage" tab. A dialog will then prompt you for the following details of the vehicle you wish to add: Year, Make, Model, License Plate, and optionally, a picture of the vehicle. If it's an Electric Vehicle, you should check the "Electric Vehicle" switch. This ensures that "fuel" economy is measured in kWh instead of gallons or liters.

![](/Vehicles/Vehicle%20Management/a/image-1726782172201.png)

Once you're done, click "Add New Vehicle" and the vehicle will now be visible in the Garage Tab.

![](/Vehicles/Vehicle%20Management/a/image-1726782176398.png)

### Purchase and Sold Information
These optional fields are used to calculate duration of ownership as well as any depreciation or appreciation costs. For length of ownership, you must provide a Purchase Date, if Sold Date was not provided, LubeLogger will calculate the amount of days between the current day and the Purchase Date as length of ownership. If both Purchase and Sold Costs are provided, LubeLogger will calculate any depreciation / appreciation costs as well as the cost per mile and cost per day. These data will show up in the Vehicle Maintenance History Report under its own section.

![](/Vehicles/Vehicle%20Management/a/image-1726782180243.png)

### Odometer Adjustments
Odometer Adjustments are conversions that will be applied to the odometer field when **adding** a new Service/Repair/Upgrade/Fuel Record.

![](/Vehicles/Vehicle%20Management/a/image-1726782183928.png)

#### Odometer Multiplier
The multiplier that will be applied on the record's odometer field. Primarily used for vehicles where the odometer uses a different unit compared to the user's settings. E.g.: A user residing in the U.S. or U.K. which uses miles as the distance unit imports a vehicle that uses kilometers(Kei trucks, motorcycles, etc). 

The user will have to enter 0.621 as the odometer multiplier to convert kilometers to miles. When the user creates a new record, they can just enter the reading off the odometer in the vehicle(i.e.: 15000 km) and the app will automatically convert it to 9315 miles when the record is being saved. In the opposite scenario where a user imports a vehicle with miles as its distance and they use kilometers by default, they will have to enter 1.609 as the odometer multiplier.

Note that this field has a limit of 3 decimal places.

#### Odometer Difference
This is primarily used for vehicles where the dash cluster was swapped out and hence the odometer no longer reflects actual mileage. E.g.: The user swapped out the dash cluster when their vehicle had 200000 miles but the new dash cluster only has 15000 miles. The user will have to enter 185000 as the odometer difference. The next time the user creates a new record, they can just enter the reading off the odometer in the vehicle(i.e.: 17500 miles) and the app will automatically add 185000 to the odometer field when the record is being saved. The user can also input negative values in here if the new dash cluster has more miles than the user's original odometer.

Note that this field only takes in whole numbers(no decimals).

Note that in the event the user has a negative odometer difference, the record will not save if the odometer field falls below 0 after applying the odometer difference, it will throw a validation error.

#### Odometer Difference and Multiplier Combined(Edge Case)
The app will always apply the odometer difference first before applying the multiplier. Therefore if a dash cluster swap was performed the user must input the converted odometer difference.

### Sorting Vehicles
To sort vehicles by Year, simply right click on the Garage tab while the tab is selected.

On mobile, make sure the Garage tab is selected and long hold on the garage menu button.

## Editing a Vehicle
To edit an existing vehicle, go into the vehicle details by clicking on the vehicle tile in the Garage. If you're on a computer/tablet, there will be a yellow button on the top right of the screen, click it to edit details regarding the vehicle.

![](/Vehicles/Vehicle%20Management/a/image-1726782194546.png)

On mobile devices, the "Edit Vehicle" button is available within the menu

![](/Vehicles/Vehicle%20Management/a/image-1726782199623.png)

## Deleting a Vehicle.
To delete an existing vehicle, click on the "Manage Vehicle" dropdown and select "Delete Vehicle". You will then be prompted for confirmation before the vehicle is deleted. Once the vehicle is deleted, you will be redirected back to the Garage.

![](/Vehicles/Vehicle%20Management/a/image-1726782209700.png)

On mobile devices, the "Delete Vehicle" button is available within the menu, located at the very bottom.

![](/Vehicles/Vehicle%20Management/a/image-1726782216539.png)

## Collaborators

If more than one individual logs records to your vehicle(e.g.: spouse, employee, etc) and they have their own user account with LubeLogger, you can add them as a collaborator.

### Adding a Collaborator

To add new collaborator, simply navigate to the Dashboard tab in the vehicle details view and look to the bottom right:

![](/Vehicles/Vehicle%20Management/a/image-1726782223006.png)

Click on the blue Add User icon on the top left of the Collaborators panel and you will be prompted to type in their username, note that a user with that username must exist in the system or you will get an error.

![](/Vehicles/Vehicle%20Management/a/image-1726782230259.png)

Once you have added them as a collaborator, their name will now show up in the Collaborators list, and you will also be given the option to remove them.

![](/Vehicles/Vehicle%20Management/a/image-1726782235900.png)

Once this is done, you should have the new collaborator refresh their browser and they should be able to see the vehicle in their Garage.

### Copying Collaborators

To copy collaborators from one vehicle to another, simply navigate to the garage tab, drag and drop the vehicle you wish to copy the collaborators from onto the vehicle you wish to copy collaborators to. You will be prompted for confirmation and the collaborators will be copied over.

![](/Vehicles/Vehicle%20Management/a/image-1726782240868.png)
