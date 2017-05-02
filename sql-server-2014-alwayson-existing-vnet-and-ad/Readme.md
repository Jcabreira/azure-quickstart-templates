# Create a SQL Server 2014 Always On Availability Group in an existing Azure VNET and an existing Active Directory instance with BYOL Image

This template will create a SQL Server 2014 Always On Availability Group using the PowerShell DSC Extension in an existing Azure Virtual Network and Active Directory environment.

This template creates the following resources:

+	Three Storage Accounts
+	One internal load balancer
+	Three VMs in a Windows Server Cluster, two VMs run SQL Server 2014 with an availability group and the third is a File Share Witness for the Cluster
+	One Availability Set for the SQL and Witness VMs

A SQL Server always on listener is created using the internal load balancer.

To deploy the required Azure VNET and Active Directory infrastructure, if not already in place, you may use <a href="https://github.com/Azure/azure-quickstart-templates/tree/master/active-directory-new-domain-ha-2-dc">this template</a> to deploy the prerequisite infrastructure.

## Notes

+	The default settings for storage are to deploy using **premium storage**.  The SQL VMs use two P30 disks each (for data and log).  These sizes can be changed by changing the relevant variables. In addition there is a P10 Disk used for each VM OS Disk.

+ 	The default settings for compute require that you have at least 9 cores of free quota to deploy.

+ 	The images used to create this deployment are
	+ 	SQL Server - Latest SQL Server 2014 on Windows Server 2012 R2 Image and SQL BYOL Licencing Model
	+ 	Witness - Latest Windows Server 2012 R2 Image

+ 	The image configuration is defined in variables, but the scripts that configure this deployment have only been tested with these versions and may not work on other images.

+	To successfully deploy this template, be sure that the subnet to which the SQL VMs are being deployed already exists on the specified Azure virtual network, AND this subnet should be defined in Active Directory Sites and Services for the appropriate AD site in which the closest domain controllers are configured.

Click the button below to deploy from the portal

azure-quickstart-templates / sql-server-2014-alwayson-existing-vnet-and-ad / azuredeploy.json 
<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FJcabreira%2Fazure-quickstart-templates%2Fmaster%2Fsql-server-2014-alwayson-existing-vnet-and-ad%2Fazuredeploy.json" target="_blank">
    <img src="http://azuredeploy.net/deploybutton.png"/>
</a>
<a href="https://portal.azure.us/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FJcabreira%2Fazure-quickstart-templates%2Fmaster%2Fsql-server-2014-alwayson-existing-vnet-and-ad%2Fazuredeploy.json" target="_blank">
    <img src="http://azuredeploy.net/deploybutton.png"/>
</a>
<a href="http://armviz.io/#/?load=https%3A%2F%2Fraw.githubusercontent.com%2FJcabreira%2Fazure-quickstart-templates%2Fmaster%2Fsql-server-2014-alwayson-existing-vnet-and-ad%2Fazuredeploy.json" target="_blank">
    <img src="http://armviz.io/visualizebutton.png"/>
</a>


