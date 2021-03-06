# phonegap/Cordova Plugin for Pushbots

> PushBots' official module for Phonegap/Cordova

https://pushbots.com/developer/docs/phonegap

## Installation

This requires phonegap/cordova CLI 5.0+

```bash
cordova plugin add pushbots-cordova-plugin
```

##Usage

1. Intialize Pushbots in deviceReady section:
```javascript
var Pushbots = PushbotsPlugin.initialize("PUSHBOTS_APPLICATIONID", {"android":{"sender_id":"SENDER_ID"}});

// First time registration
// This will be called on token registration/refresh with Android and with every runtime with iOS
Pushbots.on("registered", function(token){
	console.log("Registration Id:" + token);
});

Pushbots.getRegistrationId(function(token){
	console.log("Registration Id:" + token);
});
```


2. Methods to use it:
```javascript

Pushbots.updateAlias("Test");
Pushbots.tag("tag1");
Pushbots.untag("tag1");
Pushbots.debug(true);
Pushbots.unregister();

//iOS only

//Reset Badge
Pushbots.resetBadge();
//Set badge
Pushbots.setBadge(10);
 ```
 
 
 3. To handle Notification events:

```javascript
Pushbots.on("notification", function(data){
	console.log("Received: " + data);
});

Pushbots.on("notificationClicked", function(data){
	console.log("Clicked: " + data);
});
 ```