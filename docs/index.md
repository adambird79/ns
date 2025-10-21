---
hide:
- toc
---
## Netsweeper Process

### onboarding documents

* Complete the Netsweeper onboarding documentation and send over to the Netsweeper Account Manager

### Netsweeper Webadmin

* Is a Directory Sync required? 
    * Is it an Intune / EntraID deployment - Create [EntraID Sync](Netsweeper-webadmin.md#entraid-sync-microsoft-graph)
    * Does the customer have Radius (If RADIUS is used we will need to work with Netsweeper support to setup)
* If no additional complexity create groups in [Active Directory](Windows-AD.md#create-filtering-groups) and create matching groups in [Netsweeper](Netsweeper-webadmin.md#groups-policies)
* Add [Client IP Range(s)](Netsweeper-webadmin.md#clients)
* Create [wagent config](Netsweeper-webadmin.md#wagent)
* Create [Client Filter Config](Netsweeper-webadmin.md#client-filer-onguard)
* Create [Reports](Netsweeper-webadmin.md#reports)
* Create [User Accounts](Netsweeper-webadmin.md#acounts) for onGuard

### Windows Pre-Deployment

* Create the MST file for the [wagent](windows-build-clients.md#wagent-build-mst)
* Create the MST file for the [Client Filter](windows-build-clients.md#client-filter-build-mst)
* Deploy the [SSL certificate](Windows-AD.md#deploying-ssl-certificate)
!!! Warning "Warning"
    If we are moving from Netsweeper to Netsweeper the wagent and client filter should deployed during the switchover
* Create the [wagent GPO](Windows-AD.md#deploy-the-wagent) only if not using **Netsweeper** already
* Create the [Client Filter GPO](Windows-AD.md#deploy-the-client-filter)
* Enable the wagent GPO
* **Leave the Client Filter GPO Disabled** 

### Other Pre-Deployment

* Deploy the SSL certificate to any other devices [IOS](Apple.md#ssl-certificate), [Chromebook](Chromebook.md#ssl-certificate), [Android](Android.md#ssl-certificate) etc. 

## Deployment

### Windows Deployment

* Deploy the wagent [wagent](Windows-AD.md#deploy-the-wagent) (If not already deployed)
* Test the Filtering
* Deploy the Client Filter [Client Filter GPO](Windows-AD.md#deploy-the-client-filter)
* Test the Monitoring

### IOS Deployment

Deploy the SSL Certificate and "Client Filter" browser via the [MDM](Apple.md#mdm-guides)

### Chromebook Deployment

Deploy the [SSL Certificate](Chromebook.md#ssl-certificate)
Deploy the [Wagent Extension](Chromebook.md#wagent)
Deply the [Client Filter Extension](Chromebook.md#client-filter) (After or during Go-Live)
