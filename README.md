
#  Meraki Captive Portal /w Zapier Integration
*Static HTML/JS/CSS Site for a Click-through Splash Page*

## Overview
Cisco Meraki provides cloud managed WiFi with the ability to host your own "Splash Page", which is a captive portal service for authenticating users to join the network. This concept is called an External Captive Portal (ExCaP). 

Meraki provides two splash page modes, **click-through** and **sign-on**. This application will use the click-through method.

Just host these files in the public directory on any web server such as Apache or Firebase Hosting, configure your Meraki SSID to use your server and that's it!

This version posts the form data to a Zapier webhook and is required for operation. 




### Sample URL received from Meraki to this page.
*You can use this URL to test your application without an access point*
```
http://localhost/?base_grant_url=https%3A%2F%2Fn143.network-auth.com%2Fsplash%2Fgrant&user_continue_url=http%3A%2F%2Fspeedof.me%2F&node_id=149624922840090&node_mac=88:15:44:60:1c:1a&gateway_id=149624922840090&client_ip=10.255.60.208&client_mac=f4:5c:89:9b:17:67
```

## Installation
* Host these files on a webserver
* Configure the Meraki wireless SSID with a Click-Through splash page authentication
    * Meraki Dashboard --> Configure --> Splash Page: Click-through
* Add the domain address of the webserver to the "Walled Garden" 
    * Meraki Dashboard --> Configure --> Access Control --> SSID:yourSSID --> Walled Garden.
    * Add the Zapier domain in your Walled Garden in the Meraki Dashboard `https://hooks.zapier.com`
    * Note: You will need to use the IP address instead of the domain name or contact Meraki Support to enable Walled Garden Domain Names
* Configure Zapier with a webhook
* Configure Meraki with a custom Splash URL
   * https://yourserver/index.html&zap_url=
   * Append a ```zap_url``` query with your Zap hook URL.
   ```
   https://dexterlabora.github.io/excap-clientjs-zapier/public/index.html?zap_url=https://hooks.zapier.com/hooks/catch/ffffff/ffffff/
   ```
  



## Sample URL paramater string received by client
```
https://yourserver/index.html?base_grant_url=https%3A%2F%2Fn143.network-auth.com%2Fsplash%2Fgrant&user_continue_url=http%3A%2F%2Fask.com%2F&node_id=149624921787028&node_mac=88:15:44:50:0a:94&gateway_id=149624921787028&client_ip=10.110.154.195&client_mac=60:e3:ac:f7:48:08:22&zap_url=https://hooks.zapier.com/hooks/catch/ffffff/ffffff/
```

## Screenshot
![alt screenshot](screenshot.png)
![alt zapier screenshot](zapier-screenshot.png)


## Additional Resources
http://developers.meraki.com/tagged/Splash-Pages

### Written by 
Cory Guynn
2016
www.InternetOfLEGO.com
