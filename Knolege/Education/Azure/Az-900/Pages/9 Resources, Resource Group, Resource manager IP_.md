#azure
#### Resources (SQL,VM, Web app, ...)
- objects used to manage services in Azure
- represent service lifecycle
- Resources can be represented as a json template
Common properties
``` json
{
	"Type":"Microsoft.storage",
	"Apiversion":"2020-06-02",
	"Name":"MyStorage",
	"Location":"Weswtern Europe"
	...
}
```
#### Resource group (logical container to group resources)
1. Grouping of resources
2.  holds logically related resources
3. Ways to group resources (no specific rules)
4. Popular ways to group:
- Grouping by type (SQL1,SQL2,SQL3)
- Grouping by env (Group-Dev, Group-staging)
- by Department, by billing Location
Steps to Create Resource group
1)  Navigate to the resource groups and click Add button
2) Select subscription
3) provide a resource group name and Region (to select the best region it is better to check network delay and allowed service using Microsoft web sites) (Resorcxe group regeon does not means Resource region)

or you can Crate using CLI
1) login to use you subscription
``` azure cli
az login
```
2) create resource group
``` azure cli
az group create --name "group-name" --location "west europe"
```
3)  create resource
```
az storage account create --name "MyStorage" --resource-group group-name --location "north europe"
```
#### Access controll
You can specify Access to you resorces
1)Open Resource controll tab
2)press add button and then you can select some specific role and assign it to a single or many users.
3)press save and then you can check assigned roles in the role assignments tab

#### Additional information
- Each resource must be in one and only one resourc group
- - RG have thier own location
- Resources inside the RG can be placed in a different location
- Resource can be moved between RG
- Resource groups can't be nested RG1->RG2->RG3 (❌)

#### Resource Manager
It is an internal azure service for buildingf and managin azure resources 
To create some resources you can use
1. Portal 
2. Rest API
3. Power Shell
4. CLI
5. SDKs
All of those interfaces connected to the same point and send the same templates 

![[Pasted image 20240709081525.png]]
