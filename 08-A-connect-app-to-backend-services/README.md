# Connect Frontend and Backend Together

In this section, we'll connect the Frontend app (UI) and backend services Together.


- environment variables

Tip:
https://stackoverflow.com/questions/51480085/configuring-appsettings-with-asp-net-core-on-azure-web-app-for-containers-whith

## How troubleshooting Azure Container Instances

There are different ways to monitor the Azure Container Instances execution, as shown in the links below:

https://learn.microsoft.com/en-us/azure/container-instances/container-instances-log-analytics

https://learn.microsoft.com/en-us/cli/azure/container?view=azure-cli-latest#az-container-logs

https://learn.microsoft.com/en-us/azure/container-instances/container-instances-get-logs


```
 # reading container logs
 az container logs --resource-group rg-video-summary-v3 --name video-summary-container-group
 
 # reading container logs stream
 az container logs --resource-group rg-videosummary-v3 --name video-summary-container-group --follow

 az container attach --resource-group rg-videosummary-v3 --name video-summary-container-group

```

To-do:
# Connect Function --> Db (new db func)
# Connect CI --> Db (processor)
# Connect Function --> CloudAmqp --> CI
