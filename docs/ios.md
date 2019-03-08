# **iOS**
In this section we are going to see how to integrate GreedyGame Native Ads in iOS native projects.

### **Importing GreedyGame Native Ads SDK**

Games built with Xcode can easily integrate with Cocoapod or Manually.

**CocoaPod:**

**Manual installation:**



### **Adding Permissions**

GreedyGame SDK needs the following permissions to work with.

**Mandatory permissions**

```.plist  
    Add 'App Transport Security Settings' in your project plist file.
    Then make 'Allow Arbitary Loads' to 'YES'.
```
 ![Image](img/iOS/App-Transport-Security.png)

**Optional permissions**     


 Add any one of the location permission depends upon your requirement.We prefer to set `Privacy-Location when In Use Usage Description`
 in plist file.


 ![Image](img/iOS/Location permission.png)


!!! tip
    Location permission will help improving the revenue because of better ad targeting.

### **Creating Game ID**
Game ID is an unique identifier for your game.

**Follow the below steps to create a Game ID.**

* Goto [https://integration.greedygame.com](https://integration.greedygame.com).
* Login with your GreedyGame's Publisher account.
* Click on **`Games`** menu from the side nav.
* Click on the **`Add Game`** button from the popup model.
* Select the **`iOS`** Platform.
* Enter **`Game name`** and **`Bundle Id`** of the game.
* Click on **`SAVE`**.


![Image](img/iOS/iOS-Game-creation.png)

Once the game is successfully created you will be taken to `Game Details` page where you can see the game related metrics like `Ad requests`, `Impression` and `Clicks`.

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

### **Initializing GreedyGameAds**


`import` greedygame framework

```Swift tab=
 // Import GreedyGame framework like below 

 import greedygame

```

```Objective-c tab="Objective - C"
 // Import GreedyGame framework like below

 #import <greedygame/greedygame.h>

```

`GreedyGameAds` is the entry point to fetching Native Ads from GreedyGame SDK. Create `GreedyGameAds` instance in the `viewDidLoad` of the ViewController.

```Swift tab=
 let greedyGameAds = GreedyGameAds.Builder()
                       	.appId(GAME_ID_CREATED) //e.g 00100100
                        .addUnitId(ADUNIT_CREATED) //e.g slot-1000
                      	.addUnitId(ADUNIT_CREATED) //e.g slot-1000
                        .withAdListener(self)
                      	.build()
```

```Objective-c tab="Objective - C"

// Create GreedyGameAds property in .h file

@property(nonatomic, strong)GreedyGameAds *greedyGameAds;


// Add the below code under ViewDidLoad function in .m file

    Builder *builder = [[Builder alloc]init];
    [builder appId:GAME_ID_CREATED]; //e.g 00100100
    [builder addUnitId:ADUNIT_CREATED]; //e.g slot-1000
    [builder addUnitId:ADUNIT_CREATED]; //e.g slot-1000

    self.greedyGameAds = builder.build;

```
### **AdListener methods**

| Methods      | Definition                                      |
| ------------ | ----------------------------------------------- |
| `onAvailable(adId:)`  | SDK fetched an ad|
| `onUnavailable()`    | Failed to fetch next ad                          |
| `onError(error)`     | SDK not able to initialize. Check the `error` message.|

### **Rendering Native Ads**

To render Native Ads set the the `NativeAdView` class in  any of the view in Viewcontroller in which you want to show Native Ads.

```Swift tab=
	let nativeAdView = NativeAdView(frame: <View Size>)
	nativeAdView.adUnit = ADUNIT_CREATED
	self.view.addSubview(nativeAdView)
```

```Objective-C tab="Objective-c"
    NativeAdView *nativeAdView = [[NativeAdView alloc]initWithFrame:<View Size>];
    nativeAdView.adUnit = ADUNIT_CREATED;
    [self.view addSubview:nativeAdView];
```

Also you can add NativeAdView directly to the UIView in storyBoard.By simply assign the NativeAdView Class in Identitiy Inspector instead of UIView.

* Add the UIView into the storyBoard.

* Go to Identity inspector at the right side pane.Change the UIView class to NativeAdView.
	 	![image](img/iOS/NativeAdView-class-creation.png)

* Go to Attributes inspector enter the unit for the view and add the adUnitId in the unit Id box.
		![image](img/iOS/UnitId-Creation.png)	

!!! info
    The advantage of integrating GreedyGame Native Ads is that we handle Ads refresh based on the value **`Refresh time`** set in the Integration Panels **`Edit Game`** section. Also, by integrating via `NativeAdView` GreedyGame sdk handles `Click` and `Applying Ads` itself. 	

## **Load an Ad**
To load Native Ads call the `load()` method from `GreedyGameAds` instance created before.

```Swift tab=
  let greedyGameAds = GreedyGameAds.Builder()
                       	.appId(GAME_ID_CREATED) //e.g 00100100
                        .addUnitId(ADUNIT_CREATED) //e.g slot-1000
                      	.addUnitId(ADUNIT_CREATED) //e.g slot-1000
                        .withAdListener(self)
                      	.build()
   greedyGameAds.load()
```

```Objective-C tab="Objective-C"
  Builder *builder = [[Builder alloc]init];
  [builder appId:GAME_ID_CREATED]; //e.g 00100100
  [builder addUnitId:ADUNIT_CREATED]; //e.g slot-1000
  [builder addUnitId:ADUNIT_CREATED]; //e.g slot-1000
  self.greedyGameAds = builder.build;

  [self.greedyGameAds load];
```
!!! tip "When to load the GreedyGame's Native Ad?"
    Load the ads by calling `greedyGameAds.load()` as early as possible to get the benefits of getting an Ad early. An ideal place would be to call this on `ViewDidLoad()` method of the first viewcontroller of the game.

Once `load()` method called GreedyGame SDK will fetch ads directly from GreedyGame's demand or it will fetch from any of the Mediation's enabled.

## **Destroy Ads**

When you are done with the ads and do not want to display it call `destroy()` on `GreedyGameAds` instance.

```Swift tab=
self.greedyGameAds.destroy()
```

```Objective-C tab="Objective-C"
[self.greedyGameAds destroy];
```
