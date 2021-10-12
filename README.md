# Event-triggered Notifications Tutorial

We can implement event-triggered notifications by creating **automated messages** that get triggered when a user enters a **segment**. Adding **Data tags** allow us to arbitrarily group users and enable dynamic content generation when combined with **message templates**. 

Once all the components have been assembled, you can modify your application to set **data tags** when needed and lean on OneSignal to send the notifications wehn needed.

## Automated messages

[Automated messages](https://documentation.onesignal.com/docs/automated-messages) enable you to push notifications and emails when a user enters a segment.

### Create an automated message template using The OneSignal Dashboard

###### 1. Navigate to _Messages_
![automated-message-1](https://user-images.githubusercontent.com/1715082/136893452-2decb342-09e4-4e6a-aa15-724c3a92534e.png)

###### 2. Select _Automated_ from the submenu
![automated-message-2](https://user-images.githubusercontent.com/1715082/136895432-3090eec7-ecfa-4dce-bded-1022faecaec2.png)

###### 3. Click the _New Automated Push_ button
<img width="1440" alt="Screen Shot 2021-10-11 at 11 28 10 PM" src="https://user-images.githubusercontent.com/1715082/136896871-6ebf5f79-dd5e-411c-9214-81d15bc61069.png">

###### 4. Select _Send to particular segment(S)_ option
<img width="1440" alt="Screen Shot 2021-10-11 at 11 28 39 PM" src="https://user-images.githubusercontent.com/1715082/136897124-b8cc315d-fad3-4be5-b710-5bb93c7e3f3a.png">

###### 5. Choose segments to include
<img width="1440" alt="Screen Shot 2021-10-12 at 12 34 32 AM" src="https://user-images.githubusercontent.com/1715082/136897939-831d4fcb-c464-4cd7-9840-d4fbb49d6ee7.png">

###### 6. Choose a backing message template
<img width="1439" alt="message-template-selection" src="https://user-images.githubusercontent.com/1715082/136990762-a253eaf9-a08b-49b9-8f8d-ac70fa2e2ac2.png">

###### 7. Check _If the user returns to the app_ delivery option
<img width="1439" alt="delivery-options" src="https://user-images.githubusercontent.com/1715082/136990476-08be3754-7f63-4ce9-80fd-ee606d8406d3.png">

###### 8. Activate the automated message


## Message templates

[Message templates](https://documentation.onesignal.com/docs/templates) enable you to dynamically generate the content of push notifications and emails.

### Create a message template using The OneSignal Dashboard

###### 1. Navigate to _Messages_

###### 2. Select _Templates_ from the submenu

###### 3. Click the _New Push Template_ button

###### 4. Complete the _Message_ form and save
<img width="1438" alt="message template" src="https://user-images.githubusercontent.com/1715082/137006870-da9066f1-1140-4acb-9eee-f1b5903a23b5.png">


## Data tags

[Data tags](https://documentation.onesignal.com/docs/add-user-data-tags) enable you to attach metadata to user events. 
Tags are a map of key-value pairs and can be set from your application's backend(s) and client(s).

### Inspecting data tags

###### 1. Navigate to _Audience_
<img width="1437" alt="audience-menu-selection" src="https://user-images.githubusercontent.com/1715082/137007996-c1c20dc2-e649-4f78-8b38-8c8388d12f34.png">

###### 2. Select _All Users_ from the submenu
<img width="1441" alt="users-submenu-selection" src="https://user-images.githubusercontent.com/1715082/137008242-8b0c87e8-1f14-4eae-84bb-7c01ffea3f03.png">

###### You may need to adjust the _Displayed columns_ to see your tags
<img width="1440" alt="displayed columns" src="https://user-images.githubusercontent.com/1715082/137007643-9c3993db-c8ee-4737-bed6-e03bf0d80e2a.png">


## Segments

[Segments](https://documentation.onesignal.com/docs/segmentation) enable you to group users by things they have in common.

### Create a segment

###### 1. Navigate to _Audience_
###### 2. Click _New Segment_ button
###### 3. Give the segment a name
###### 4. Add rules for how users will be filtered 
<img width="1439" alt="Screen Shot 2021-10-12 at 1 37 57 PM" src="https://user-images.githubusercontent.com/1715082/137010953-d2c9d0e2-1823-4327-bcd2-2dcfdcc80fe8.png">


## Sample code 

This repo ☝️☝️☝️

1. Explain how to set up and run sample code
