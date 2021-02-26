# citrix-workspace-app-linux
How to install the Citrix Workspace App (formerly Citrix Receiver) on Linux. The downloaded file is also known as `icaclient`.

1. Download the latest version of the Citrix Workspace App from the Citrix website:
- [https://www.citrix.com/downloads/workspace-app/linux/](https://www.citrix.com/downloads/workspace-app/linux/)
- If you need an older version, you can still download the Citrix Receiver app: [https://www.citrix.com/downloads/citrix-receiver/linux/](https://www.citrix.com/downloads/citrix-receiver/linux/)

2. Install the downloaded file

3. You might get the following error:
```
Citrix Workspace

SSL error
Contact your help desk with the following information:
You have not chosen to trust "USERTrust RSA Certification Authority",
the issuer of the server's security certificate (SSL error 61).
```

4. To fix this issue, execute the following commands in your Linux terminal:
```
sudo -H ln -s /usr/share/ca-certificates/mozilla/* /opt/Citrix/ICAClient/keystore/cacerts/
sudo -H /opt/Citrix/ICAClient/util/ctx_rehash
```
Source: [https://return42.github.io/handsOn/citrix/index.html](https://return42.github.io/handsOn/citrix/index.html) (German)

5. Try logging in again. It should work now.
