# [PushPole](http://push-pole.com) SDK plugin for Unity.

> **Note**: Works only for projects targeted **Android** platform.

## Run the sample

* Clone this repo: `git clone https://github.com/push-pole/unity-sample.git`
* Open the project with your unity editor.


## Add PushPole to your own project

### Import PushPole to the project

* Download the latest package from the [documents](https://docs.push-pole.com/docs/unity/) or right here.

<img src="https://img.shields.io/github/v/release/push-pole/unity-sample"></img>
> Checkout [ChangeLog](https://github.com/push-pole/unity-sample/blob/master/CHANGELOG.md) for more details.


* Right click on `Assets` and select `Import package => Custom package` and browse downloaded file <br>

* From `Assets` menu, go to `Play service resolver => Android resolver`, and select `Resolve` or `Force resolve`<br>
> **Note**: Since gradle repositories refuses connections from Iran, you must use proxy in order to get the necessary files from gradle<br>

* For simple initialization, just drag `PushPole.cs` script to your game object in the hierarchy (e.g. Main camera).

### Change AndroidManifest.xml

1. Go to your [PushPole console](http://console.push-pole.com/) and add your application with the same application package name selected in `Bundle Identifier`<br>
2. Get the manifest content and add it to your project manifest file.<br>

> **Note:** If your application doesn't have such a manifest, go to `C:\Program Files\Unity\Editor\Data\PlaybackEngines\androidplayer\apk` and copy `AndroidManifest.xml` to your `Assets/Plugins/Android`

### Run
Your project is ready to launch. Select `Build&Run` from `File` menu and test it on your device.


## Usage methods

> **Note**: Since PushPole uses `AndroidJavaObject` and `AndroidJavaClass`, wrap all usages in try/catch block in order to prevent errors.

#### Initialization

 To initialize PushPole, make sure manifest token is set and then call:
 
 ```c#
 PushPole.Initialize(); // Optional arguemnt (showGooglePlayDialog: Boolean)
 ```
 
**Note**: Before using any other PushPole methods, be sure to call `Initialize()` first.
 
#### Topic (Categorize users in specific groups)
 
To add user to a specific group, use topics. To subscribe a user to a topic:
 
```cs
var topicName = "sport";
PushPole.Subscribe(topicName);
```
And to unsubscribe:

```cs
var topicName = "sport";
PushPole.Unsubscribe(topicName);
```

#### Disable / Enable notification

```cs
PushPole.SetNotificationOn(); // To enable (Default settings)

PushPole.SetNotificationOff(); // To disable
``` 

#### Check initialization

To see if PushPole has already been initialized, use this method:

```cs
bool isPushPoleInitialized = PushPole.IsPushPoleInitialized();
```

#### PushPole id

A unique id for the device (this id belongs to the device and will not change). To get PushPole id call this method:

```cs
string PushPoleId = PushPole.GetId();
```

#### Send notification via code

Having a PushPole id of a device, you can send notification to it using these codes.

To send a simple notification with only title and content:

```cs
var PushPoleId = "somePushPoleId";
var title = "Notification title";
var content = "Notification content";

PushPole.SendSimpleNotifToUser(PushPoleId, title, content);
```

> To send notification to the current device running this code use `PushPole.GetId();` as the PushPole id (first argument).

To send an advance notification with other properties:

```cs
var PushPoleId = "somePushPoleId";
var notificationJson = "{ \"title\":\"Notification content\"", \"content\":\"Notification content\" }";
PushPole.SendAdvancedNotifToUser(PushPoleId, notificationJson);
```


## More info and FAQ
For detailed documentations visit https://docs.push-pole.com/docs/unity/
[Troubleshooting](https://docs.push-pole.com/docs/unity)

#### Contribution

If there are any improvements you can add to make this sample better, feel free to send a pull request.

## Support 
#### Email:
support [at] push-pole.com
