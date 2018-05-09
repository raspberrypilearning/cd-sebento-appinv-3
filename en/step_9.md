## Filtering by distances

Great! You now have a procedure that can work out the distance between two addresses. Next you have to add this to your `when FireBase.GotValue` function.

For this you of course need two addresses: the address of the place and your address.

+ First you should get your current location. As you will be using this value multiple times it would be a good idea to make a variable contain it. Add an `initialize global name to` block, change its name to `currentLocation` and set it to an empty Text block.

![](images/initGlobalLocation.png)

+ In the `when ListOfPlaces.Initialize` block add a `set global currentLocation to` block and connect it with a `get LocationSensor.CurrentAddress` block.  

+ But what if the user's location is unavailable? To cover this possibility, you need to do a check before setting the current location variable.

+ Put an `if then` block into `when ListOfPlaces.Initialize` and move the `set lobal currentLocation` code into the `then`.    

+ Find the `LocationSensor.HasLongitudeLatitude` block and attach it to the `if`. 
![](images/getCurrentLocation.png)

Now you are ready to use the procedure you made to get the distance.

+ Insert an `initialize local name to` block (the one with a top attachment) into the `then` in your `when FireBase.GotValue` and change `name` to `distance`. 

+ You only want to use the distance formula if you know the user's location, so connect an `if then else` block (the one that has a side attachment), and to the `if` attach three blocks: `not` (Logic), `is empty` (Text) and `get global currentLocation`. 

+ Connect a `call distanceBetween` block to the `then`.  If the current location is blank, you will just show all the places, so place a `0` Math block in the `else` to return a distance of zero.

![](images/initDistWithLocationCheck.png)

+ For one of the **parameters** (values that you are passing to the function) of the `call distanceBetween` attach a `get global currentLocation` block and for the other **parameter** attach a `get value` block (remember this contains the address of the place you got from Firebase).

+ Inside the `initialize local distance to` block add an `if then` block.

+ You are now going to check if the distance is less than 5km. Get a `<` block from the **Math** section along with a `0` block.

+ Put a `get distance` into the first input in the `<` block and the `0` block, set to 5, into the second input. Plug the `<` block into the `if then` block.

+ Move the `add items to list` block to be inside the then statement of the `if then` block.

+ If everything has gone correctly it should look like this:

![](images/filteringByDistance.png)
