# Sharing Vehicles

Multiple users can contribute to the same vehicles either by adding them as a collaborator or as a household member.

## Collaborators

A collaborator is best described as a co-owner of a vehicle. Collaborators have full access over the vehicle, they can add, edit and delete records, and manage collaborators by adding or deleting other collaborators. They can also delete entire vehicles.

A user is automatically added as a collaborator when they create the vehicle. 

### Managing Collaborators for a Single Vehicle

To add new collaborator, simply navigate to the Dashboard tab in the vehicle details view and look to the bottom left:

![](/Vehicles/Vehicle%20Management/a/image-1726782223006.png)

Click on the blue Add User icon on the top left of the Collaborators panel and you will be prompted to type in their username, note that a user with that username must exist in the system or you will get an error.

![](/Vehicles/Vehicle%20Management/a/image-1726782230259.png)

Once you have added them as a collaborator, their name will now show up in the Collaborators list, and you will also be given the option to remove them.

![](/Vehicles/Vehicle%20Management/a/image-1726782235900.png)

Once this is done, you should have the new collaborator refresh their browser and they should be able to see the vehicle in their Garage.

### Managing Collaborators for Multiple Vehicles

To manage collaborators for multiple vehicles, select the vehicles in the garage, right click, and select "Manage Collaborators"

![](/Vehicles/Vehicle%20Management/a/image-1760533315878.png)

If all the vehicles have the same collaborators, you will be presented with this dialog which allows you to add or delete collaborators for all selected vehicles:

![](/Vehicles/Vehicle%20Management/a/image-1760533423783.png)

However, if that is not the case, you will be presented with this dialog instead:

![](/Vehicles/Vehicle%20Management/a/image-1760533540967.png)

In this example, `test` has access to both vehicles but `test2` only has access to one of the vehicles. The left side of the dialog is for Common Collaborators which means collaborators who have access to all selected vehicles, whereas Partial Collaborators on the right side is for collaborators who only have access to some of the selected vehicles.

Adding a Collaborator in this dialog will add the user as a Common Collaborator.

You can also move selected Partial Collaborator on the right to become a Common Collaborator by selecting the users and clicking "Move Selected"

You can delete both Common or Partial Collaborators by selecting them and clicking "Remove Selected"

## Household Members

Household members differ from collaborators in that they automatically inherit vehicles from their head of household and their permissions are more limited than a full collaborator.

Collaborators are vehicle-specific whereas a household member is user-specific.

Head of Households must be full collaborators of the vehicle in order for their household members to access the vehicle.

### Managing Households

Every user has a household that they can manage

![](/Vehicles/Collaborators/a/image-1763222741115.png)

Users can add users to their household and set their roles which determines their permissions

![](/Vehicles/Collaborators/a/image-1763222863061.png)

There are three roles:

- Viewer: Read-only permisisons
- Editor: Add and edit records
- Manager: Add, edit, and delete records

Household members cannot delete or manage collaborators for a vehicle inherited from their head of household.

Users can be members of multiple households, if there are different roles for the same vehicle across multiple households, they will have the permissions of the greater role. I.e.: if the household for `test` and `test2` can both access the same vehicle but `test` only granted Viewer role to `test3` whereas `test2` granted Manager role to `test3`, `test3` will have permissions from the Manager Role.

Household members only inherit vehicles from their direct head of household. If their head of household is a household member of another user, the users do not inherit those vehicles. I.e.: `test3` is a member of `test` household and `test` is a member of `test4` household, `test3` does not inherit vehicles from `test4`

#### Root User Household

Root users cannot have their own household by design as a household that can automatically view every vehicle created in the system is a security risk. Root users must create a separate user and add that new user as a collaborator to the vehicles before adding other users to their household.

### Collaborator vs Household Member Permissions

![](/Vehicles/Collaborators/a/image-1763223623195.png)
