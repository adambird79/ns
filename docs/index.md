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
    * Does the customer have Radius
* If no additional complexity create groups in [Active Directory](Windows-AD.md#windows-active-directory-setup) and create matching groups in [Netsweeper](Netsweeper-webadmin.md#groups-policies)
* Add [Client IP Range(s)](Netsweeper-webadmin.md#clients)
* Create [wagent config](Netsweeper-webadmin.md#wagent)
* Create [Client Filter Config](Netsweeper-webadmin.md#client-filer-onguard)
* Create [Reports](Netsweeper-webadmin.md#reports)
* Create [User Accounts](Netsweeper-webadmin.md#users) for onGuard

### Windows Pre-Deployment

* Create the MST file for the [wagent](Windows-AD.md#wagent-build-mst)
* Create the MST file for the [Client Filter](Windows-AD.md#clinet-filter-build-mst)
* Deploy the SSL certificate
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

* Deploy the wagent [wagent](Windows-AD.md#deploy-the-wagent)
* Test the Filtering
* Deploy the Client Filter [Client Filter GPO](Windows-AD.md#deploy-the-client-filter)
* Test the Monitoring

### IOS Deployment

Text here

### Chromebook Deployment

Text here
