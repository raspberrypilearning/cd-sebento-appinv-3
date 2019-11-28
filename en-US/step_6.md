## Working out the distance between two locations

Don’t worry, I’ll kept the maths to a minimum. You’ll have no problem understanding it, and anyway, you’re going to be programming a computer to do the maths for you!

What you want is to only show places that are close to where a user currently is. To do this, you need to find the distance between two addresses.

To explain how this works, I'll be talking about three things:
  1. Latitude
  1. Longitude
  1. An old guy named Pythagoras

### Latitude and longitude
Latitude and longitude are geographic coordinates. They allow for the position of places to be described using numbers.

   **Example:** The Spire, Dublin, Ireland is located at 53.3498° N (latitude), 6.2603°W (longitude)

+ On average, the distance between two lines of latitude (i.e. The distance between something at 53° to something at 54°) is 111 kilometers (69 miles).

+ The average distance between two lines of longitude is 89 kilometers (55 miles).

Great! So now if you know the latitude and longitude of two points, you can find the distance their latitude and longitude lines are apart.

### That Pythagoras guy

+ You might want to draw out this next bit! What you have right now is the length of two lines, and what you want is the length of the line that connects the tops of these two lines.

![](images/latitudeLongitudeDiagram.png)

You are in luck! In the 500s BC, there lived a mathematician named Pythagoras. He discovered that by knowing the lengths of two sides of a triangle (since what you have is a triangle), you can work out the length of the third side.

He came up with this equation ![](images/pythagorasTheorem.png)  where Z is the largest side

+ So with this in mind, we can insert our values into this equation to calculate the length of the line we're interested in: ![](images/pythagorasTheorem1.png) ![](images/pythagorasTheorem2.png) ![](images/pythagorasTheorem3.png) ![](images/pythagorasTheorem4.png) ![](images/pythagorasTheorem5.png)

Tada! With this method, you can work out the distance between any person and the location of an accessible place! Pretty cool, right?

On the next card, you will write a **procedure** that does this calculation for you.
