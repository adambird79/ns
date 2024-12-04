# Windows Configuration

## Netsweeper Service Account

Create an account for the Netsweeper user, this user account only need
to be a member of “Domain Users” and should **NOT** be a “Domain
Administrator”

First check the “Advanced Features” is enabled under the View menu in
Active Directory.

![AAD Advanced Enable](https://github.com/adambird79/netsweeper/blob/main/media/media/aad-advanced.jpg)

If needed create a new Organisational Unit for this user otherwise
create this user account with other service accounts.

Right click on the white space in the folder and select “New” -\> “User”

<img src="https://github.com/adambird79/netsweeper/blob/main/media/media/image2.png"
style="width:3.17717in;height:2.3622in"
alt="A screenshot of a computer program Description automatically generated" />

Fill out the form naming the account to fit in with the schools’ naming
conventions. Click “Next” when done.

<img src="https://github.com/adambird79/netsweeper/blob/main/media/media/image3.png"
style="width:3.63386in;height:3.14961in"
alt="A screenshot of a computer Description automatically generated" />

Set a complex password and tick the “Password never expires” box, then
click “Next”

<img src="https://github.com/adambird79/netsweeper/blob/main/media/media/image4.png"
style="width:3.61811in;height:3.14961in"
alt="A screenshot of a computer Description automatically generated" />

On the next screen, click “Finish”

<img src="https://github.com/adambird79/netsweeper/blob/main/media/media/image5.png"
style="width:3.63386in;height:3.14961in"
alt="A screenshot of a computer Description automatically generated" />

Once we have created the user either double click on the user account or
right click and select “Properties”

When the screen loads you should the “Attribute Editor” tab, if not go
back and make sure you enabled “Advanced Features” under the view menu.
Select the “Attribute Editor” tab.

<img src="https://github.com/adambird79/netsweeper/blob/main/media/media/image6.png"
style="width:3.50787in;height:4.72441in" />

In the “Attribute Editor" tab scroll down and find the entry
“distinguishedName” and click the “View” button. The value will look
something like this: “*CN=svc
netsweeper,OU=Netsweeper,DC=domain,DC=local”* make a note of this value
Netsweeper requires this for the LDAP Sync.

<img src="https://github.com/adambird79/netsweeper/blob/main/media/media/image7.png"
style="width:4.36519in;height:5.77164in"
alt="A screenshot of a computer program Description automatically generated" />

## Create Filtering groups

To create the filtering groups go to the “Organisational Unit” where you
store Active Directory groups or create a new location.

Right click in the white space on the right and select “New” -\> “Group”

<img src="https://github.com/adambird79/netsweeper/blob/main/media/media/image8.png"
style="width:3.29134in;height:2.3622in"
alt="A screenshot of a computer program Description automatically generated" />

The Group name should be set here with the prefix **nsw\_**

So in the example below we have setup the filtering group for staff with
the name **nsw_staff**

<img src="https://github.com/adambird79/netsweeper/blob/main/media/media/image9.png"
style="width:4.56314in;height:3.93805in"
alt="A screenshot of a group Description automatically generated" />

Once the groups have been created add the required users to the group,
groups can be nested in here but be careful making sure a user doesn’t
end up being a member of multiple filtering groups.

## Deploying SSL Certificate

Before anything we need to grab a copy of the SSL certificate for
Netsweeper this can be downloaded from:

<https://wavenetcloud.netsweeper.com/webadmin/tools/download_proxy_cert.php>

### Deploying SSL via Group Policy

<img src="https://github.com/adambird79/netsweeper/blob/main/media/media/image10.png"
style="width:4.13599in;height:1.8961in"
alt="A screenshot of a computer login Description automatically generated" />

<img src="https://github.com/adambird79/netsweeper/blob/main/media/media/image11.png"
style="width:3.53174in;height:4.18808in"
alt="A screenshot of a computer Description automatically generated" />

<img src="https://github.com/adambird79/netsweeper/blob/main/media/media/image12.png"
style="width:6.26806in;height:4.44792in" />

<img src="https://github.com/adambird79/netsweeper/blob/main/media/media/image13.png"
style="width:5.00394in;height:3.93701in"
alt="A screenshot of a certificate Description automatically generated" />

<img src="https://github.com/adambird79/netsweeper/blob/main/media/media/image14.png"
style="width:4.06693in;height:3.93701in"
alt="A screenshot of a computer Description automatically generated" />

<img src="https://github.com/adambird79/netsweeper/blob/main/media/media/image15.png"
style="width:5.5315in;height:3.93701in" />

<img src="https://github.com/adambird79/netsweeper/blob/main/media/media/image16.png"
style="width:4.11024in;height:3.93701in"
alt="A screenshot of a computer Description automatically generated" />

<img src="https://github.com/adambird79/netsweeper/blob/main/media/media/image17.png"
style="width:4.12598in;height:3.93701in"
alt="A screenshot of a computer Description automatically generated" />

<img src="https://github.com/adambird79/netsweeper/blob/main/media/media/image18.png"
style="width:4.09449in;height:3.93701in"
alt="A screenshot of a certificate Description automatically generated" />

### Deploying SSL manually

<img src="https://github.com/adambird79/netsweeper/blob/main/media/media/image19.png"
style="width:3.77953in;height:2.75591in"
alt="A screenshot of a computer error Description automatically generated" />

<img src="https://github.com/adambird79/netsweeper/blob/main/media/media/image20.png"
style="width:3.07087in;height:3.93701in" />

<img src="https://github.com/adambird79/netsweeper/blob/main/media/media/image21.png"
style="width:4.05906in;height:3.93701in" />

<img src="https://github.com/adambird79/netsweeper/blob/main/media/media/image22.png"
style="width:4.0748in;height:3.93701in" />

<img src="https://github.com/adambird79/netsweeper/blob/main/media/media/image23.png"
style="width:4.03543in;height:3.93701in"
alt="A screenshot of a computer Description automatically generated" />

<img src="https://github.com/adambird79/netsweeper/blob/main/media/media/image24.png"
style="width:4.04331in;height:3.93701in"
alt="A screenshot of a certificate Description automatically generated" />

## Deploying WAgent

The WAgent can be installed prior to going live with the filtering
system.

### Deploying WAgent Group Policy

In group policy management create a new group policy, setting the name
to fit in with the schools group policy naming conventions.

<img src="https://github.com/adambird79/netsweeper/blob/main/media/media/image25.png"
style="width:6.26806in;height:4.03264in" />

In this example we call the group policy “Software Deployment”

<img src="https://github.com/adambird79/netsweeper/blob/main/media/media/image26.png"
style="width:4.0839in;height:1.91693in"
alt="A screenshot of a computer Description automatically generated" />

Once created location the group policy and right click on this and
select “Edit”

<img src="https://github.com/adambird79/netsweeper/blob/main/media/media/image27.png"
style="width:4.02139in;height:3.9693in" />

Once this opens browse to “Computer Configuration” -\> “Policies” -\>
“Software Settings” -\> “Software installation”

<img src="https://github.com/adambird79/netsweeper/blob/main/media/media/image28.png"
style="width:6.26806in;height:2.33958in"
alt="A screenshot of a computer Description automatically generated" />

Right click on the white space and select “New” -\> “Package”

<img src="https://github.com/adambird79/netsweeper/blob/main/media/media/image29.png"
style="width:3.39631in;height:2.5316in"
alt="A screenshot of a computer Description automatically generated" />

Here browse to the UNC path of the share where the software is stored.
In the below example we browse to the location
[\\DC01\Software](file:///\\DC01\Software) and select the MSI package
named “Netsweeper Workstation Agent - 4.40.54.54-windows.msi” and click
“Open”

<img src="https://github.com/adambird79/netsweeper/blob/main/media/media/image30.png"
style="width:6.26806in;height:4.44306in"
alt="A screenshot of a computer Description automatically generated" />

<img src="https://github.com/adambird79/netsweeper/blob/main/media/media/image31.png"
style="width:3.62551in;height:2.54202in"
alt="A screenshot of a software Description automatically generated" />

<img src="https://github.com/adambird79/netsweeper/blob/main/media/media/image32.png"
style="width:4.13542in;height:4.6875in" />

<img src="https://github.com/adambird79/netsweeper/blob/main/media/media/image33.png"
style="width:6.26806in;height:4.38889in"
alt="A screenshot of a computer Description automatically generated" />

<img src="https://github.com/adambird79/netsweeper/blob/main/media/media/image34.png"
style="width:4.15683in;height:4.71941in"
alt="A screenshot of a computer Description automatically generated" />

### Deploying WAgent (Manual Installation)

open a command prompt with Administrator privileges, this must be
**CMD** and not Powershell.

The command we need to run to install the software is (change the
TRANSFORMS=… part to match the MST for the school):

msiexec /i "wagent.msi" /qn TRANSFORMS="123-4567 wagent transform
filemst.mst"

## Deploying nMonitor

nMonitor is the software required for the filtering with onGuard, this
should be deployed when ready to “Go Live”

### Deploying nMonitor – Group Policy

In group policy management create a new group policy, setting the name
to fit in with the schools group policy naming conventions.

<img src="https://github.com/adambird79/netsweeper/blob/main/media/media/image25.png"
style="width:6.26806in;height:4.03264in" />

In this example we call the group policy “Software Deployment”

<img src="https://github.com/adambird79/netsweeper/blob/main/media/media/image26.png"
style="width:4.0839in;height:1.91693in"
alt="A screenshot of a computer Description automatically generated" />

Once created location the group policy and right click on this and
select “Edit”

<img src="https://github.com/adambird79/netsweeper/blob/main/media/media/image27.png"
style="width:4.02139in;height:3.9693in" />

Once this opens browse to “Computer Configuration” -\> “Policies” -\>
“Software Settings” -\> “Software installation”

<img src="https://github.com/adambird79/netsweeper/blob/main/media/media/image28.png"
style="width:6.26806in;height:2.33958in"
alt="A screenshot of a computer Description automatically generated" />

Right click on the white space and select “New” -\> “Package”

<img src="https://github.com/adambird79/netsweeper/blob/main/media/media/image29.png"
style="width:3.39631in;height:2.5316in"
alt="A screenshot of a computer Description automatically generated" />

Here browse to the UNC path of the share where the software is stored.
In the below example we browse to the location
[\\DC01\Software](file:///\\DC01\Software) and select the MSI package
named “nMonitor Client – 11.60.54.1 win64.msi” and click “Open”

<img src="https://github.com/adambird79/netsweeper/blob/main/media/media/image35.png"
style="width:6.26806in;height:4.67361in"
alt="A screenshot of a computer Description automatically generated" />

Once this has been selected, and clicked “Open” the next screen we need
to change the default option from “Assigned” to “**Advanced**”

<img src="https://github.com/adambird79/netsweeper/blob/main/media/media/image31.png"
style="width:3.62551in;height:2.54202in"
alt="A screenshot of a software Description automatically generated" />

When the option has been set to “Advanced” click Ok. Then select the tab
“Modifications” on the screen that loads.

<img src="https://github.com/adambird79/netsweeper/blob/main/media/media/image36.png"
style="width:4.07292in;height:4.67708in" />

On the “Modifications” screen click “Add” and you should see the MST
file, assuming you have stored this in the same location as the MSI
installation file.

<img src="https://github.com/adambird79/netsweeper/blob/main/media/media/image37.png"
style="width:4.13542in;height:4.75in" />

<img src="https://github.com/adambird79/netsweeper/blob/main/media/media/image38.png"
style="width:5.26772in;height:3.93701in"
alt="A screenshot of a computer Description automatically generated" />

Once the MST is selected, click Ok.

On the next screen, click OK again and this is now configured.

<img src="https://github.com/adambird79/netsweeper/blob/main/media/media/image39.png"
style="width:3.43701in;height:3.93701in"
alt="A screenshot of a computer program Description automatically generated" />

## 

### nMonitor (Manual Installation)

open a command prompt with Administrator privileges, this must be
**CMD** and not Powershell.

The command we need to run to install the software is (change the
TRANSFORMS=… part to match the MST for the school):

msiexec /i "nMonitor Client - 11.60.54.1 win64.msi" /qn
TRANSFORMS="123-4567 nMonitor transform filemst.mst"

<img src="https://github.com/adambird79/netsweeper/blob/main/media/media/image40.png"
style="width:6.26806in;height:1.71111in"
alt="A computer screen with text on it Description automatically generated" />

Once this is installed you will see the below icon in the system tray

<img src="https://github.com/adambird79/netsweeper/blob/main/media/media/image41.png"
style="width:0.40631in;height:0.30213in" />

# Create Netsweeper Windows Agents

To create the Netsweeper Windows agents you need to be able to edit the MSI files, to do this you will need to install ORCA, below is the Microsoft link on how to do this:

[Installing ORCA](https://learn.microsoft.com/en-us/windows/win32/msi/orca-exe)

## WAgent

Download the latest **GA** version from: [Netsweeper Helpdesk](https://helpdesk.netsweeper.com/docs/8_2_Docs/8_2_Netsweeper_Docs/Content/Release_Notes/WAGENT_Release_Notes/Contents__Wagent_Release_Notes.htm)

Open Microsoft ORCA and open the WAGent.MSI, then go to "Transform" -> "New Transform"

![ORCA_WAgent](https://github.com/adambird79/netsweeper/blob/main/media/media/orca_WAGENT_blank.jpg)

On the left select "Property" and we need to update the NS_WAGENT_ARGS line, with the following

``` bash
-w wavenetcloud.netsweeper.com -d nsagent-login.netsweeper.com -s nsw -g {LOGON GUID}-L {LOGOUT GUID} -t 600 -i -l -v -F -S
```
Change the LOGON and LOGOUT GUIDs with the GUID for the WAgent from the Netsweeper page "Tools" -> "Agent"

![WAgent](https://github.com/adambird79/netsweeper/blob/main/media/media/wagent.jpg)

![ORCA WAgent](https://github.com/adambird79/netsweeper/blob/main/media/media/orca_WAGENT.jpg)

CONFIGEDIT
``` bash
-p filter.wavenetcloud.netsweeper.com:3431 -y {BRAND_NAME} -f 923649 -i nsw -d {DFE-CODE} -c -s
```

NMONITOR_CONFIG
``` bash
--webadmin=https://wavenetcloud.netsweeper.com/webadmin/ --log=0 --ocr_disabled=0 --ocr_image_compare_disabled=0 --ocr_matched_category_compare=1 --ocr_disable_words_compare=0 --ocr_disable_input_compare=0 --ocr_timeout_recapture=5 --keylog_disabled=0 --keylog_buffer_size=1024 --keylog_timeout_send=1 --keylog_timeout_clear=30 --image_quality=50 --image_target_width=0 --image_target_height=0 --tray_disabled=0 --tray_menu_disabled=0
```

NUPDATE_ENABLED
``` bash
1
```
Once the settings have been set go to "Transforms" -> "Generate Transform" and then save the MST file

## nMonitor

Download the latest **GA** version from: [Netsweeper Helpdesk](https://helpdesk.netsweeper.com/docs/8_2_Docs/8_2_Netsweeper_Docs/Content/Client_Filter/Client_Filter_Release_Notes/12_Client_Filter_Releases_and_Downloads/Contents_Client_Filter_12_Releases_and_Downloads.htm)

Open Microsoft ORCA and open the WAGent.MSI, then go to "Transform" -> "New Transform"

![ORCA nMonitor](https://github.com/adambird79/netsweeper/blob/main/media/media/orca_nmon.jpg)

On the left select "Property" and we need to update the following lines CONFIGEDIT, NMONITOR_CONFIG, NUPDATE_ENABLED, with the following

![ORCA nMonitor](https://github.com/adambird79/netsweeper/blob/main/media/media/orca_nmon_blank.jpg)

CONFIGEDIT
``` bash
-p filter.wavenetcloud.netsweeper.com:3431 -y {BRAND_NAME} -f 923649 -i nsw -d {DFE-CODE} -c -s
```
NMONITOR_CONFIG
``` bash
--webadmin=https://wavenetcloud.netsweeper.com/webadmin/ --log=0 --ocr_disabled=0 --ocr_image_compare_disabled=0 --ocr_matched_category_compare=1 --ocr_disable_words_compare=0 --ocr_disable_input_compare=0 --ocr_timeout_recapture=5 --keylog_disabled=0 --keylog_buffer_size=1024 --keylog_timeout_send=1 --keylog_timeout_clear=30 --image_quality=50 --image_target_width=0 --image_target_height=0 --tray_disabled=0 --tray_menu_disabled=0
```
NUPDATE_ENABLED
```bash
1
```
Once the settings have been set go to "Transforms" -> "Generate Transform" and then save the MST file