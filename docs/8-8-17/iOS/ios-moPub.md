## **Enable MoPub Ads**

GreedyGame SDK can source Ads from GreedyGame directly or it can also fetch demand from `MoPub` also.

To enable `MoPub Mediation` call `enableMoPub(true)` on the `GreedyGameAgent.Builder` instance.

```Swift tab= hl_lines="4"
  let greedyGameAgent = GreedyGameAgent.Builder()
                       	.setGameId(GAME_ID_CREATED) //e.g 00100100
                        .addUnit(ADUNIT_CREATED) //e.g unit-1000
                        .enableMoPub(true)
                        ---"other builder methods"---
                      	.build()
  greedyGameAgent.initialize()
```

```Objective-C tab="Objective-C" hl_lines="4"
  Builder *builder = [[Builder alloc]init];
  [builder setGameId:GAME_ID_CREATED]; //e.g 00100100
  [builder addUnit:ADUNIT_CREATED]; //e.g unit-1000
  [builder enableMoPub:YES];
  ---"other builder methods"---
  self.greedyGameAgent = builder.build;

  [self.greedyGameAgent initialize];
```