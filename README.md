# Unit testing with MVP Design Pattern in Android

## Introduction
There are many ways to architect your android app but not all allow you to structure your code in clean way so that it will be easy to test.

**The key idea to a testable architecture is to separate parts of the application, making them easier to maintain and test individually. One common UI Pattern is _Model-View-Presenter_ or MVP for short**

So, let's start implementing a simple **Contacts application** following MVP pattern and add some Unit and functional tests to it. 
So, we will develop an app that has the following features
- Shows the list of contacts
- Add a new contact
- Show the details of an existing contact

We are going to use 
- *Kotlin* to write this app
- *JUnit4, Mockito* for unit testing 
- *Espresso* for UI test cases

## The Model-View-Presenter pattern
In our app, we follow MVP pattern, separating the data *model* from a passive *view* through a *presenter* that handles the logic of our application.

### Model
Model provides and stores the data for our application. In our case, it is model that does all the work when we try to load the list of contacts or save a new contact. It is a data source for our application.

### View
A view is responsible to display data that is provided by the Model. Don't confuse the View with Android View class. A view can be an activity or a fragment. 

### Presenter
Presenter is the co-ordinator between the Model and View. It is responsible to fetch all the data from the model and send it to View to display. It is also responsible to act upon the user interactions.

Now that we reiterated the concept of MVP, let's see the code. We attached a link to the project's git repo. You can clone it and follow along with us.

#### Project Structure
We have structured the application by *package per feature*. This greatly helps in readability and modularizes the code. Each feature of the app has it's own package

**Package** : com.innominds.mvpcontacts

| Package        | Description                                     |
-----------------|:-----------------------------------------------:|
|.addcontact     | Add new contact                                 |
|.contactdetail  | View contact details                            |
|.contacts       | List of contacts                                |
|.data           | Stores contacts- contains our model             |
|.util           | Utility classes used in various parts of the app|

Each feature of the app contains a **Contract** interface - this defines the interface for the View and Presenter callbacks of each feature. Let's see what that means. Take a look at `AddContactContract.kt` file. This is the *contract* interface for 'Add contact' feature. Here we define two more interfaces

- *View* interface - conatins all the functions that we expose from the View layer and make available to the Presentation Layer 
- *UserActionListener* interface - describes the actions that can be started from the View. The view shouldn't handle user interaction   directly where it affects the model. Instead, it should forward interactions to the presenter

```kotlin
interface AddContactContract {
    interface View{
        fun showEmptyContactError()

        fun showContactsList()
    }

    interface UserActionListener{
        fun saveNote(name: String, description: String)
    }
}
```
we have two functions in View interface, so our fragment should implement this interface functions and define what to be done when presenter calls this method.

