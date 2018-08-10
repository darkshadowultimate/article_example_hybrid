# Project Phonegap - Hybrid App

## Requirements

**node / npm** <br />
**localtunnel** (only if you're running a NodeJS server locally) <br />
**cordova** <br />
**phonegap** - maybe for testing on website <br />
**Android Studio** <br />
**XCode** <br />


## Setup Envoirment

### node / npm

To install node and npm on Mac you need to type from terminal:
```
	brew install node
``` 
Obviously this is the way using Homebrew and it's very easy and fast.
Once you have done that, check from your terminal the correct installation
of **node** and **npm** by typing : ```node -v``` then ```npm -v```.

If you need more information see [npm](http://blog.teamtreehouse.com/install-node-js-npm-mac).

##

### localtunnel

This is a dependency of NodeJS and allow you to specify a port on your computer to assign to it a public URL (https://{random_characters}.localtunnel.me).

**N.B.** => every time that this command is executed, assumes a different URL because the command decides the random characters to use. So when it changes you have to change the URL inside your code, too.

To install it globally type from your terminal :
```npm install -g localtunnel```

To execute the command type from your terminal :
```lt --port {number_port}```
Example : ```lt --port 4000``` (because my NodeJS server is listening on 4000 port)

For more informations see the official page [localtunnel](https://www.npmjs.com/package/localtunnel)

##
### Cordova

To install cordova you can use directly **npm** by typing from terminal : 
```npm install -g cordova```.

If you want consult **npm** official page see [cordova](https://www.npmjs.com/package/cordova).

##
### Phonegap

To install phonegap you can use directly **npm** by typing from terminal :
```npm install -g phonegap```.
If you want consult **npm** official page see [npm-phonegap](https://www.npmjs.com/package/phonegap)

For testing you app from the website,  inside your project's folder directory you can type :
```phonegap serve``` .
It will start a server locally giving you an IP address and a port.
If you want consult **phonegap** documentation see [phonegap-doc](http://docs.phonegap.com/references/browser-support/usage/cli/)

##
### Android Studio

To download and install Android Studio go to the official page [Android Studio](https://developer.android.com/studio/)
If you need help consult the [help page](https://developer.android.com/studio/intro/) of Android Studio.

##
### XCode

To download and install XCode go to [Xcode page](https://developer.apple.com/xcode/) or to the appStore.

##
## Creation of the application

### Step 1. - Creation of the app

To create the application you're gonna use cordova from terminal :
```cordova create {name_folder} {unique_id_application} {name_app}```

Example : ```cordova create myapp org.myapp_cordova.raremark helloworld```

If you need a reference see [cordova create](https://cordova.apache.org/docs/en/latest/reference/cordova-cli/#examples)

### Step 2. - Platforms and plugins

Inside your application inside the folder **platforms** are contained the platforms that you'll install and the same for the plugin's folder.
#### Platforms
**N.B.** => Inside the **android** folder the file to open in the emulator is **build.gradle** .
**N.B.** => Inside the **ios** folder the file to open in the emulator is **name_file.xcodeproj** .


#### Adding platform

To add a platform using terminal you need to type : ```cordova platform add {name_platform}```
Example: ```cordova platform add android``` .

#### Removing platform

To add a platform using terminal you need to type : ```cordova platform remove {name_platform}``` 
Example: ```cordova platform remove android``` .

---

#### Adding plugin

To add a plugin using terminal you need to type : ```cordova plugin add {name_platform}```
Example: ```cordova plugin add https://github.com/katzer/cordova-plugin-local-notifications#0.8.1``` .

**N.B.** => If you install a plugin using URL of the repository you'll take the latest version.

#### Removing plugin

To add a plugin using terminal you need to type : ```cordova plugin remove {name_platform}```
Example: ```cordova plugin remove de.appplant.cordova.plugin.local-notification``` .

### Step 3. - Building the app

When the build command is thrown, the **build.gradle** or the **app_name.xcodeproj** file is updated. So everytime you change the app, you have to build your application to see the changes the next time you'll run the emulator.

To build your entire app type the following command in the terminal :
```cordova build```

If you want build your app only for a specific platform type on terminal :
```cordova build {name_platform}```
Example: ```cordova build android```

## Emulators

### Android Studio

Before you execute the emulator you need to open the project.
To do this, you need to open the **build.gradle** file in your android folder.
Path to **build.gradle** => ```main_app/platforms/android/build.gradle``` 

Once done this, select your name on left panel in Android Studio and start the emulator by clicking on **Run** in bar options in the options top bar or on the **green button** start on the right top.

---
### XCode

Before you execute the emulator you need to open the project.
To do this, you need to open the **name_app.xcodeproj** file in your ios folder.
Path to **name_app.xcodeproj** => ```main_app/platforms/ios/name_app.xcodeproj``` 

Once done this, select your name on left panel in XCode and start the emulator by clicking on the **grey button** start on the left top.

## Coding part

The coding used in web developing is the same used in a cordova's project.
However there's a difference for the links.

---
### Links

Usually for the links you need to insert a specific *absolute path* to your app's folder.
But instead to that, you can use ```location.pathname``` to get dynamically the full path
to the file you're currently using.
However that's a disadvantage to this, because you have to write every single combination if you want use only a ```.js``` file to manage routes.


## Notifications - PushBots

For the notifications you need to create a **Firebase** and **PushBots** projects.

### Step 1. - Create a new Firebase project

You need to go on Firebase [website](https://firebase.google.com/) .
After this, log into the console (top right) of the page.
1. Now create a new project :
	1. insert a name for the project ;
	2. and accept the terms for the agreements ;
	3. create the project ;
2. Get *API Server Key* and *ID sender* :
	1. click the *settings* symbol near **Project Overview** ;
	2. click on **Project Settings** ;
	3. click on **Cloud Messaging** ;
3. Register a new app (Android and iOS) in the same project :
	1. Android :
		1. in *Project Overview* choose add Firebase to Android app ;
		2. insert the *id* property value contained in **config.xml** (project folder) ;
		3. click the button *Register app* ;
		4. download the *google-services.json* ;
		5. click on *Next* button ;
		6. follow the instructions to *add the SDK Firebase* ;
		7. then you can *skip* the next phase.
	
	2. iOS :
		1. in *Project Overview* choose add Firebase to iOS app ;
		2. insert the *id* property value contained in **config.xml** (project folder) ;
		3. click the button *Register app* ;
		4. download the *GoogleService-Info.plist* and move it inside the **ios** folder ;
		5. click on *Next* button ;
		6. follow the instructions to add an SDK Firebase to your project.
			
		7. follow the instructions to add lines to your code.
			The location of the *AppDelegate* file is :
			```main_folder/platforms/ios/{name_project}/Classes/AppDelegate.m```  ;
		8. then you can skip the next phase.

---
### Step 2. - Create a new PushBots project
You need to go on Pushbots [website](https://pushbots.com/) .
Click on **GET STARTED FOR FREE** and sign in or sign up.

#### Create a new Pushbots application

**Android** :

1. Once that you're inside the dashboard click on *+ NEW APP* ;
2. change the name to the application ;
3. choose the platform you're interested in and press *GET STARTED* ;
4. click on *INTEGRATE SDK* ;
5. now insert *Sender ID* and *API Server Key* stored in Firebase ;
6. now click on *CORDOVA/PHONEGAP* 
7. now type on your terminal inside your project's folder:
```cordova plugin add pushbots-cordova-plugin --save```
	and follow the instructions.
8. click on *NEXT* button and after you've changed the app, build it and execute it ;
9. once the application will execute the code inserted, the webpage on pushbots
	will receive the initialization code and you'll be able to send a notification from the site ;
10. send a message from the site following the steps in the site to test your app ;

After you'll send the notification, your project will be created on your dashboard in the site.

**iOS** :
1. Click on the three points symbol on the project and choose **Add platform** ;
2. Follow the instructions to use the same project to send notifications to iOS and Android devices ,

---
### Step 3. - Send notifications from server

For this task I've used **NodeJS** and for this reason the example will be different from the code that you'll use for your project,  because your technologies will be different.
However this can be useful at the same for you.

Here's the code to **send notifications from NodeJS to a device, more devices or all devices** (*The values used are fake*).

Install dependencies from terminal in your NodeJS project's folder :
```npm install node-gcm --save```
```npm install pushbots --save```

```javascript
	// respect the order of the followings lines of code
	const gcm = require('node-gcm');
	const pushbots = require('pushbots');

	// respect the order of the followings lines of code
	app.get('/notification', (req, res) => {
	  //console.log(`this is the token: ${ req.query.token }`);

	  /* both of these parameters are visible in the settings of the Pushbots' 			
		 project in 'Keys' option */
	  const Pushbots = new pushbots.api({
	    id:'5b633f581db2dc7f60554283',  //Application ID
	    secret:'81bdf97fef1cde15d2cea4bf4353a5b7' //Application Secret
	  });
	  // define the body of the notification
	  Pushbots.setMessage("This is the body of notification");
	  // define the title of the notification
	  Pushbots.customNotificationTitle("Title of notification");

	  //to push to all devices registrered on the pushbots' project on the site
	  /*
	  Pushbots.push(function(response){
	    console.log(response);
	  });
	  */

	  //to push to one device
	  const token = req.query.token;
	  Pushbots.pushOne(token, function(response){
	      console.log(response);
	  });

	  // response for the client
	  res.send('ok');

});
```

**N.B.** :
To retrieve *Application ID* and *Application Secret*,
follow this steps :

1. go to your dashboard on [pushbots](https://dashboard.pushbots.com/) website ;
2. on the project that you have created, click on the settings symbol ;
3. then select from the menu the option **Keys** and you'll see them.
Your URL should be something like: *https://dashboard.pushbots.com/application/edit/id_user*

If you need more informations [Pushbots-NodeJS](https://github.com/pushbots/pushbots-nodejs)
