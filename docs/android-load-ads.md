## **Load an Ad**
To load Native Ads call the `init()` method from `GreedyGameAgent` instance created before.

```Java tab= hl_lines="6"
GreedyGameAgent greedyGame = new GreedyGameAgent.Builder(activity)
    .setGameId(GAME_ID_CREATED) //e.g 00100100
    .addUnitId(ADUNIT_CREATED) //e.g slot-1000
     ---"other builder methods"---
    .build();
greedyGame.init();
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

