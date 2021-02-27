# citrix-workspace-app-linux
How to install the Citrix Workspace App (formerly Citrix Receiver) on Linux. The downloaded file is also known as `icaclient`.

1. Download the latest version of the Citrix Workspace App from the Citrix website:
- [https://www.citrix.com/downloads/workspace-app/linux/](https://www.citrix.com/downloads/workspace-app/linux/)
- If you need an older version, you can still download the Citrix Receiver app: [https://www.citrix.com/downloads/citrix-receiver/linux/](https://www.citrix.com/downloads/citrix-receiver/linux/)

2. Install the downloaded file

3. During the installation process you might get asked: "`Do you want to install the app protection component?`" where you have to choose between Yes and No. You can decide whether to install the app protection or not based on this information: [https://docs.citrix.com/en-us/citrix-virtual-apps-desktops/secure/app-protection.html](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops/secure/app-protection.html)

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

7. For security reasons you might want to check the other configuration recommendations at [https://return42.github.io/handsOn/citrix/index.html#konfiguration](https://return42.github.io/handsOn/citrix/index.html#konfiguration).
