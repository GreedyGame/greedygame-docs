## **Enable AdMob Ads**

GreedyGame SDK sources Ads from multiple Ad Demand Partners using GreedyGame's Mediation Platform directly which requires no additional setup.

But to serve Admob ads, GreedyGame requires you to enble Admob in the initialization script.

To enable `Admob Ads` call `enableAdmob(true)` on the `GreedyGameAgent.Builder` instance.

```Java tab= hl_lines="4"
GreedyGameAgent greedyGameAgent = new GreedyGameAgent.Builder(activity)
    .setGameId(GAME_ID_CREATED) //e.g 00100100
    .addUnitId(ADUNIT_CREATED) //e.g slot-1000
    .enableAdmob(true)
     ---"other builder methods"---
    .build();
greedyGameAgent.init();
```

<!-- ```Java tab="Kotlin" hl_lines="4"
val greedyGame = GreedyGameAgent.Builder(activity)
    .appId(APP_ID_CREATED) //e.g 00100100
    .addUnitId(ADUNIT_CREATED) //e.g slot-1000
    .enableAdmob(true)
     ---"other builder methods"---
    .build()
greedyGame.load()
``` -->
