# Windows Standalone

## Manual SSL Installation

Download the SSL Certificate: 

[SSL Proxy Certificate](https://wavenetcloud.netsweeper.com/webadmin/tools/download_proxy_cert.php)

![win-sa1](media/windows-sa/win-sa1.png)

![win-sa2](media/windows-sa/win-sa2.png)

![win-sa3](media/windows-sa/win-sa3.png)

![win-sa4](media/windows-sa/win-sa4.png)

![win-sa5](media/windows-sa/win-sa5.png)

![win-sa6](media/windows-sa/win-sa6.png)

## Manaul wagent Installation

open a command prompt with Administrator privileges, this must be CMD and not Powershell.

The command we need to run to install the software is (change the TRANSFORMS=… part to match the MST for the school):

``` cmd
msiexec /i "wagent.msi" /qn TRANSFORMS="123-4567 wagent transform filemst.mst"
```

## Manual Client Filter Installation

open a command prompt with Administrator privileges, this must be CMD and not Powershell.

The command we need to run to install the software is (change the TRANSFORMS=… part to match the MST for the school):

``` cmd
msiexec /i "nMonitor Client.msi" /qn TRANSFORMS="123-4567 nMonitor transform filemst.mst"
```

Once this is installed you will see the below icon in the system tray

![win-cficon](media/windows-sa/win-cficon.png)