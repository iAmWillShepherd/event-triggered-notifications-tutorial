# Event-triggered Notifications Tutorial

OneSignal can be leveraged to deliver messages in response to an event that occurs. An event is simply something that happens. Typically the thing that happens is significant or meaningful in some way. That's it. Nothing fancy.

When it comes to events and OneSignal, you can think of events as actions a user may take or change in your application's state. Events that are commonly observed in OneSignal include cart abandonment, user achievement, and new user signup.  

Events don't happen in a vacuum, however. The context in which they exist is just as important as the event itself, so OneSignal enables you to include details about the context via data tags.

What are Data Tags? They are key-value pairs represented in JSON. OneSignal is unopinionated about what key names you use or the data type of the values, although simplicity is encouraged when modeling your context object.

You may be wondering, what can I do with events in OneSignal? 

One of the cooler things you can do with events is trigger notifications, which we call event-triggered notifications. They are powerful because they effectively allow you to automate your messages.

Suppose, for example, that you want to send a new user an email reminding them to complete app onboarding. This use case can be broken into these workflow steps:

1. A potential user comes to your site (event)
2. They signup for your new app (event)
3. They begin the onboarding process for your app but ultimately do not complete it (event)
4. You send an email after some time reminding them to complete their onboarding (action)

Each event results from a user action, and we can conditionally perform actions based on the event's context. You may be thinking that all this event stuff is a bit abstract, so we'll work through implementing the previous use case. Along the way, I'll cover some best practices to get the most out of event-triggered notifications in OneSignal.

There are actually three methods that can be used to deliver event-triggered notifcations. 
* We could rely on Data tags and Segments to send a message when a user moves into or out of a segment.
* We can take full control over the sending of messages by using the OneSignal notification API.
* We can use one of the SDKs we make available to the most popular platforms.

## Data tags & Segments

This is the easies way to deliver event-triggered notifications requireing very little changes to your code; however, this ease of use comes at the cost of flexibility. This method should only be used when the business rules for sending a notification are simple because this method relies on users entering or leaving a segment. 

## Notification API

This method provides the most flexibility; however, this comes at the cost of simplicity. You will need to write or change code in your project for this method to work and you may need to consider things like rate limiting. This method does not rely on data tags or segments, so this method should be used if data tags & segments are not a fit.

## OneSignal SDK

Reach out to Scott today to talk about the deprecations 
Reach out to the blog platforms to discuss analytics short-coming
Follow people who have some interest
