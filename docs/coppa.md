

### Android

To enable COPPA filter in GreedyGame's Native Android SDK you can enable it by calling the method `enableCoppa(true)` in `GreedyGameAgent.Builder` instance.

```Java tab= hl_lines="4"
GreedyGameAgent greedyGame = new GreedyGameAgent.Builder(activity)
    .setGameId(GAME_ID_CREATED) //e.g 00100100
    .addUnitId(ADUNIT_CREATED) //e.g float-1000
    .enableCoppa(true)
     ---"other builder methods"---
    .build();
```

<!-- 
```Java tab="Kotlin" hl_lines="4"
val greedyGame = GreedyGameAgent.Builder(activity)
    .appId(APP_ID_CREATED) //e.g 00100100
    .addUnitId(ADUNIT_CREATED) //e.g slot-1000
    .enableCoppa(true)
     ---"other builder methods"---
    .build()
```
 -->

### iOS

To enable COPPA filter in GreedyGame's Native iOS SDK you can call the method `enableCoppa(true)` in `GreedyGameAgent.Builder` instance.

```Swift tab= hl_lines="4"
  let greedyGameAgent = GreedyGameAgent.Builder()
                        .setGameId(GAME_ID_CREATED) //e.g 00100100
                        .addUnit(ADUNIT_CREATED) //e.g unit-1000 or float-1234
                        .enableCoppa(true)
                        ---"other builder methods"---
                        .build()
```

```Objective-C tab="Objective-C" hl_lines="4"
  Builder *builder = [[Builder alloc]init];
  [builder setGameId:GAME_ID_CREATED]; //e.g 00100100
  [builder addUnit:ADUNIT_CREATED]; //e.g unit-1 or float-1234
  [builder enableCoppa:YES];
  ---"other builder methods"---
  self.GreedyGameAgent = builder.build;
```