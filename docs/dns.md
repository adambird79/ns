# DNS Filtering

Netsweeper support DNS filtering, this is a one policy solution per **External IP** 

DNS Server addresses available upon request. 

## DNS Client

When creating the Client in "Policies" -> "Clients", click the "+" to add a new network

Group – this should be the group you want to apply to DNS filtering
Client Type – set this to “Workstation Address”
Client Settings:
Client Name – DFE-CODE_DNS e.g. 123-4567_DNS 
IP Address or Range – This should be the Network Address e.g. 10.1.2.0
Subnet Mask: this should be the subnet mask for the network e.g. 255.255.255.0

!!! NOTE "Client Name"
    This is the only time we **do not** append the client name with **@DFE-CODE**

