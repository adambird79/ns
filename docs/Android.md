---
date:
    create: 2025-10-17
tags:
    - Android
    - Google
---
# Android

## Requirements

!!! Warning "MDM"
    A MDM Solution is required to use the Client Filter on Android

## Limitations
Android devices require a connection to www.google.com to verify internet connectivity, so an Android device going through Netsweeper will report that it has no internet connection

The Netsweeper workaround is to add a new CNAME record on your local DNS server for your local Google domain(s) that points to forcesafesearch.google.com

Ideally any Android devices would need to be on a separate VLAN due to not inspecting the Google traffic.

## MDM Guides

### Intune

#### SSL Certificate