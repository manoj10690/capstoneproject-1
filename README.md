# capstoneproject-1
This is my first Capstone Project where I have designed an E-commerce website using Azure services. 
Capstone Project
CREATING AN ECOMMERCE WEBSITE

Project requirements
As per the project requirement, I need to create a solution that meets the following needs: 
1.	An internet facing website deployed in the public cloud.
2.	Should meet global traffic demands, need to deploy virtual machines in different regions. 
3.	Balance the traffic coming from all around using load balancing. 
4.	A solution that ensures the internal employee easy access to the files. 
5.	Content delivery network to deliver static content to global traffic without any delay. 
SOLUTION
In order to provide solution to this problem, I am going to create multiple (3) Virtual machines in different regions and then deploy the website in each Virtual machine (VM). Once the VMs are deployed, I will create DNS traffic manager for load balancing and connect each VMs IPs as endpoint for high performance to meet global traffic demand. After that I will create CDN profile for caching the static content for faster delivery and then add the endpoint. Once that is done, I am going to create a file share for easy access of common files within the organization.  
This project is done using Azure Cloud services and following resources have been used to complete the project: 
•	Azure Virtual Machines 
•	Azure Storge accounts 
	Blob storage
	Files-share storage
•	Azure CDN services and endpoints
•	Azure Traffic manager and endpoints
•	Tag, Cost management and Resource Groups
===================================================
Note: Apart from these specific services, the other services are default services like networking. For the management of resources to be easier and quick, I have used tags and resource manager tools. 
====================================================



Step1: Deploying Virtual machines in 3 different regions
(East US, Central US and Central India)
1.	Logged in and went to Azure home page and searched for Virtual Machine and clicked on create.
 
2.	Entered the basic information like VM name, select the image, choose the location, select the VM size based on the requirement and entered login credentials. 
 
3.	Clicked on Next: Disk, chose Standard Disk as this project does not require much workload and this disk type saves cost. Other settings left to default settings.
 
4.	Clicked on Next: Networking, Virtual network is automatically created while creating a Virtual machine, however, we do get option to create customized Virtual Network if needed. Also enabled port 80 (HTTP) and 443 (HTTPS) for VM to allow all internet traffic along with RDP port 3389. Additionally, enabled Delete IP address and NIC option if the VM is deleted so that I do not get extra charges. 
 
5.	Clicked on Next: Management, turned off Boot diagnostics but in real time environment it can be turned On. Other settings left to default.
 
6.	Clicked on Next: Advance, no changes made to Advance settings. 
 
7.	Clicked on Next: Tags, created tags for each VMs so that it becomes easy to identify resources and manage. 
 
8.	Clicked on Next: Review and Create, after entering all the details, clicked on Review and Create, all the values are validated and I got the option to successfully create VM. 
 
9.	Opened RDP session and provided the login credentials and successfully logged in to the Virtual machine. 
 
10.	Opened PowerShell and run the command as “Install-WindowsFeature -Name Web-Server -IncludeManagementTool” to install the IIS (Internet Information Services) web server in the virtual machine.  Other option to install is Graphical User Interface (GUI), steps below: 
•	Open Server Manager and click Manage > Add Roles and Features. Click Next.
•	Select Role-based or feature-based installation and click Next.
•	Select the appropriate server. The local server is selected by default. Click Next.
•	Enable Web Server (IIS) and click Next.
•	No additional features are necessary to install the Web Adaptor, so click Next.
•	On the Web Server Role (IIS) dialog box, click Next.
•	On the Select role services dialog box, verify that the web server components listed below are enabled. Click Next.
•	Verify that your settings are correct and click Install.
•	When the installation completes, click Close to exit the wizard.
 
11.	After installing the IIS server, navigated to This PC >> C drive >> Inetpub >> wwwroot folder and removed the host file and entered the html code file (Shopping List). 
12.	After implementing the website and saving the changes, run the webserver and all the VMs are successfully running and showing the shopping list. 
13.	Repeated the same steps for creating the other two VMs. 
 
 
 
Step2: Deploying Traffic manager to manage the load coming across the Globe (Traffic manager is load balancing solution at DNS level)
1.	In Azure home page, searched for Load Balancing and chose Traffic manager as solution for this project. 
 

2.	Clicked on create and created a Traffic Manager profile.
 

3.	After successful creation of Traffic Manager profile, connected each virtual machines as an Endpoints. 
 
4.	In order to add VMs as endpoints, I needed to configure the DNS name for the VMs.
 


5.	The Traffic manager and endpoints are successfully created and the web page is showing up which is closest to my location “Central India”. As I stopped the Central India VM, the other VMs are showing up. Endpoint link: http://capprolb.trafficmanager.net/

 




Step3: Setting up CDN profile and endpoint
1.	Created a blob storage account and added the static content.
 
2.	Create a CDN profile. 
 
3.	Added endpoint to the CDN profile for users to access the static content.
Step4: Creating a File-share for employees to easily access the internal files
1.	In the Resource manager, clicked on storage account as it is already created.
 
2.	Created a File-share. 
 
3.	Enabled port 445 to connect File-share with webserver (VMs). 
 
4.	The code or script is generated, connected to the virtual server and it successfully worked, a file is created and all users with permission can access the data.
 

 

 
Finally, the solution is ready, for cost management and resources management, we have tool called Resource Groups. It allows us to access all the services at one place and also easy to manage and monitor the services.
Resource Groups overview:

 

Cost Management tool: 

 

