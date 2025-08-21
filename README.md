# deploy-container-to-azure-app-service
Developing solutions for Microsoft Azure, including how to deploy a containerised application to Azure App Service.

STEP PROCESS USING AZURE PORTAL

login: https://portal.azure.com.
Create a resource in Azure Services.
Search for WebApp and create a new app>

 FILL IN BASIC (configurations)
 
 1. subscription: Retain the default name created by the webApp
 2. resource group: select the existing resource group
 3. Name: Name according to desired (Turn off the slide bar)
 4. publish: Select CONTAINER
 5. O.S(operating system: Linux 
 6. Region: EastUs (choose according to nearest location)
 7. Linux Plan: Asp-rg-webApp------
 8. Pricing: free F1 plan (advisable for test or practice)

 NAVIGATE to the CONTAINER tab at the top after Basic to input the following:
 
 1. Side cart support: OFF
 2. Image source: Select other container register
 3. Access type: Retain default as public
 4. Register URL: name url: http://mcr.microsoft.com/K8se
 5. Image & tag: quickstart: latest


Review
Select + create

Now that your deployment has finished, it's time to view the web app. 
Select the link to your web app located next to the Default domain field in the Essentials section. The link will open the site in a new tab and test see that your app is running.

Clean up resources to avoid extra cost: to avoid unnecessary resource usage.
1. Navigate to the resource group you created and view the contents of the resources used in this exercise.
2. On the toolbar, select Delete resource group.
3> Enter the resource group name and confirm that you want to delete it.

   Done: congratulations to you, friend.





STEP PROCESS USING #BASH
# Log in to Azure
az login

# Create a Resource Group
az group create --name myResourceGroup --location "eastus"

# Create an Azure App Service plan (the server farm)
az appservice plan create --name myAppServicePlan --resource-group myResourceGroup --sku B1 --is-linux

# Create the web app and tell it to use your container from Docker Hub
az webapp create --resource-group myResourceGroup --plan myAppServicePlan --name my-unique-app-name --deployment-container-image-name nginx
