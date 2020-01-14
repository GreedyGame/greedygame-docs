### **Initializing GreedyGameAgent**

`GreedyGameAgent` is the entry point to fetching Native Ads from GreedyGame SDK.

Create `GreedyGameAgent` instance in the `onCreate` of the Activity.

```Java tab= hl_lines="2 3"
GreedyGameAgent greedyGameAgent = new GreedyGameAgent.Builder(activity)
    .setGameId(GAME_ID_CREATED) //e.g 00100100
    .addUnitId(ADUNIT_CREATED) //e.g float-1000
    .addUnitId(ADUNIT_CREATED) //e.g float-1002
    .enableAdmob(true)
    .withAgentListener(new CampaignStateListener() {
        @Override
        public void onUnavailable() {
            reloadAd(); 
            /*
            This function retries to get an ad when campaign is unvailable or onError.
            This will be defined in a later step.
            */
        }

        @Override
        public void onAvailable(String campaignId) {
            loadAd();
            /* 
            This function will be used for rendering ads.
            This will be defined in a later step .
            */
            reloadAd();
            /*
            In this context,the function will start the countdown for the refresh call, to fetch new ads.
            This will be defined in a later step.
            */
        }

        @Override
        public void onError(String error) {
            reloadAd(); 
            /*
            This function retries to get an ad when campaign is unvailable or onError.
            This will be defined in a later step.
            */
        }
    })
    .build();
```

!!! INFO
    <font size="3">You can look at the definitions of  **[`loadAd()`](android-rendering-ads.md#implementation-of-rendering-code)** , **[`reloadAd()`](android-refresh-ads.md)** for a better understanding of the flow.</font>

!!! WARNING
    * <font size="3" color="red">**Ensure that you mention the correct App ID and Unit IDs in the highlighted lines, and also for any other ad units.**</font>


<!-- 
```Java tab="Kotlin"
val GreedyGameAgent = GreedyGameAgent.Builder(activity)
    .appId(APP_ID_CREATED) //e.g 00100100
    .addUnitId(ADUNIT_CREATED) //e.g slot-1000
    .addUnitId(ADUNIT_CREATED) //e.g slot-1002
    .withAgentListener(object: CampaignStateListener() {

        override fun onUnavailable() {

        }

        override fun onAvailable(advId: String) {

        }

        override fun onError(error: String) {

        }
    })
    .build()
``` 
-->



To initialize GreedyGame SDK call the `init()` method from `GreedyGameAgent` instance created before.

```Java tab= hl_lines="6"
GreedyGameAgent greedyGameAgent = new GreedyGameAgent.Builder(activity)
    .setGameId(GAME_ID_CREATED) //e.g 00100100
    .addUnitId(ADUNIT_CREATED) //e.g slot-1000
     ---"other builder methods"---
    .build();
greedyGameAgent.init();
```

<!-- ```Java tab="Kotlin" hl_lines="6"
val greedyGame = GreedyGameAgent.Builder(activity)
    .appId(APP_ID_CREATED) //e.g 00100100
    .addUnitId(ADUNIT_CREATED) //e.g slot-1000
     ---"other builder methods"---
    .build()
greedyGame.load()
```
 -->
!!! tip "When to load the GreedyGame's Native Ad?"
    Load the ads by calling `GreedyGameAgent.init()` as early as possible to get the benefits of getting an Ad early. An ideal place would be to call this on `onCreate()` method of `Splash screen` of the game or `Menu screen` of the game.

Once `init()` method called GreedyGame SDK will fetch ads from directly from GreedyGame's demand or it will fetch from any of the Mediation's enabled.

<!-- ## **Destroy Ad**

When you are done with the ads and do not want to display it call `destroy()` on `GreedyGameAgent` instance.

```Java tab=
greedyGame.destroy();
```
 -->
<!-- ```java tab="Kotlin"
greedyGame.destroy()
``` -->

<!-- Detroying ads will automatically remove the Ads created with `NativeAdView`. You can also register for Ad destroy events by the following way.

```Java tab=
greedyGame.setAdDestroyListener(new AdDestroyListener() {
    @Override
    public void onDestroy() {

    }
});
```
 -->
<!-- 
```java tab="Kotlin"
greedyGame.setAdDestroyListener(object: AdDestroyListener() {
    override fun onDestroy() {

    }
});
```
 -->

### **CampaignStateListener methods**

| Methods      | Definition                                      |
| ------------ | ----------------------------------------------- |
| `onAvailable(campaignId)`  | SDK fetched an ad|
| `onUnavailable()`    | Failed to fetch next ad                          |
| `onError(error)`     | SDK not able to initialize. Check the `error` message.|
