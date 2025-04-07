# Azure Public Ip's

A public IP address is an IP address that is reachable from the internet.

In Azure, a public IP address enables internet communication to resources within your virtual network by assigning a unique IP address to each resource that needs to be accessible from outside the Azure network.

Public IP can be assigned to various Azure resources such as virtual machines, Azure load Balancer and application gateways to facilitate internet communication.

## Considerations

* Only assign public IPS when absolutely necessary for internal workload.
* Use private IPS to reduce exposure to the internet, and the more you open up your workload to the internet, your depth in defence strategy will always need to have many other considerations.
* You should always use any firewalls or application gateways to restrict access to resources with public IPS, and limit the attack surface for workloads exposed to the internet.

## Create Public IP

Create the public ip's based on the needs and requirement.

|  Name | pip-region1- |
| ------------- | ------------- |
| IP Version  | IPv4  |
| SKU  | Standard  |
| Availability Zone  | Zone-Redundant  |
| Tier  | Regional  |
| IP Address Assignment  | Static  |
| Routing prefence  | Microsoft network  |
| DNS Name label | something(per need) |
| Idle Timeout (minutes) | 4 |


## Public IP Prefixes

Public IP prefix lets you create multiple public IP at the same time.

|  Name | myapp-nat-pip-prefix |
| ------------- | ------------- |
| IP Version  | IPv4  |
| SKU  | Standard  |
| Availability Zone  | Zone-Redundant  |
| Tier  | Regional  |
| Prefix Ownership  | Microsoft Owned  |
| Prefix Size  | /32(2 addresses)  |
| Routing prefence  | Microsoft network  |

