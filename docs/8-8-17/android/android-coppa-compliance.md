## **Compliance with COPPA**



**This is not mandatory, but only if your app has to be COPPA Compliant**

To enable COPPA filter in GreedyGame's Native Android SDK you can enable it by calling the method `enableCOPPAFilter(true)` in `GreedyGameAgent.Builder` instance.

```Java tab= hl_lines="4"
GreedyGameAgent greedyGameAgent = new GreedyGameAgent.Builder(activity)
    .setGameId(GAME_ID_CREATED) //e.g 00100100
    .addUnitId(ADUNIT_CREATED) //e.g slot-1000
    .enableCOPPAFilter(true)
     ---"other builder methods"---
    .build();
```
