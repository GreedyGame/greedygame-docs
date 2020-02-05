## **Compliance with CCPA**



**This is not mandatory, but only if your app has to be CCPA Compliant**

To enable CCPA filter in GreedyGame's Native Android SDK you can enable it by calling the method `enableCCPA(true)` in `GreedyGameAgent.Builder` instance.

```Java tab= hl_lines="4"
GreedyGameAgent greedyGameAgent = new GreedyGameAgent.Builder(activity)
    .setGameId(GAME_ID_CREATED) //e.g 00100100
    .addUnitId(ADUNIT_CREATED) //e.g slot-1000
    .enableCCPA(true)
     ---"other builder methods"---
    .build();
```
