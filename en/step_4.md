## Getting the user's location

If you want to know where the accessible places are you are going to need users to add the locations of them. Luckily App Inventor has a **LocationSensor** component.

+ On the "AddPlace" screen, drag a LocationSensor from **Sensors** onto your app.

You’re now going to get the user’s location and put it into the **TextBox**.

+ Switch over to the Blocks view and drag two `when Button.Click` blocks onto the screen.

--- collapse ---
---
title: Renaming components
---

I like giving my components identifiable names. 

+ In the **Designer** view click on the component and at the bottom of the **Components** Section click **Rename**. 

+ I called my buttons "CurrentLocation" and "Save".

--- /collapse ---

+ Drag a `set TextBox.Text` block onto the screen and put it in your "Current Location" button.

+ Now drag a `LocationSensor.CurrentAddress` block out and attach it to the `set TextBox.Text` block.

![](images/getUserLocation.png)

Great! Now when you click on "GetLocation" the textbox’s text will be set to your current address from the LocationSensor.

You need to be careful though: it's a good idea to check that there is always an address in the textbox before adding a new place! You need to **Validate the input**.

+ Drag out an `if, then, else` block and put it into the `when Save.Click` block.

+ Now you need to make the `if` condition check if the textbox has text in it.

+ Drag out an `is empty` block and attach it to a `TextBox.text` block.

+ Ok, so now you can check if the **TextBox** is empty, but you want to check if it is **not** empty. To do this, get a `not` block out and put it before the `is empty` block.

![](images/checkIfTextBoxEmpty.png)

One last thing: you need to tell the user that the textbox is empty.

+ Switch over to the Designer view and drag a Label into the app. Give it a warning message and set the text color to red. Finally uncheck the **Visible** checkbox.

+ Also you are only going to want to show that label for a second so you are going to need a Clock. Drag one out from **Sensors** – it will appear with the non-visible components. 

+ Uncheck the clock's **TimerEnabled** checkbox so it doesn’t fire right away!

+ Back in the **Blocks** view drag a `set Label.Visible` and a `set Clock.TimerEnabled` block out and attach both of them to `true` blocks. Now put both in the `else` statement.

![](images/saveClickElse.png)

Nearly there! Now, if there is no text in the **TextBox** your warning label will become visible and your clock will be enabled. You just need to make the label invisible again after about a second, so the user doesn't have to keep looking at it.

+ Take out a when `Clock.Timer` block and duplicate the two blocks you just made. Change `true` to `false` and put the blocks inside the `when Clock.Timer` block.

![](images/hideLabel.png)


