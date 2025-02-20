## Creating Azure Resources

To save time, we have an ARM template to get a few Azure resources created:

- Container Registry (Used to store Docker Images for Application and Services)

Go ahead and Deploy to Azure

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fgithub.com%2Ffelipecembranelli%2Fyoutubeblink%2Fblob%2FNEW_ARCHITECTURE%2F03-Push-the-docker-images-to-acr%2Fazuredeploy.json)

> 📝 Please Note, Create a new resource when prompted, such as: **rg-video-summary** and substitute your network alias for **youralias**, or something unique that will appear as a FQDN for accessing your Azure Pet Store Application.

You should see something similar to the below image:

![](images/00_4.png)

> ⏱ The resource provisioning will take some time. **Do not wait!** Continue with the guides. Remember your Resource Group!

If you head over to your Azure Resource Group (once completed) You should see something similar to the below image:

![](images/00_5.png)

---

