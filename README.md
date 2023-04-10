1. Introduction <br />
I have created a weather application which tells you the temperature and provides you with a brief description of the weather of lots of the major capital cities of popular holiday countries around the world.

The recycler view allows the user to scroll seamlessly through a wide range of countries and upon clicking on a country you are met with the weather information and name of the capital city of that given country

Through the menus, the user has the ability to toggle between different units of temperature and can get the information either in Celsius or Fahrenheit.

Also through the menus, the user has the ability to change the background colour of all windows of the application to either white, red, blue or green. Their preference is stored and will remain set at the colour the user selects until the user changes the colour again.

The application still functions with no internet connection, albeit the weather information cannot load when requested, however, the application informs the user they have no internet connection and encourages the user to check their connection, the application does not crash upon lack of internet.



2. Design Rationale <br />
Fragments: I could have used fragments to display the weather details for each capital city. One fragment displays the list of countries and the second displays the list of capital cities for a selected country. When a capital city is selected, the weather details could be displayed in another fragment. However, this approach would have made the app much more complex and would have added extra unrequired code. I have used a RecyclerView instead to display a list of items (of countries), and launching a new activity to display details of the selected item (The weather information of the capital city).  Considering the simplicity of the UI and lack of complex interactions between different areas of the application I feel using solely activities instead of fragments was a sensible decision.

Content Provider: The app could have used a content provider to retrieve the weather data. This would have made the app more modular, easier to maintain, and upgrade, and had the possibility of allowing other apps to access the data. I felt however for a small app like this it was unnecessary. 

Data Storage Options: For storing data, the user preference for the colour of the background, I used Shared Preferences, useful because it means the app can be closed down or restarted and still be able to store the users' preference.  I could have used a cloud-based database to retrieve real-time weather data, but this would have made the app far more complex than it needed to be.

Using SharedPreferences in the way I did gave a simple way to store user preferences, with a simple key-value storage system. Furthermore, SharedPreferences are private to the app therefore the data that is stored isn't accessible to other apps or extra users on the device. Overall it is a simple lightweight mechanism that was easy to implement.

I have used 'AsyncTask' to offload network operations to a background thread. The doInBackground method from the FetchWeatherInfoTask class performs the network request to get the weather information, and as the doInBackground method runs from a background thread, it means that the main thread is not blocked while waiting for the network request to complete.

Overall, the design of the code is simple and easy to maintain, change and upgrade which is appropriate for a small app like this.


3. Challenges faced and how to improve the app <br />
I really struggled with the menus section and spent the majority of my time learning and debugging that area of my app. The menu was the last area of the app I completed and up to that point, the weather API returned the weather information with units of Kelvin which I felt was neither useful nor appropriate for the user. So in the menus, I allowed the user to choose between Celsius or Fahrenheit however I had great difficulty in getting the value they selected within the menu for the units of temperature over to the URL which requested the weather from the API. The second hardest part of the app for me also came from within the menu area again. It was trying to get the value of what the user selected for their preferred background colour to be displayed across all areas of the app. In order for a specific window to show the new background colour which the user selected, the app had to refresh. I eventually solved the issue by using the onResume method which is called when the activity is resumed after being paused or stopped.

There are lots of improvements I feel can be added to the app. Firstly the ability to search for a specific country/city as opposed to just being given a set list of places to view. Originally I wanted the app to be useful for people looking to go on holiday, hence an app that showed only weather for big holiday cities, I thought would be useful however deep into the project I thought it would be better if the user could just search a city instead. So improvements I'd like to add would be to search any city and then be able to pin specific cities that the user has selected to the top of their list so their favourite cities are all there at a glance. Another improvement I feel would be good is more customisation of the UI. Users can change the background colour but I think being able to change the fonts or language of the app would be a great feature to add. Furthermore a feature I think would be good to add would be the ability to link it to social media accounts. This would allow users to share weather updates wherever they are efficiently and can see the weather from where their friends and family are currently! The last feature I would like to add would be a news API which would display weather-related news under the weather report for any given city.
