## Developer Reference

These are all the functions available for you from the GreedyGameSDK listed by Object

### GreedyGameAgent

| Method                                                                        | Introduced Since | Description                                                                                                        |   |   |
|-------------------------------------------------------------------------------|------------------|--------------------------------------------------------------------------------------------------------------------|---|---|
| void init()                                                                   | [beginning]      | Initiates the ad loading process.                                                                                  |   |   |
| Activity getActivity()                                                        | [beginning]      | Returns the activity instance provided via builder or null if Garbage Collected.                                   |   |   |
| Context getContext()                                                          | [beginning]      | Returns the context instance provided via builder or null if Garbage Collected.                                    |   |   |
| void showFloat(Activity,String)                                               | [deprecated]     | Shows float unit. Will be removed in future releases.                                                              |   |   |
| void removeFloat(String)                                                      | [deprecated]     | Removes float unit. Will be removed in future releases.                                                            |   |   |
| void removeAllFloat()                                                         | [deprecated]     | Removes all float units. Will be removed in future releases.                                                       |   |   |
| void showUII(String)                                                          | [beginning]      | Opens engagement window for the ad unit passed.                                                                    |   |   |
| String getPath(String)                                                        | [beginning]      | Returns the ad unit path for the unit passed. Returns empty if the unit is not yet ready or is not valid.          |   |   |
| String getSDKVersion()                                                        | [beginning]      | Returns the GreedyGameSDK version.                                                                                 |   |   |
| boolean isCampaignAvailable()                                                 | [beginning]      | Returns true if a campaign is available.                                                                           |   |   |
| void setCampaignStateListener(CampaignStateListener campaignStateListener)    | [beginning]      | Registers a listener for SDK events like onError,onAvailable or onUnavailable                                      |   |   |
| void removeCampaignStateListener(CampaignStateListener campaignStateListener) | [beginning]      | Removes the registered event listener                                                                              |   |   |
| void startEventRefresh()                                                      | [beginning]      | This will initiate a refresh which will fetch new ads.                                                             |   |   |
| void sendCrash(Throwable throwable, boolean isFatal)                          | [beginning]      | Send a crash to GreedyGame                                                                                         |   |   |
| void sendCrash(String error, boolean isFatal)                                 | [beginning]      | Send a crash to GreedyGame                                                                                         |   |   |
| void setPrivacyOptions(PrivacyOptions options)                                | [beginning]      | Sets GDPR Privacy Options.[Click here to know more](/8-8-17/android/android-gdpr-compliance/) |   |   |
| boolean isSdkInitialized();                                                   | v8.8.17          | Returns true if SDK is initialized.                                                                                |   |   |
|                                                                               |                  |                                                                                                                    |   |   |

### GreedyGameBuilder
| Method | Introduced Since | Description |
|------------------------------------------------------------------------|------------------|---------------------------------------------------------------------------------------------------------------------|
| Builder Builder(Activity) | [beginning] | Returns the Builder instance with the provided activity |
| Builder Builder(Context) | [beginning] | Returns the Builder instance with the provided context |
| Builder enableAdmob(boolean) | [beginning] | Enables Admob as a monetization partner. Default is false |
| Builder enableFacebook(boolean value) | [beginning] | Enables Facebook as a monetization partner. Default is false |
| Builder enableMopub(boolean value) | [beginning] | Enables Mopub as a monetization partner. Default is false |
| Builder enableCrash(boolean value) | [beginning] | If enabled will send crashes over to GreedyGameServers |
| void showUII(String) | [beginning] | Opens engagement window for the ad unit passed.  |
| Builder enableCOPPAFilter(boolean value) | [beginning] | Enables COPPA. Default is false |
| Builder enableCCPA(boolean value) | [beginning] | Enables CCPA. Default is false |
| Builder setGameId(String gameId) | [beginning]  | Provide your appId or gameId created in your GreedyGameAccount |
| Builder addUnitId(String unitId) | [beginning] | Add a single ad unit for which ad needs to be created. If you have multiple units, use addUnitList(List unitIdList) |
| Builder addUnitList(List unitIdList) | [beginning] | Add a list of ad units for which ad needs to be created.  |
| Builder withAgentListener(CampaignStateListener campaignStateListener) | [beginning] | Register a campaign state listener. |
| GreedyGameAgent build | [beginning] | Returns an instance of GreedyGameAgent if all conditions are checked. Returns null if failed. |
| Builder gameEngine(String value) | [beginning] | Used only by GameEngines |
| Builder engineVersion(String version) | [beginning] | Used only by GameEngines |
|  |  |  |