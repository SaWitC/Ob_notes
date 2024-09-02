#azure

Compute services it is a category of on-demand services used to run cloud-based applications
#### Virtualization
- Emulation of physical machine
- Different virtual hardware configuration per machine/app
- Different operating systems per machine/app
- total separation of  environment
	- file system
	- services
	- ports
	- middleware
	- configuration
![[Pasted image 20240709082916.png]]

#### Azure VM
key charasteristics
- Infrastructure as a service (IaaS)
- Total control over operating system ant the software
- Supports marketplaces (images of operating system that is prepared already) and custom images (your own operating system image with a specific configuration)
- Vest suited for
	- custom software requiring custom system configuration
	- Liftt-and-shift scenarios
- Can run any application/scenario
	- Web app& web services
	- Databases
	- Desktop applications
	- jumpboxes
	- geteways,etc

#### Containers
- user host's operating system
- Emulate operating system (vms emulate hardware)
- Lightweight (no O/S)
	- Development Effort
	- Maintenance
	- Compute & storage requirements
	Respond quicker to demand changes
	Designed for almost any scenario
##### Azure Continer instance
- simples and fastest way to run container in azure
- (Paas) Platform as a service
- Serverles containers
- Designed for 
	- Small and simple web apps/services
	- background job
	- scheduled script

Way to create
azure resources(sidebar)->Create resource->container instances->create(button)->select or choose RG and specify other settings