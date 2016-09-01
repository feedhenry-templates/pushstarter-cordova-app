
# Cordova Push Template
---------
Author: Erik Jan de Wit   
Level: Intermediate  
Technologies: Javascript, Cordova, RHMAP  
Summary: A demonstration of how to use push notifications with RHMAP.  
Community Project : [Feed Henry](http://feedhenry.org)
Target Product: RHMAP  
Product Versions: RHMAP 3.8.0+   
Source: https://github.com/feedhenry-templates/pushstarter-cordova-app  
Prerequisites: fh-js-sdk : 3.0.+, Cordova : 4.0 or newer

## What is it?

This application shows a list of the push messages that have been recieved with RHMAP.  Refer to [fhconfig.json](www/fhconfig.json) for the relevant configuraiton.

If you do not have access to a RHMAP instance, you can sign up for a free instance at [https://openshift.feedhenry.com/](https://openshift.feedhenry.com/).

## How do I run it?  

### RHMAP Studio

This application and its cloud services are available as a project template in RHMAP as part of the "Push Notification Hello World" template.

### Local Clone (ideal for Open Source Development)
If you wish to contribute to this template, the following information may be helpful; otherwise, RHMAP and its build facilities are the preferred solution.

###  Prerequisites  
 * fh-js-sdk : 3.0.+
 * Cordova : 4.0 or newer

## Firebase Cloud Messaging

 * You need to have a valid Firebase Cloud Messaging project setup. Download the `google-services.json` file from the Firebase Console and put it into the `www` directory of your app.
 * You also need to use the `package` from the Firebase Cloud Messaging configuration. In the studio, you specify this package on the *Config* menu in the *Android* option.

## Build instructions

 * Edit [fhconfig.json](www/fhconfig.json) to include the relevant information from RHMAP.  
 * cordova create <bundle-id> pushstarter
 * cordova plugin add aerogear-cordova-push
 * cordova platform add <ios android windows>
 * cordova run --device

## How does it work?

### Initialization

[index.js#register](www/js/index.js#L30) is the method which is responsible for configuring and setting up push.  Further details are available in our [API documentation](http://docs.feedhenry.com/v3/api/api_push.html).

### Sending messages

Once a message is received the [index.js#onNotification(event)](www/js/index.js#L45) callback is called and will display the message on the UI. You can send messages from the RHMAP studio under the push tab.