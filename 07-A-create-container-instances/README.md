## Creating Container Instances

To save time, we have an ARM template to get the container instances for the Video Summary Processor component.

Go ahead and Deploy to Azure

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Ffelipecembranelli%2Fyoutubeblink%2Frefs%2Fheads%2FNEW_ARCHITECTURE%2F07-A-create-container-instances%2Fazuredeploy-aci-processor.json)


> 📝 Please Note, Create a new resource when prompted, such as: **rg-video-summary** and substitute your network alias for **youralias**, or something unique that will appear as a FQDN for accessing your Azure Application.

You should see something similar to the below image:

![alt text](../img/arm_aci_processor.JPG)

> ⏱ The resource provisioning will take some time. **Do not wait!** Continue with the guides. Remember your Resource Group!
