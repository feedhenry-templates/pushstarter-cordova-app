
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
Prerequisites: fh-js-sdk : 2.14.+, Cordova : 5.0 or newer

## What is it?

This application shows a list of the push messages that have been recieved with RHMAP.  Refer to [fhconfig.json](www/fhconfig.json) for the relevant configuraiton.

If you do not have access to a RHMAP instance, you can sign up for a free instance at [https://openshift.feedhenry.com/](https://openshift.feedhenry.com/).

## How do I run it?

### RHMAP Studio

This application and its cloud services are available as a project template in RHMAP as part of the "Push Notification Hello World" template.

### Local Clone (ideal for Open Source Development)
If you wish to contribute to this template, the following information may be helpful; otherwise, RHMAP and its build facilities are the preferred solution.

###  Prerequisites
 * Cordova : 5.0 or newer

## Firebase Cloud Messaging

 * You need to have a valid Firebase Cloud Messaging project setup. Download the `google-services.json` file from the Firebase Console and put it into the `www` directory of your app.
 * You also need to use the `package` from the Firebase Cloud Messaging configuration. In the studio, you specify this package on the *Config* menu in the *Android* option.

## Build instructions
 * npm install
 * Edit [fhconfig.json](www/fhconfig.json) to include the relevant information from RHMAP.
 * cordova run --device

### npm dependencies
The `fh-js-sdk` and other development dependencies are defined in [package.json](package.json) and included in a [browserified script](www/main.js).

* This generated [main.js](www/main.js) file is checked-in to allow RHMAP studio preview to statically serve dependencies.

* The [init.js](www/js/init.js) file is browserified and acts as a bridge between template script and npm dependencies. 

* All the other JavaScript files in the template app will not be browserified, in order for you to be able to experiment live edit in RHMAP Studio preview.

### Updating fh-js-sdk version
To update the JS SDK:
- change the version in [package.json](package.json)
- run `npm install` a grunt task is automatically ran to regenerate main.js
- check-in git repo the npackage.json + main.js

### Grunt

This template uses [Grunt](http://gruntjs.com/), the Javascript Task Runner. To use Grunt with this Template App, do the following:

* Install grunt: ```npm install -g grunt-cli```
* In your App directory, run: ```npm install```. This installs Grunt plugins, etc for use with this App.
* Run ```grunt serve``` to preview this App locally


## How does it work?

### Initialization

[index.js#register](www/js/index.js#L30) is the method which is responsible for configuring and setting up push.  Further details are available in our [API documentation](http://docs.feedhenry.com/v3/api/api_push.html).

### Sending messages

Once a message is received the [index.js#onNotification(event)](www/js/index.js#L45) callback is called and will display the message on the UI. You can send messages from the RHMAP studio under the push tab.
