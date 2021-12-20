# Event-triggered Notifications Tutorial

An event-triggered notification is an automated messages sent in response to an event.

There are three approaches for implementing these types of notifications:

- Leverage **Segments** for sending messages
- Use the OneSignal Notification API
- Use a platform SDK

This tutorial series will cover the three methods outlined above, but first, I need to cover the building blocks that make this possible: events, segments, and automated messages.

## Example Use-case

Suppose we want to send a new user an email, reminding them to complete the onboarding process for our app. The workflow may look something like the following:

1. A potential user lands on our site
2. They sign up for our app
3. They begin the onboarding process for the app, but don't complete it
4. The app sends a customized email after 2 days of inactivity reminding them to complete onboarding

Each event results from a user action, and we can conditionally perform actions based on the event's context. You may be thinking that all this event stuff is a bit abstract, so we'll work through implementing the use case. Along the way, I'll cover some best practices to get the most out of event-triggered notifications in OneSignal.

## What Are Events

An event is an action or occurrence recognized by the software that usually originates from user interaction.

Common events you may want to respond to include:

- Cart abandonment
- User achievement
- New user signup
- A checkout
- Social share

### Events generated in example use-case

Let's see where events are generated with respect to our use-case example:

- **Step 1 -** Landing on the site
- **Step 2 -** Signing up for the app
- **Step 3 -** Starting the onboarding process
- **Step 4 -** N/A

## What Are Data Tags

Events don't happen in a vacuum, so we provide a mechanism for you to include relevant context about the event called **data tags**.

Data tags are attributes you attach to a device/user expressed as key-value pairs that enable you to:

- Group devices/users into segments
- Personalize messages
- Track and analyze user data

### Rules

Tags should be structured as key-value string pairs and never as a list or array. When implementing an even-triggered message workflow, we need to capture tags based on user activity. Keys should identify the action, while values can be one of several types.

- Numbers to count actions taken
- Strings for qualitative data
- Timestamps for time data

#### Keys

- Name cannot be `null` or `undefined`
- Names are case-sensitive

#### Values

- Must be encoded as string data; this includes numbers
- Cannot contain more than 300 characters

#### Best practices

- Only use lowercase characters for key names.
- Avoid special characters (`~ ! @ # $ % ^ & * ‘ { } ( ) | \ .`) in key names and value data.
- Avoid spaces in both key names and value data
- Stick to alphanumeric characters and underscores (`_`)
- Keep it simple when modeling data tag values

### Capturing data

We can capture tags from user interactions like clicks or form submissions and send them using the `sendTag` and `sendTags` methods available across all of our SDKs.

```js
// Web SDK
OneSignal.sendTag("times_event_performed", "3");
```

We recommend using numbers as much as possible in your tag values. They support logical operations that enable more fine-grained user targeting and time operations that measure how long it’s been since a user acted. When using numbers to represent time like Unix timestamps, be sure to convert the value to seconds before sending it to OneSignal.

### Data tags in example use-case

Let's explore how data tags are used in our use-case example.

**Step 1 -** We capture specific attributes like whether or not the potential user has ever landed on our site in the past.

```json
{
  "last_site_visit_date": ""  // the potential user has never landed on our site
```

**Step 2 -** We collect user details like name, email, etc from the event's context.

```json
{
  "last_site_visit_date": "",
  "first_name": "Rick",
  "last_name": "Sanchez",
  "email": "something@example.com"
}
```

**Step 3 -** use data tag to indicate wherein the onboarding process the user is and when they got there. If our process has only two steps, we would choose either `onboarding_started` or `onboarding_complete` and mark the time for each step.

```json
{
  "last_site_visit_date": "",
  "first_name": "Rick",
  "last_name": "Sanchez",
  "email": "picklerick@gmail.com",
  "onboarding_stage": "started",
  "onboarding_start_date": "1638209022859" // 'Mon Nov 29 2021 12:04:00 GMT-0600 (Central Standard Time)'
}
```

**Step 4 -** N/A

## Segments

Segments allow you to group devices based on their attributes. We can take advantage of one of the features of segments – sending an automated messages when a user/devices moves into a segment – to deliver an event-triggered notication workflow.

### How to create a segment

1. Navigate to _Audience_
2. Click _New Segment_ button
3. Give the segment a name
4. Add rules for how users will be filtered
   <img width="1439" alt="Screen Shot 2021-10-12 at 1 37 57 PM" src="https://user-images.githubusercontent.com/1715082/137010953-d2c9d0e2-1823-4327-bcd2-2dcfdcc80fe8.png">
5. Click the _Create Segment_ button

### How to inspect data tags

Since segments depend on data tags, we should learn how to inspect their values, so that we can have some level of transparency into how a device ends up in a particular segment. This is very useful when you're trying to debug why a device is being placed into a particular segment.

1. Navigate to _Audience_
   <img width="1437" alt="audience-menu-selection" src="https://user-images.githubusercontent.com/1715082/137007996-c1c20dc2-e649-4f78-8b38-8c8388d12f34.png">
2. Select _All Users_ from the submenu
   <img width="1441" alt="users-submenu-selection" src="https://user-images.githubusercontent.com/1715082/137008242-8b0c87e8-1f14-4eae-84bb-7c01ffea3f03.png">
3. Adjust the _Displayed columns_ to see your tags
   <img width="1440" alt="displayed columns" src="https://user-images.githubusercontent.com/1715082/137007643-9c3993db-c8ee-4737-bed6-e03bf0d80e2a.png">

## Message Templates

[Message templates](https://documentation.onesignal.com/docs/templates) enable you to scaffold out a message whose content is dynamically generated via data tag substitution.

### How to creating a message template

We can create a message template using the dashboard by following these steps.

1. Navigate to _Messages_
2. Select _Templates_ from the submenu
3. Click the _New Push Template_ button
4. Complete the _Message_ form and save
   <img width="1438" alt="message template" src="https://user-images.githubusercontent.com/1715082/137006870-da9066f1-1140-4acb-9eee-f1b5903a23b5.png">

## Automated Messages

[Automated messages](https://documentation.onesignal.com/docs/automated-messages) enable you to push notifications or emails when a user enters a segment and are a key building block for implementing event-triggered notifications.

### How to Create an Automated Message

We can create automated messages using the OneSignal dashboard by following these steps.

1. Navigate to _Messages_
   ![automated-message-1](https://user-images.githubusercontent.com/1715082/136893452-2decb342-09e4-4e6a-aa15-724c3a92534e.png)

2. Select _Automated_ from the submenu
   ![automated-message-2](https://user-images.githubusercontent.com/1715082/136895432-3090eec7-ecfa-4dce-bded-1022faecaec2.png)

3. Click the _New Automated Push_ button
   <img width="1440" alt="Screen Shot 2021-10-11 at 11 28 10 PM" src="https://user-images.githubusercontent.com/1715082/136896871-6ebf5f79-dd5e-411c-9214-81d15bc61069.png">

4. Select _Send to particular segment(s)_ option
   <img width="1440" alt="Screen Shot 2021-10-11 at 11 28 39 PM" src="https://user-images.githubusercontent.com/1715082/136897124-b8cc315d-fad3-4be5-b710-5bb93c7e3f3a.png">

5. Choose segments to include
   <img width="1440" alt="Screen Shot 2021-10-12 at 12 34 32 AM" src="https://user-images.githubusercontent.com/1715082/136897939-831d4fcb-c464-4cd7-9840-d4fbb49d6ee7.png">

6. Choose a backing message template
   <img width="1439" alt="message-template-selection" src="https://user-images.githubusercontent.com/1715082/136990762-a253eaf9-a08b-49b9-8f8d-ac70fa2e2ac2.png">

7. Check _If the user returns to the app_ delivery option
   <img width="1439" alt="delivery-options" src="https://user-images.githubusercontent.com/1715082/136990476-08be3754-7f63-4ce9-80fd-ee606d8406d3.png">

8. Activate the automated message

## Triggering a notification
