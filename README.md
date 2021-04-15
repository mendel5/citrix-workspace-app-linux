# citrix-workspace-app-linux
How to install the Citrix Workspace App (formerly Citrix Receiver) on Linux. The downloaded file is also known as `icaclient`.

1. Download the latest version of the Citrix Workspace App from the Citrix website:
- [https://www.citrix.com/downloads/workspace-app/linux/](https://www.citrix.com/downloads/workspace-app/linux/)
- If you need an older version, you can still download the Citrix Receiver app: [https://www.citrix.com/downloads/citrix-receiver/linux/](https://www.citrix.com/downloads/citrix-receiver/linux/)

2. Install the downloaded file

3. During the installation process you might get asked: "`Do you want to install the app protection component?`" where you have to choose between `Yes` and `No`. You can decide whether to install the app protection or not based on this information: [https://docs.citrix.com/en-us/citrix-virtual-apps-desktops/secure/app-protection.html](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops/secure/app-protection.html) Selecting `No` should be fine.

4. When trying to log in, you might get the following error:
```
Citrix Workspace

SSL error
Contact your help desk with the following information:
You have not chosen to trust "USERTrust RSA Certification Authority",
the issuer of the server's security certificate (SSL error 61).
```

5. To fix this issue, execute the following commands in your Linux terminal:
```
sudo -H ln -s /usr/share/ca-certificates/mozilla/* /opt/Citrix/ICAClient/keystore/cacerts/

sudo -H /opt/Citrix/ICAClient/util/ctx_rehash
```
Source: [https://return42.github.io/handsOn/citrix/index.html](https://return42.github.io/handsOn/citrix/index.html) (German)

6. Try logging in again. It should work now.

7. For security reasons you might want to adjust the further configuration recommendations in the config files.

Location:
```
/opt/Citrix/ICAClient/config/wfclient.template
/opt/Citrix/ICAClient/nls/<lang>/wfclient.template
```

Change to:
```
[WFClient]
...
CREnabled=False
CDMAllowed=Off
ClientPrinterQueue=Off
ClientManagement=Off
ClientComm=Off
```
Source: [https://return42.github.io/handsOn/citrix/index.html#konfiguration](https://return42.github.io/handsOn/citrix/index.html#konfiguration)

8. You might be unsure whether to use the `Disconnect` button or the `Sign Out` button in Citrix. 
- Disconnecting by hitting “X” in the top right of the screen or selecting “Disconnect” from the connection bar will leave your session as is on the server with applications remaining open. This disconnected state does not save your documents so be sure to save any work before disconnecting. When you reconnect to your disconnected session it should login right as you left it with the running applications. Note that your organization may enforce a stricter logoff policy so your session may be logged out before you are able to return to it.
- Logging off/Signing out means fully logging off of Citrix and signing out of your profile. This closes all open applications and closes your session requiring a fresh login next time you connect. Note that your organization may have an enforced daily logoff policy.

Source: [https://support.virsage.com/kb/article/8--logging-off-versus-disconnecting-from-the-citrix-desktop/](https://support.virsage.com/kb/article/8--logging-off-versus-disconnecting-from-the-citrix-desktop/)
