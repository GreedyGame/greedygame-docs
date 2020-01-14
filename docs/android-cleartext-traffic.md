**ClearText Traffic Support**

Add the following code snippets to your manifest file for cleartext traffic support. These are required as part of Android API level 9.0 compatibility. These are mandatory requirements for GreedyGame.

* The steps to add this are
    *  Create a `network_security_config.xml` file under `res/xml` in the project
    *  Paste the following content into it.
    ```xml
    <network-security-config>
    <domain-config cleartextTrafficPermitted="true">
      <domain includeSubdomains="true">api.greedygame.com</domain>
    </domain-config>
    </network-security-config>
    ```

    * In your manifest file add this as  `networkSecurityConfig`

    ```xml hl_lines="3"
    <application 
    ...
    android:networkSecurityConfig="@xml/network_security_config">
    ...
    </application>
    ```

    * Beginning with Android 9, HTTP library is removed from the bootclasspath and is not available to apps by default. To enable the usage add the following code snippet in manifest.

    ```xml hl_lines="3"
    <application>
    ...
    <uses-library android:name="org.apache.http.legacy" android:required="false"/>
    ...
    </application>
    ```

!!! WARNING
    * <font size="3" color="red">**Ensure that you have added the network_security_config file**</font>
