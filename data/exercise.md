## Some Hands On!

### Deploy VNET 

Deploy Vnet configurations illustrated in the **[Virtual Network Design and Segmentation](/data/design.md)**

* Create Public IP and Public IP Prefixes
* Create peering between HUB and SPOKE
* Deploy Nat Gateway and configure with spoke workload subnet. (Needed to manage public outbound)

### Deploy Private DNS Zone - (myorg.net)
    * Link Vnets
    * Resolve Vm's deployed in 2 different n/w

### Deploy Public DNS Zone
Deploy Public DNS Zone, Delegate to Azure DNS and create sub-domains.

* You need to have a domain from any provider (godaddy)
* You cannot buy the domain in Azure, in AWS with Route53 you can buy the domain.
* Zone name has to be exactly like domain name (contoso.com)
* Now in the record set we see is 2 records, NS record and SOA record. Now NS records are the records that we have to add on DNS registrar portal for the name server.
* This process is called the ```DNS delegation```.
* Once Nameserver updated with DNS registrar, we don't know whether these name servers have been replicated across the globe or not, whether our
change is basically replicated or not.  
* Validate it on dnschecker.org
* Create zone for sub-domain (stage.contoso.com)
* Then go to parent zone (contoso.com) and new record
```
Name: stage
type: NS - Name Server records
TTL : default (1hr)
Name Server: Copy the NS records in subdomain and add.
```

### Create PrivateLink DNS Zones

Create Prviate Link DNS Zones and link to the Vnet. 
Services that support : https://learn.microsoft.com/en-us/azure/private-link/private-endpoint-dns

* Create privatelink Private DNS Zones (privatelink.blob.core.windows.net) 
* Deploy the resources with Private Endpoint
* Add the configure private DNS zone
