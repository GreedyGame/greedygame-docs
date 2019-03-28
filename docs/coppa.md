

### Android

To enable COPPA filter in GreedyGame's Native Android SDK you can enable it by calling the method `enableCoppa(true)` in `GreedyGameAds.Builder` instance.

```Java tab= hl_lines="4"
GreedyGameAds greedyGame = new GreedyGameAds.Builder(activity)
    .appId(APP_ID_CREATED) //e.g 00100100
    .addUnitId(ADUNIT_CREATED) //e.g slot-1000
    .enableCoppa(true)
     ---"other builder methods"---
    .build();
```

```Java tab="Kotlin" hl_lines="4"
val greedyGame = GreedyGameAds.Builder(activity)
    .appId(APP_ID_CREATED) //e.g 00100100
    .addUnitId(ADUNIT_CREATED) //e.g slot-1000
    .enableCoppa(true)
     ---"other builder methods"---
    .build()
```

## **iOS**

To enable COPPA filter in GreedyGame's Native iOS SDK you can call the method `enableCoppa(true)` in `GreedyGameAds.Builder` instance.

```Swift tab= 
  let greedyGameAds = GreedyGameAds.Builder()
                        .appId(GAME_ID_CREATED) //e.g 00100100
                        .addUnitId(ADUNIT_CREATED) //e.g slot-1000
                        .enableCoppa(true)
                        ---"other builder methods"---
                        .build()
  greedyGameAds.load()
```

```Objective-C tab="Objective-C"
  Builder *builder = [[Builder alloc]init];
  [builder appId:GAME_ID_CREATED]; //e.g 00100100
  [builder addUnitId:ADUNIT_CREATED]; //e.g slot-1000
  [builder enableCoppa:YES];
  ---"other builder methods"---
  self.greedyGameAds = builder.build;

  [self.greedyGameAds load];
```