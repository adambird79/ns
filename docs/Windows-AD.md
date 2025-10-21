---
date:
    created: 2025-10-17
---
# Windows Active Directory Setup

## Windows Active Directory Sync

### Netsweeper Service Account

Create an account for the Netsweeper user, this user account only need to be a member of “Domain Users” and should NOT be a “Domain Administrator”

First check the “Advanced Features” is enabled under the View menu in Active Directory.

![Service Account1](media/windows-ad/win-sa1.png)

If needed create a new Organisational Unit for this user otherwise create this user account with other service accounts.

Right click on the white space in the folder and select “New” -> “User”

![service account2](media/windows-ad/win-sa2.png)

Fill out the form naming the account to fit in with the schools’ naming conventions. Click “Next” when done.

![sevice account3](media/windows-ad/win-sa3.png)

Set a complex password and tick the “Password never expires” box, then click “Next”

![service account4](media/windows-ad/win-sa4.png)

On the next screen, click “Finish”

![service accout5](media/windows-ad/win-sa5.png)

Once we have created the user either double click on the user account or right click and select “Properties”

When the screen loads you should the “Attribute Editor” tab, if not go back and make sure you enabled “Advanced Features” under the view menu. Select the “Attribute Editor” tab.

![service account6](media/windows-ad/win-sa6.png)

In the “Attribute Editor" tab scroll down and find the entry “distinguishedName” and click the “View” button. The value will look something like this: “CN=svc netsweeper,OU=Netsweeper,DC=domain,DC=local” make a note of this value Netsweeper requires this for the LDAP Sync.

![service account7](media/windows-ad/win-sa7.png)

### Create Filtering Groups

To create the filtering groups go to the “Organisational Unit” where you store Active Directory groups or create a new location. Right click in the white space on the right and select “New” -> “Group”

![win fg1](media/windows-ad/win-fg1.png)

The Group name should be set here with the prefix nsw_
So in the example below we have setup the filtering group for staff with the name nsw_staff

![win fg2](media/windows-ad/win-fg2.png)

Once the groups have been created add the required users to the group, groups can be nested in here but be careful making sure a user doesn’t end up being a member of multiple filtering groups.

### Deploying SSL Certificate

Before anything we need to grab a copy of the SSL certificate for Netsweeper this can be downloaded from:

[SSL Proxy Certificate](https://wavenetcloud.netsweeper.com/webadmin/tools/download_proxy_cert.php)

Create a new Group Policy Object named something like "SSL"

![win ssl1](media/windows-ad/win-ssl1.png)

Right click and "Edit" the new policy

![win ssl2](media/windows-ad/win-ssl2.png)

![winssl3](media/windows-ad/win-ssl3.png)

![winssl4](media/windows-ad/win-ssl4.png)

![winssl5](media/windows-ad/win-ssl5.png)

![winssl6](media/windows-ad/win-ssl6.png)

![winssl7](media/windows-ad/win-ssl7.png)

![winssl8](media/windows-ad/win-ssl8.png)

![winssl9](media/windows-ad/win-ssl9.png)

### wagent build MST

### Clinet Filter build MST

### Windows Group Policy

#### Deploy the Wagent

#### Deploy the Client Filter

### Windows Manual Installation