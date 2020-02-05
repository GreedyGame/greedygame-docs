

You should refresh the ads to maximize your revenue potential.

Refreshing of ads can be of 2 types:

* **Time Based Refresh**: The most common way to refresh ads is based on regular intervals of time. Time based refresh can be used in both apps and games. The countdown timer to call refresh should be started when the first unit is displayed.

* **Event Based Refresh**: More suited to games, ads can be refreshed during natural pauses in your gameflow. Typical examples would be to include the game pause menu, user trying to restart a level or move to another level, death of a character etc. 


GreedyGame SDK by default doesn’t refresh the ads in between a session. For this you need to call the following API.

```java


void reloadAd(){ // Call this function to refresh ads.
        new CountDownTimer(70000,1000){

            @Override
            public void onTick(long millisUntilFinished) {

            }

            @Override
            public void onFinish() {
                greedyGameAgent.startEventRefresh();
            }
        }.start();
    }
```
This will give a callback at the same CampaignStateListener set earlier and the flow would happen as earlier. The units should be properly updated on both `onAvailable()` and `onUnavailable()` callbacks.

!!! warning

    **There is a 70 seconds minimum threshold applied to this API. This means that if this API gets called again within 70 seconds of the previous call, it is ignored. There won't be callbacks to onUnavailable, onAvailable or onError functions.**
