# Designing Network

## Decide CIDR Ranges

|  Supernet | Region |
| ------------- | ------------- |
| 10.10.0.0/20  | EastUs  |
| 10.20.0.0/20  | CentralUs  |


## VNET Segmentation 

| East US (10.10.0.0/20)|  |
| -------------- | ------------ |
| 10.10.0.0/22  | vnet-region1-hub1  |
| 10.10.4.0/22  | vnet-region1-spoke1  |
| 10.10.6.0/22  | vnet-region1-spoke2  |
| 10.10.8.0/22  | untitled  |
| 10.10.10.0/22  | untitled  |
| 10.10.12.0/22  | untitled  |
| 10.10.14.0/22  | untitled  |

| Central US (10.20.0.0/20)|  |
| -------------- | ------------ |
| 10.20.0.0/22  | vnet-region2-hub1  |
| 10.20.4.0/22  | vnet-region2-spoke1  |
| 10.20.6.0/22  | vnet-region2-spoke2  |
| 10.20.8.0/22  | untitled  |
| 10.20.10.0/22  | untitled  |
| 10.20.12.0/22  | untitled  |
| 10.20.14.0/22  | untitled  |

### HUB Vnet Segmentation

#### East US Region

| Subscription  | secure-networking-demo |
| -------------- | ------------ |
| Resource Group  | rg-region1-networks  |
| Region  | EUS   |
| VNet Name  | vnet-region1-hub1  |
| Address Space  | 10.10.0.0/22  |

| Subnet Name  | CIDR  | Purpose |
| -------------- | ------ | ------ |
| AzureBastionSubnet  | 10.10.0.0/24  | Azure Bastion subnet |
| GatewaySubnet | 10.10.1.0/24  | VPN Gateway Subnet |
| unused | 10.10.2.0/24  | unused | 
| unused | 10.10.3.0/25  | unused |
| unused | 10.10.3.128/25 | unused |


#### Central US Region

| Subscription  | secure-networking-demo |
| -------------- | ------------ |
| Resource Group  | rg-region2-networks  |
| Region  | Central US   |
| VNet Name  | vnet-region2-hub1  |
| Address Space  | 10.20.0.0/22  |


| Subnet Name  | CIDR  | Purpose |
| -------------- | ------| ------ |
| AzureBastionSubnet  | 10.20.0.0/24  | Azure Bastion subnet |
| GatewaySubnet | 10.20.1.0/24  | VPN Gateway Subnet |
| unused | 10.20.2.0/24  | unused |
| unused | 10.20.3.0/25  | unused |
| unused | 10.20.3.128/25 | unused |


### SPOKE Vnet Segmentation

#### East US Region

##### SPOKE1 

| Subscription  | secure-networking-demo |
| -------------- | ------------ |
| Resource Group  | rg-region1-networks  |
| Region  | EUS   |
| VNet Name  | vnet-region1-spoke1  |
| Address Space  | 10.10.4.0/23  |

| Subnet Name  | CIDR  | Purpose |
| -------------- | ------ | ------ |
| Workload  | 10.10.4.0/25  | Azure Vm's |
| privateEndpoints | 10.10.4.128/25  | private endpoints |
| unused | 10.10.5.0/24  | unused |

##### SPOKE2 

| Subscription  | secure-networking-demo |
| -------------- | ------------ |
| Resource Group  | rg-region1-networks  |
| Region  | EUS   |
| VNet Name  | vnet-region1-spoke2  |
| Address Space  | 10.10.6.0/23  |

| Subnet Name  | CIDR  | Purpose |
| -------------- | ------ | ------ |
| Workload  | 10.10.6.0/25  | Azure Vm's |
| privateEndpoints | 10.10.6.128/25  | private endpoints |
| unused | 10.10.7.0/24  | unused |