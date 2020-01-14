# SDK-8 Series
We will guide you through the steps involved in integrating GreedyGame SDK in Unity using the GreedyGame Plugin.

## **Integration Video**
Here is a sample video to help you by the whole integration process. We strongly recommend going through the whole documentation before using the video.

<iframe width="560" height="315" src="https://www.youtube.com/embed/jRxXeSkYfg0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### **Importing GreedyGame Native Ads SDK For Unity**

Download the GreedyGame Unity SDK  

<a target="_blank" rel="noopener noreferrer" href="https://github.com/GreedyGame/unity-plugin/releases/" class="pure-material-button-contained">Download Plugin</a>


**Import the Unity Package Inside current-sdk folder** 
Open the downloaded SDK folder from Github. Go to 'current-sdk' folder and import the package to unity. 
**Assets > Import > Import Custom Package**

!!! note ""
    Make sure you have atleast one scene added to your Build Settings before proceeding to the next step.

### **Import Google Mobile Ads SDK for Unity**
If you don't have Google Mobile Ads SDK for Unity already integrated download it <a target="_blank" rel="noopener noreferrer" href="https://github.com/googleads/googleads-mobile-unity/releases/latest">here</a>.
Import the package **Assets > Import > Import Custom Package**.
Google Mobile Ads SDK is a mandatory requirement for GreedyGame SDK<br/>
                            **OR**                                 
Open the downloaded SDK folder from Github(GreedyGameSDK). Go to <br/>**"current-sdk->PlayServicesAAR"** folder.Copy all the **".aar"** files inside this folder and place them under **"Assets->Plugins->Android->libs"**. 


### **Update your AndroidManifest.xml**

Add the following `<activity>` declaration inside `<application>` tag of the Manifest.
```xml 
<activity
  android:name="com.greedygame.android.core.campaign.uii.web.GGWebActivity"
  android:screenOrientation="sensorLandscape"
  android:configChanges="keyboardHidden|screenSize|screenLayout|layoutDirection|orientation"
  android:hardwareAccelerated="true"
  android:launchMode="singleTask"
  android:theme="@style/Theme.GGTransparent"/>

<activity
  android:name="com.greedygame.android.core.mediation.admob.GGAdMobActivity"
  android:screenOrientation="sensorLandscape"
  android:configChanges="keyboardHidden|screenSize|screenLayout|layoutDirection|orientation"
  android:hardwareAccelerated="true"
  android:launchMode="singleTask"
  android:theme="@style/Theme.GGTransparent"/>

<activity
  android:name="com.greedygame.android.core.mediation.greedygame.GGS2SActivity"
  android:screenOrientation="sensorLandscape"
  android:configChanges="keyboardHidden|screenSize|screenLayout|layoutDirection|orientation"
  android:hardwareAccelerated="true"
  android:launchMode="singleTask"
  android:theme="@style/Theme.GGTransparent"/>
```

Also, note the highlighted line where you can change the orientation of the `screenOrientation` property based on which orientation you want to open the engagment. All the allowed values can be found in <a target="_blank" rel="noopener noreferrer" href="https://developer.android.com/guide/topics/manifest/activity-element#screen">Android Documentation</a>

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

None of the above permissions are mandatory. But for better targeting of ads and thereby better revenue possibilities you should include these permissions.<br/>

#### **Android 9.0 requirements**
Add the following code snippets to your manifest file. These are required as part of Android API level 9.0 compatibility. These are mandatory requirements for GreedyGame.<br/>
##### **ClearText Support**
Add the following code snippet to your network config file. This allows GreedyGame API's to work in Android 9.0 devices.<br/>

Create an xml file and name it network_security_config.xml and add the following code snippet inside it.<br/>
Add this file to **"Assets/Plugins/Android/res/xml/"**

```xml
<network-security-config>
  <domain-config cleartextTrafficPermitted="true">
      <domain includeSubdomains="true">api.greedygame.com</domain>
  </domain-config>
</network-security-config>
``` 
Then Inside your Manifest's application tag

```xml
<application 
  ... 
  android:networkSecurityConfig="@xml/network_security_config">
  ...
</application>
```
##### **Apache Legacy Compatibility**
Beginning with Android 9, HTTP library is removed from the bootclasspath and is not available to apps by default. To enable the usage add the following code snippet in manifest.

```xml
<application>
  ...
  <uses-library android:name="org.apache.http.legacy" android:required="false"/>
  ...
</application>
```

### **Creating Ad Units**
Adunits are ad assets that are rendered as a native component to the app.

**Follow the below steps to create an Ad Unit ID.**

* Goto **<a target="_blank" rel="noopener noreferrer" href="https://integration-v2.greedygame.com">Integration Panel</a>**
* Select an App you have created previously.
* Click on **`Create Unit`** inside the **`Ad units in app`** Card.
* Enter all the fields and click **`Save`**.

![Image](img/android/unit-creation.png)

Follow the same procedure to create multiple Ad Units inside the app.

!!! note ""
    Best practices about the Unit Dimensions can be found under **<a target="_blank" rel="noopener noreferrer" href="/best-practices">Best Practices</a>** section.

        



### **Initializing GreedyGame SDK**
Create a new C# Script and add the following code snippet inside Start(). Then add this script to the new "GameObject" in the scene where you want to initialize the SDK(Ideally it should be done in the first scene).

``` c
public List<string> unitList = new List<string> {"unit-1234", "unit-1235",
                                                 "float-2345"};
void Awake(){
    DontDestroyOnLoad(this.gameObject);
    if (RuntimePlatform.Android == Application.platform)
    {
       GGAdConfig ggAdConfig = new GGAdConfig();
       ggAdConfig.setGameId("YOUR GAME ID HERE");
       ggAdConfig.addUnitList(unitList);
       ggAdConfig.enableAdmob(true);
       ggAdConfig.enableNpa(true);      //If you do not receive consent for Personalised Ads
       ggAdConfig.setListener(new GreedyAgentListener());
       GreedyGameAgent.Instance.init(ggAdConfig);
    }
}
```
### Create a GGConfig object
* ggAdConfig.setGameId(AppId) : Game Id (string) is the id of the app that was created.          
* ggAdConfig.enableCoppa(enable) : enable (boolean) to enforce COPPA regulations 

### **Setting Ad Listener**
Create a class implementing GGAdListener and set it using the setListener API.

| Methods      | Definition                                      |
| ------------ | ----------------------------------------------- |
| `onAvailable(campaignId)`  | SDK fetched an ad|
| `onUnavailable()`    | Failed to fetch next ad                          |
| `onError(error)`     | SDK not able to initialize. Check the `error` message.|


### Initialize GreedyGame using the following API
```
 GreedyGameAgent.Instance.Init(adConfig);
```

### Rendering Ads

### Identifying/Creating potential ad spots
First step in rendering GreedyGame Ads is identifying which object needs to be used for displaying ads. You can choose any plane surface in your game like billboards or walls in the street etc. for displaying ads. While choosing make sure that these units are visible to the user and are placed at interesting places inside the game.

!!! note ""
    While selecting an object or creating an object for ad rendering, please keep in mind that GreedyGame SDK needs an object with mesh/canvas/sprite renderer to display ads.


### **Non Clickable Unit Integration**
The non-clickable unit helps creating a branding experience without intruding the user. They should be designed to blend well in your gaming environment.

### Script Integration
You can attach supplied scripts in order to change GameObject textures at runtime.

1. If your game object has mesh renderer or sprite renderer, then attach GGRenderer script to the
GameObject.

2. If you want to take care of the rendering yourself, then attach GGCustomRenderer script to the GameObject and add appropriate code for rendering in Step Delegate-A and Step Delegate-B specified inside the script. Refer to a snapshot of the script below

```c#
private RawImage rawImage;
public Texture defaultTexture;
public string unitId;

// Use this for initialization
void Start () {
//Use this API to register delegates which will send you the branded texture
//The below delegate is an example which uses raw image to render image
//You should make sure that the actual rendering of the object
//is done inside the delegate
    GreedyGameAgent.Instance.registerGameObject(this.gameObject,
        defaultTexture as Texture2D,
        unitId,
        delegate (string unitId, Texture2D assignedTexture, bool isBranded) {
        // The assignedTexture returned by the delegate can be the branded
        // texture, the default texture or a transparent texture. 
        // A transparent texture is returned in case the default texture you
        // pass to the registerGameObject API is null and there are no 
        // branded textures. If you want to disable or enable a game object
        //based on whether assignedTexture is branded or not you can use the
        // isBranded boolean which would be true in case its a branded texture.
        if (assignedTexture != null)
        {
            // Step Delegate-A
            rawImage = GetComponent<RawImage>();
            if(rawImage != null)
            {
                rawImage.texture = assignedTexture as Texture;
            }
        }

        if(!isBranded) {
            // Step Delegate-B
            // Disable your game object here in case you want to.
            // Based on whether the assignedTexture is branded or not
        }
    });
}
void OnDestroy()
{
    GreedyGameAgent.Instance.unregisterGameObject(this.gameObject);
}
```

#### Code Integration
If you want to create your own script or prefer using the API directly, then refer to the Register GameObject documentation given below.

1. If you have a Mesh or Sprite renderer, you can register the game object to receive texture updates. Make sure to unregister the Game Object when the `onDestroy` is called. Please refer to the sample below.

```c#
public Texture2D defaultTexture;// Default Texture for the Game Object
public string unitId;           // Clickable or non-clickable unit ID
public bool applyToAll = true;  // Change to false if you dont want all 
                                // the objects to be updated that share the 
                                // same material
void Start()
{
    // Attach this script to an object that needs branding.
    // Make sure that the object has mesh or sprite renderer attached to it.
    GreedyGameAgent.Instance.registerGameObject(this.gameObject,
    defaultTexture,
    unitId,
    applyToAll);
}

void OnDestroy()
{
    GreedyGameAgent.Instance.unregisterGameObject(this.gameObject);
}
```

2. If you are rendering the GameObjects yourself, you can supply a delegate function to handle
changes yourself.

```c#
private RawImage rawImage;
public Texture defaultTexture;
public string unitId;
void Start () {
    // Use this API to register delegates which will send you the branded texture.
    // The below delegate is an example which uses raw image to render image.
    // You should make sure that the actual rendering of the object
    // is done inside the delegate
    GreedyGameAgent.Instance.registerGameObject(this.gameObject,
        defaultTexture as Texture2D,
        unitId,
        delegate (string unitId, Texture2D assignedTexture, bool isBranded) {
            //The assignedTexture returned by the delegate can be the branded texture,
            //the default texture or a transparent texture. A transparent texture is
            //returned in case the default texture you pass to the registerGameObject
            //API is null and there are no branded textures. If you want to disable or
            //enable a game object based on whether assignedTexture is branded or not
            //you can use the isBranded boolean which would be true in case its
            //a branded texture.
            if (assignedTexture!=null)
            {
                //Step Delegate-A
                rawImage = GetComponent<RawImage>();
                if(rawImage != null)
                {
                    rawImage.texture = assignedTexture as Texture;
                }
            }
            
            if(!isBranded) {
                //Step Delegate-B
                //Disable your game object here in case you want to.
                //Based on whether the assignedTexture is branded or not
            }
        });
}

void OnDestroy()
{
    GreedyGameAgent.Instance.unregisterGameObject(this.gameObject);
}
```

### **Clickable Unit Integration**
Clickable Units are used to collect user response for a particular ad campaign. They typically look like buttons, placed at strategic points, to have minimal gamer inconvenience. Clickable Units present an opportunity for the user to express their interest and know more about the ad that they are experiencing. We recommend placing clickable units in conjunction
with non-clickable units. This is essential for advertisers to measure campaign effectiveness and reach their targets. Clicking on this unit will open an in-game browser, called the User-Initiated Interstitial (UII). This window will show the ad in detail and supports multiple formats of ads.

1. Follow the same steps for non-clickable units to change the texture of the clickable unit.

2. Modify the click property of your game object and call the following code block with the correct unit id.

```c#
GreedyGameAgent.Instance.showEngagementWindow("float-1234");
```

!!! tip
    Like for non-clickable units, please get in touch with your Account Manager to get better ad spots.
!!! tip
    The methods listed for clickable and non-clickable unit integration will automatically update the texture of gameobject if that object is active in scene, you don't need to manually update the game object texture

### **Refresh Ads**

You should refresh the ads that are shown, during natural pauses in your gameflow. Typical examples would include the game pause menu, user trying to restart a level or move to another level, death of a character etc. This will help maximise your revenue and also blend in seamlessly to the gamer. GreedyGame SDK by default doesn’t refresh the ads in between a session. For this you need to call the following API.

```c#
GreedyGameAgent.Instance.startEventRefresh();
```
This will give a callback at the same CampaignStateListener set earlier and the flow would happen as earlier. The units should be properly updated on both `onAvailable()` and `onUnavailable()` callbacks.

!!! warning

    There is a 60 second minimum threshold applied to this API. This means that if this API gets called again within 60 seconds of the previous call, it is ignored.



## **Test Ads**

Now you have successfully integrated with GreedyGame Native Ads now is the time to test the integration.

GreedyGame recommends an easy way to test the ads by following the below steps

* Goto **<a target="_blank" rel="noopener noreferrer" href="https://integration-v2.greedygame.com">Integration Panel</a>**
* Select an App in which you want to check the test ads.
* Click `SCAN QR` under the test Ads section and follow the steps mentioned to get the test ads.


## **Going Live**

You have successfully integrated GreedyGame SDK and verified the testing flow with Test Ads section. Now follow the below steps to start earning revenue.

* Goto **<a target="_blank" rel="noopener noreferrer" href="https://integration-v2.greedygame.com">Integration Panel</a>**
* Select the App which you want to make `Live`.
* Click  `GO LIVE` under Publish section and you will get a message  `Your request has been received and live traffic will be started in 48 hours`.
* You will start making money once the status changes to `APP IS LIVE` under publish section.

!!! warning
    you have gone live do not click on the production ads for testing. Always go to the **Test Ads** section and Test your integration.

## **FAQ**
For Unity Specific <a target="_blank" rel="noopener noreferrer" href="http://127.0.0.1:8000/unity-faq/">here</a>.
<br/>
For General <a target="_blank" rel="noopener noreferrer" href="http://127.0.0.1:8000/general-faq/">here</a>.




