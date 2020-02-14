## **Compliance with COPPA**

**This is not mandatory, but only if your app has to be COPPA Compliant**


To enable COPPA filter in GreedyGame's Native iOS SDK you can call the method `setCOPPAFilter(true)` in `GreedyGameAgent.Builder` instance.

```Swift tab= hl_lines="4"
  let greedyGameAgent = GreedyGameAgent.Builder()
                       	.setGameId(GAME_ID_CREATED) //e.g 00100100
                        .addUnit(ADUNIT_CREATED)    //e.g float-1000
                        .setCOPPAFilter(true)
                        ---"other builder methods"---
                      	.build()
  greedyGameAgent.initialize()
```

```Objective-C tab="Objective-C" hl_lines="4"
  Builder *builder = [[Builder alloc]init];
  [builder setGameId:GAME_ID_CREATED]; //e.g 00100100
  [builder addUnit:ADUNIT_CREATED]; //e.g float-1000
  [builder setCOPPAFilter:YES];
  ---"other builder methods"---
  self.greedyGameAgent = builder.build;

  [self.greedyGameAgent initialize];
```