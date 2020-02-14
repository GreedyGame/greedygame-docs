## **Testing of Ads**

Now that you have successfully integrated with GreedyGame Native Ads SDK, now is the time to test the integration.

GreedyGame recommends an easy way to test the ads by following the below steps

Click on **Testing** in the left panel, or click on **Get Test Ads**

<img src="/img/newiOS/a_test_ads.png" alt="" style="margin-left: 50px" width="652" height="580">

If you are testing for the first time, you will have to add a test device. Click on **Add New Device** in the left panel or on **Create**

<img src="/img/newiOS/b_test_ads.png" alt="" style="margin-left: 50px" width="650" height="280">

Select the app you want to test by clicking on **App ID** and enter the **Advertising ID** of the iOS device you want to get test ads on
   
   * Install the app <a target="_blank" rel="noopener noreferrer" href="https://apps.apple.com/us/app/myidfa/id1099872451
">MyIDFA</a> or any other apps like <a target="_blank" rel="noopener noreferrer" href="https://apps.apple.com/bg/app/whatsmyidfa/id1313131350">WhatsMyIDFA</a>, <a target="_blank" rel="noopener noreferrer" href="https://apps.apple.com/us/app/my-device-id-by-appsflyer/id1192323960">DeviceId</a>..etc from AppStore to get your device Advertising id.

   * Please make sure that the app you are testing should be on the device you have added for testing.

<img src="/img/newiOS/c_test_ads.png" alt="" style="margin-left: 50px" width="650" height="330">

Once your device is added it will be shown on the Panel

<img src="/img/newiOS/d_test_ads.png" alt="" style="margin-left: 50px" width="650" height="272">

Click on **Get Test Ads** to start getting test ads. Open your app in the testing device to see the test ads.

<center><img src="/img/newiOS/e_test_ads.png" alt="" style="margin-left: 50px" width="650" height="296"></center>

!!! Important "Remove simulator architecture from GreedyGame SDK"
    Greedygame SDK has simulator architecture.You need to remove this architecture by <a target="_blank" rel="noopener noreferrer" href="https://github.com/GreedyGame/ios-native-plugin">add the script</a> under `Note` section as run script in build phases.

## **Build Verification**

Once your integration is complete, share your app via TestFlight to `arpit@greedygame.com`, so that our quality team can verify the integration.

!!! Warning
    
    **It is mandatory for the app to be approved by the GreedyGame Quality team, before making the app live.**