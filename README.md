# Unit testing with MVP Architecture in Android

## Introduction
Mobile applications run on devices that vary greatly in screen size and resolution, processing power, available memory or connectivity. Manually testing your application across all these different device configurations is next to impossible - that's where automated testing can help. There are many ways to architect your android app but not all allow you to structure your code in clean way so that it is easy to test.

**The key idea to a testable architecture is to separate parts of the application, making them easier to maintain and test individually. One common UI Pattern is _Model-View-Presenter_ or MVP for short**

So, let's start implementing a simple **News application** following MVP pattern and add some Unit and functional tests to it. We are going to use 
- *Kotlin* to write this app
- *JUnit4, Mockito* for unit testing 
- *Espresso* for UI test cases

## The Model-View-Presenter pattern
In our app, we follow MVP pattern, separating the data *model* from a passive *view* through a *presenter* that handles the logic of our application.
