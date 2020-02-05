**Support for User Certificates**

To verify the build we need to inpect the  requests coming from the SDK. Add the following configuration,this will only trust the certificates in debug release.

* The steps to add this are
    *  Create a `network_security_config.xml` file under `res/xml` in the project
    *  Paste the following content into it.
    ```xml
    <network-security-config>
        <debug-overrides>
            <trust-anchors>
                <!-- Trust user added CAs while debuggable only -->
                <certificates src="user" />
            </trust-anchors>
        </debug-overrides>
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

!!! WARNING
    * <font size="3" color="red">**Ensure that you have added the network_security_config file**</font>
