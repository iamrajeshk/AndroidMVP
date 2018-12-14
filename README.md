# Unit testing with MVP Architecture in Android

## Introduction
Mobile applications run on devices that vary greatly in screen size and resolution, processing power, available memory or connectivity. Manually testing your application across all these different device configurations is next to impossible - that's where automated testing can help. There are many ways to architect your android app but not all allow you to structure your code in clean way so that it is easy to test.

**The key idea to a testable architecture is to separate parts of the application, making them easier to maintain and test individually. One common UI Pattern is _Model-View-Presenter_ or MVP for short**

So, let's start implementing a simple **Contacts application** following MVP pattern and add some Unit and functional tests to it. 
So, we will develop an app that has the following features
- Shows the list of contacts
- Add a new contact
- Show the details of a contact

We are going to use 
- *Kotlin* to write this app
- *JUnit4, Mockito* for unit testing 
- *Espresso* for UI test cases

## The Model-View-Presenter pattern
In our app, we follow MVP pattern, separating the data *model* from a passive *view* through a *presenter* that handles the logic of our application.

### Model
Model provides and stores the data for our application. In our case, it is model that does all the work when we try to load the list of contacts or save a new contact. It is a data source for our application.

### View
A view is responsible to display the data that is provided by the Model. Don't confuse the View with Android View class. A view can be an activity or a fragment. 

### Presenter
Presenter is the co-ordinator between the Model and View. It is responsible to fetch all the data from the model and send it to View to display. It is also responsible to act upon the user interactions.

Now that we reiterated the concept of MVP, let's see the code. We attached a link to the project's git repo. You can clone it and follow along with us.

