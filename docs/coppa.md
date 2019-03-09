

### Android

To enable COPPA filter in GreedyGame's Native Android SDK you can enable it by calling the method `enableCoppa(true)` in `GreedyGameAds.Builder` instance.

```Java tab=
GreedyGameAds greedyGame = new GreedyGameAds.Builder(activity)
    .appId(APP_ID_CREATED) //e.g 00100100
    .addUnitId(ADUNIT_CREATED) //e.g slot-1000
    .enableCoppa(true)
     ---"other builder methods"---
    .build();
```

```Java tab="Kotlin"
val greedyGame = GreedyGameAds.Builder(activity)
    .appId(APP_ID_CREATED) //e.g 00100100
    .addUnitId(ADUNIT_CREATED) //e.g slot-1000
    .enableCoppa(true)
     ---"other builder methods"---
    .build()
```