# Unity Advanced (Beta)

This guide will walk you through detailed GreedyGame SDK integration without using plugin. In case you want to know more on plugin integration please go to the following link.

### **Getting started**
### **Update your AndroidManifest.xml**

Add the following `<activity>` declaration inside `<application>` tag of the Manifest.
```xml hl_lines="6"
<activity
    android:name="com.greedygame.android.core.campaign.uii.GreedyGameActivity"
    android:configChanges="keyboardHidden|orientation|screenSize|screenLayout|layoutDirection"
    android:hardwareAccelerated="true"
    android:launchMode="singleTask"
    android:screenOrientation="portrait"
    android:theme="@style/Theme.GGTransparent">
</activity>
```

Also, note the highlighted line where you can change the orientation of the `screenOrientation` property based on which orientation you want to open the engagment. All the allowed values can be found in [Android Documentation](https://developer.android.com/guide/topics/manifest/activity-element#screen).

### **Adding Permissions**

GreedyGame SDK needs the following permissions to work with.

**Mandatory permissions**

```xml
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>
<uses-permission android:name="android.permission.ACCESS_WIFI_STATE"/>
<uses-permission android:name="android.permission.INTERNET"/>
```

**Optional permissions**

```xml
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION"/>
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>
```

!!! tip
    `ACCESS_COARSE_LOCATION` permission will help improving the revenue because of doing better ad targetting.

### **Creating Game ID**
Game ID is an unique identifier for your game.

**Follow the below steps to create a Game ID.**

* Goto [https://integration.greedygame.com](https://integration.greedygame.com).
* Login with your GreedyGame's Publisher account.
* Click on **`Games`** menu from the side nav.
* Click on the **`Add Game`** button from the popup model.
* Select the **`Android`** Platform.
* Enter **`Game name`** and **`Package name`** of the game.
* Click on **`SAVE`**.

![Image](img/android/android-game-creation.png)

Once the game is successfully created you will be taken to `Game Details` page where you can see the game related metrics like `Ad requests`, `Impression` and `Clicks`. 

### **Import Google Mobile Ads SDK for Unity**
If you don't have Google Mobile Ads SDK for Unity already integrated download it [here](https://github.com/googleads/googleads-mobile-unity/releases/latest).
Import the package **Assets > Import > Import Custom Package**.
Google Mobile Ads SDK is a mandatory requirement for GreedyGame SDK.


### **Importing GreedyGame Native Ads SDK For Unity**

Download the GreedyGame Unity SDK [here](https://github.com/GreedyGame/unity-plugin/releases/latest)

**Import Unity Package Inside current-sdk folder** 
Open the downloaded SDK folder from github. Go to 'current-sdk' folder and import the package to unity. 
Assets > Import > Import Custom Package

!!! note ""
    Make sure you have atleast one scene added to your Build Settings before proceeding to the next step.




### **Creating Ad Units**
Adunits are ad assets that are rendered as a native component to the game.

**Follow the below steps to create an Ad Unit ID.**

* Goto **[Integration panel](https://integration.greedygame.com)**.
* Select a Game you have created previously.
* Click on **`Create Unit`** inside the **`Ad units in game`** Card.
* Enter all the fields and click **`Save`**.

![Image](img/unit-creation.png)

Follow the same procedure to create multiple Ad Units inside the game.

!!! note ""
    Best practices about the Unit Dimensions can be found under **[Best Practices](http://127.0.0.1:8000/best_practices/)** section.


### **Creating Ad Units**
Adunits are ad assets that are rendered as a native component to the game.

**Follow the below steps to create an Ad Unit ID.**

* Goto **[Integration panel](https://integration.greedygame.com)**.
* Select a Game you have created previously.
* Click on **`Create Unit`** inside the **`Ad units in game`** Card.
* Enter all the fields and click **`Save`**.

![Image](img/unit-creation.png)

Follow the same procedure to create multiple Ad Units inside the game.

!!! note ""
    Best practices about the Unit Dimensions can be found under **[Best Practices](http://127.0.0.1:8000/best_practices/)** section.

### **Initializing GreedyGame SDK**
Create a new C# Script and add the following code snippet inside Start() method
``` c
		DontDestroyOnLoad (this.gameObject);
        if (RuntimePlatform.Android == Application.platform || RuntimePlatform.IPhonePlayer == Application.platform) {
            GGConfig adConfig = new GGConfig ();
            adConfig.setGameId (AppId);
            adConfig.setListener (new GreedyAgentListener ());
            GGUnitConfig adUnitConfig = new GGUnitConfig ("slot-123", defaultTexture, true, false);
            adConfig.addUnit (adUnitConfig);
            adConfig.enableCoppa (enableCoppa);
            GreedyGameAgent.Instance.Init (adConfig);
        }
```
### Create a GGConfig object
* adConfig.setGameId (AppId) : AppId (string) is the id of the app that was created.
* adConfig.addUnit (adUnitConfig) : create GGUnitConfig for each unit that you created and add it using addUnit API or addUnitList API.            
* adConfig.enableCoppa(enable) : enable (boolean) to enforce COPPA regulations 

### **Setting Ad Listener**
Create a class implementing GGAdListener and set it using the setListener API.

| Methods      | Definition                                      |
| ------------ | ----------------------------------------------- |
| `onAvailable(adId)`  | SDK fetched an ad|
| `onUnavailable()`    | Failed to fetch next ad                          |
| `onError(error)`     | SDK not able to initialize. Check the `error` message.|


### Initialize GreedyGame using the following API
```
* GreedyGameAgent.Instance.Init (adConfig);
```

### Rendering Ads

### Identifying/Creating potential ad spots
First step in rendering GreedyGame Ads is identifying which object needs to be used for displaying ads. You can choose any plane surface in your game like billboards or walls in the street etc. for displaying ads. While choosing make sure that these units are visible to the user and are placed at interesting places inside the game.

!!! note ""
    While selecting an object or creating an object for ad rendering, please keep in mind that GreedyGame SDK needs an object with mesh/canvas/sprite renderer to display ads.


### Registering for Ad Rendering
Once you have idenified/created a game object add a CS script to the object and add the following snippets to the script.

### In Start() function
```
GreedyGameAgent.RegisterGameObject("slot-123", this.gameObject);
```

### In Destroy() function
```
GreedyGameAgent.UnregisterGameObject(this.gameObject);
```

