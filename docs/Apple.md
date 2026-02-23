---
date:
    create: 2025-10-17
    modified: 2026-02-23
tags:
    - Apple
    - IOS
    - iPad
    - MacOS
---
# Apple

## IOS

The nMonitor app should be purchased from the MDM (this is free). nMonitor is a replacement browser and to ensure monitoring is effective any other browsers should be disabled via the MDM

Where a MDM is not in-place we can only install the SSL certificate and enable filtering on the devices, note this would be a manual process adding time to the project.

### Requirements

!!! Warning "MDM"
    A MDM Solution is required to use the Client Filter on IOS

For the IOS replacement "Clint Filter" browser the device must be running IOS 14.0 or later

![ios](media/apple/ios.png)

### MDM Guides

#### Intune

##### SSL Certificate

##### Clint Filter (Replacement Browser)
To setup Microsoft Endpoint Manager for you will need to have the client filter plist files prepared already.

Login to: [Intune Admin](https://intune.microsoft.com){:target="_blank"} 

Then go to “Apps” -> “IOS/iPadOS”

![Apps](media/apple/apple-intune1.png)

Then click “+ Add” and then on the new blade select the drop down and “iOS store app” once selected click “Select”

![apple intune2](media/apple/apple-intune2.png)

On this next screen select “Search the App Store”

![apple intune3](media/apple/apple-intune3.png)

Search for “Netsweeper” this returns the fewest results

![apple intune4](media/apple/apple-intune4.png)

Once selected you will the following screen

![apple intune5](media/apple/apple-intune5.png)

Click “Next” and the assign to the groups / devices that should be receiving the app. Then on the next screen click “Create”.

Once the App is created, we need to push the configuration out to the App. To do this we need to create a configuration policy in “App Configuration Policies”.

Still under “Apps” click the “App configuration policies" then click the “+ Add” and select "Managed Devices.

![apple intune6](media/apple/apple-intune6.png)

On this next page we need to complete the following:

Name – Should be something identifiable (e.g. IOS – Netsweeper Client Filter – Pupil)

Platform: iOS/iPadOS

Targeted app: click “Select app” and find the “Netsweeper Client Filter” in the list

![apple-intune7](media/apple/apple-intune7.png)

The next screen we need to import the plist settings, for “Configuration settings format” I select “Enter XML data”, now in the box at the bottom we need to enter the XML from the plist, inTune only accepts the XML between the tags <dict> and </dict> as below:

![apple-intune8](media/apple/apple-intune8.png)

Click “Next” and assign to the required groups and the under “Review + Create” click “Create”

```xml
<?xml version="1.0" encoding="UTF-8"?\>

<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN"
"http://www.apple.com/DTDs/PropertyList-1.0.dtd"\>

<plist version="1.0"\>

<dict\>

    <key\>configedit\</key\>

    <string\>-p filter.wavenetcloud.netsweeper.com:3431 -y
netsweeper_brand -f 958209 -n {{username}} -d DFE-CODE -g nsw_pupil@DFE-CODE -a DFE-CODE -A DFE-CODE</string\>

</dict\>

</plist\>
```

#### Moysle

``` xml
<dict>
    <key>configedit</key>
    <string>-p filter.wavenetcloud.netsweeper.com:3431 -y netsweeper_brand -f 958209 -n %DeviceName% -d DFE-CODE -g nsw_pupil -a DFE-CODE -A DFE-CODE</string>
</dict>
```
In Mosyle the available variables are shown when you go to create the app configuration, the most useful will be %DeviceName% (make sure no spaces in the name) and %SerialNumber%

#### JAMF

#### Lightspeed

``` xml
<?xml version="1.0" encoding="UTF-8"?\>

<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN"
"http://www.apple.com/DTDs/PropertyList-1.0.dtd"\>

<plist version="1.0"\>

<dict\>

    <key\>configedit\</key\>

    <string\>-p filter.wavenetcloud.netsweeper.com:3431 -y
netsweeper_brand -f 958209 -n %devicename%@123-4567 -d 123-4567 -g nsw_pupil\</string\>

</dict\>

</plist\>
```
Notice LightspeedMDM requires the DFE code on the "-n" as well as the "-d" options, also note that device names will not show correctly if they have a space in the name.

#### Meraki

### IOS Manual SSL Installation

To manually install the SSL Certificate see Apple support: [Trust manually installed certificate](https://support.apple.com/en-us/102390){:target="_blank"}

## MACOS (Manual Installation)

The Wavenet Helpdesk will generate the MACOS Wagent and Client Filter configurations for the below.

### SSL Installation

[SSL Proxy Certificate](https://wavenetcloud.netsweeper.com/webadmin/tools/download_proxy_cert.php)

Set the permissions on the SSL certificate as below:

![macos-ssl1](media/apple/macos-ssl1.png)


### WAGENT

Download the latest [WAgent v4.50.54.54](https://repo.netsweeper.com/clientfilter/netsweeper/wagent/Netsweeper%20Workstation%20Agent%20-%204.50.54.54-mac.pkg)

Install the WAgent package, this can be installed in the same way any other MacOS app is installed. Double Click the pkg file and follow the onscreen instructions.

![macos-wagent1](media/apple/macos-wagent1.png)

![macos-wagent2](media/apple/macos-wagent2.png)

![macos-wagent3](media/apple/macos-wagent3.png)

![macos-wagent4](media/apple/macos-wagent4.png)

Witht the com.netsweeper.wagent.plist supplied by the Wavenet Helpdesk, copy “com.netsweeper.wagent.plist” to “/Library/LaunchAgents/com.netsweeper.wagent.plist” you can use the terminal and the command 

``` zsh
sudo cp com.netsweeper.wagent.plist /Library/LaunchAgents/com.netsweeper.wagent.plist
```

Once this file is copied into place you should restart the Macbook.
 
### Client Filter


