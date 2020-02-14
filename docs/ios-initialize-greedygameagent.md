### **Initializing GreedyGameAgent**

`GreedyGameAgent` is the entry point to fetching Native Ads from GreedyGame SDK. 

Create `GreedyGameAgent` instance in the `viewDidLoad` of the ViewController or `didFinishLaunchingWithOptions` in AppDelegate.

### **Import GreedyGame Framework**

```Swift tab=

  import greedygame

```

```Objective-c tab="Objective - C"

  #import <greedygame/greedygame.h>

```

### **Creating GreedyGameAgent**

```Swift tab=
  // Create the greedyGameAgent variable globally
  var greedyGameAgent : GreedyGameAgent?

  // Add the below code in ViewDidLoad of ViewController or didFinishLaunchingWithOptions in AppDelegate
  greedyGameAgent = GreedyGameAgent.Builder()
                        .setGameId(App_ID_CREATED) //e.g 00100100
                        .addUnit(ADUNIT_CREATED) //e.g unit-1000
                        .addUnit(ADUNIT_CREATED) //e.g float-1000
                        .stateListener(self)
                        .build()
```

```Objective-c tab="Objective - C"

 // Create GreedyGameAgent property in .h file
  @property(nonatomic, strong)GreedyGameAgent *greedyGameAgent;


 // Add the below code in .m file
  Builder *builder = [[Builder alloc]init];
  [builder setGameId:APP_ID_CREATED]; //e.g 00100100
  [builder addUnit:ADUNIT_CREATED]; //e.g unit-1000
  [builder addUnit:ADUNIT_CREATED]; //e.g float-1000
  [builder stateListener:self];

  self.greedyGameAgent = builder.build;
```

### **CampaignStateListener methods**

Extend the `CampaignStateListener` to the corresponding viewcontroller or AppDelegate which receives callback of the ad.


| Methods      | Definition                                      |
| ------------ | ----------------------------------------------- |
| `onAvailable(campaignId: String)`  | SDK fetched an ad|
| `onUnavailable()`    | Failed to fetch next ad                          |
| `onError(error: String)`     | SDK not able to initialize. Check the `error` message.|


```Swift tab=
func onAvailable(campaignId: String) {
    loadAd()
   /*
   This function will be used for rendering ads.
   This will be defined in a later step .
   */
   reloadAd()
   /*
   In this context,the function will start the countdown for the refresh call, to fetch new ads.
   This will be defined in a later step.
   */
}

func onUnavailable() {
    reloadAd()
    /*
    This function retries to get an ad when campaign is unvailable or onError.
    This will be defined in a later step.
    */
}

func onError(error: String) {
    reloadAd()
    /*
    This function retries to get an ad when campaign is unvailable or onError.
    This will be defined in a later step.
    */
}
```

```Objective-c tab=

-(void)onAvailableWithCampaignId:(NSString *)campaignId{
    [self loadAd];
    /*
    This function will be used for rendering ads.
    This will be defined in a later step .
    */
    [self reloadAd];
    /*
    In this context,the function will start the countdown for the refresh call, to fetch new ads.
    This will be defined in a later step.
    */
}


-(void)onUnavailable{
    [self reloadAd];
    /*
    This function retries to get an ad when campaign is unvailable or onError.
    This will be defined in a later step.
    */
}

-(void)onErrorWithError:(NSString *)error{
    [self loadAd];
    /*
    This function retries to get an ad when campaign is unvailable or onError.
    This will be defined in a later step.
    */
}
```

!!! INFO
    <font size="2.5">You can look at the definitions of  **[`loadAd()`](ios-rendering-ads.md#implementation-of-rendering-code)** , **[`reloadAd()`](ios-refresh-ads.md)** for a better understanding of the flow.</font>

To initialize GreedyGame SDK call the `initialize()` method from `GreedyGameAgent` instance created before.

```Swift tab= hl_lines="8"
  let greedyGameAgent = GreedyGameAgent.Builder()
                        .setGameId(App_ID_CREATED) //e.g 00100100
                        .addUnit(ADUNIT_CREATED) //e.g unit-1000
                        .addUnit(ADUNIT_CREATED) //e.g float-1000
                        .stateListener(self)
                        .build()

  greedyGameAgent.initialize()
```

```Objective-c tab= hl_lines="16"

 // Create GreedyGameAgent property in .h file

  @property(nonatomic, strong)GreedyGameAgent *greedyGameAgent;


 // Add the below code under ViewDidLoad function in .m file

  Builder *builder = [[Builder alloc]init];
  [builder setGameId:APP_ID_CREATED]; //e.g 00100100
  [builder addUnit:ADUNIT_CREATED]; //e.g unit-1000
  [builder addUnit:ADUNIT_CREATED]; //e.g float-1000
  [builder stateListener:self];

  self.greedyGameAgent = builder.build;

  [self.greedyGameAgent initialize];
```



