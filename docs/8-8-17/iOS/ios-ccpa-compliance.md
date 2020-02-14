## **Compliance with CCPA**

**This is not mandatory, but only if your app has to be CCPA Compliant**


To enable CCPA filter in GreedyGame's Native iOS SDK you can call the method `setCCPAFilter(true)` in `GreedyGameAgent.Builder` instance.

```Swift tab= hl_lines="4"
  let greedyGameAgent = GreedyGameAgent.Builder()
                        .setGameId(GAME_ID_CREATED) //e.g 00100100
                        .addUnit(ADUNIT_CREATED)    //e.g float-1000
                        .setCCPAFilter(true)
                        ---"other builder methods"---
                        .build()
  greedyGameAgent.load()
```

```Objective-C tab="Objective-C" hl_lines="4"
  Builder *builder = [[Builder alloc]init];
  [builder setGameId:GAME_ID_CREATED]; //e.g 00100100
  [builder addUnit:ADUNIT_CREATED]; //e.g float-1000
  [builder setCCPAFilter:YES];
  ---"other builder methods"---
  self.greedyGameAgent = builder.build;

  [self.greedyGameAgent initialize];
```