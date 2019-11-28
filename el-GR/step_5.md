## Displaying data in the ListView

The next step in the making of your app is creating a way to see all the accessbile places. You want to program it so that it finds all the place entries and then adds each one as an element of the ListView in the ListOfPlaces screen. To do this, you are to need the FirebaseDB component again.

+ Switch to the ListOfPlaces screen and drag out a FirebaseDB component onto the Designer view.

+ Now switch over to the Blocks view, and take out a `when ListOfPlaces.Initialize` block. Everything in this will run as soon as this screen opens up.

+ Place a `call FireBase.GetTagList` block inside this block. This tells Firebase to return a list containing the tags of all saved data in your database.

![](images/firebaseGetTagList.png)

+ Take out a `when FireBase.TagList` block and insert a `for each item in list` block inside it. This function will run as soon as Firebase gets our collection of tags in the form of a list, which it uses as the `value` variable.

With the `for` loop you now have individual tags being set to the item variable. Of course you don’t want the tag, you want the address, and you'll use the tag to get it.

Grab a `call Firebase.GetValue` block, and set the tag to the `item` variable, since this contains the current tag from the `value` list.

![](images/firebaseTagList.png)

+ Add a `when Firebase.GotValue` block, and put a `add items to list` block inside it.

+ You will need a list to add locations to, so add an `initialize global name` block. Change its `name` to `locations` and drag a `create empty list` block onto the end of it.

+ Now attach a `get global locations` block to the list attachment of the `add items to list` block, and a `get value` block to the item attachment. The `value` variable contains the address of the place.

**Note**: the list of tags will also contain the `"PlaceNumber"` tag that you're using to keep count of the places, so you'll need to exclude that from the list you display.

+ Add an `if then` block from Control to your `GotValue` block, and move the `add items to list` code so it's inside the `then` block.

+ Onto the `if` part: attach a `not` and an `=` from Logic. Hover over the `tag` variable and put a `get tag` on the left of the `=`. tThen put a `""` Text block on the right and type `"PlaceNumber"` into it.

![](images/ifTagNotPlaceNumber.png)

+ Lastly you need to tell the ListView to get its elements from your list. Get a `set ListView.Elements` block and attach a `get global locations` block to it.

![](images/firebaseGotLocation.png)
