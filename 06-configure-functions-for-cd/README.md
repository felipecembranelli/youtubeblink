# Configure Functions for CI/CD

In this section, we'll configure Git Hub Action for the Azure Functions used to collect new YouTube videos:


Workflow sample:

```
name: Build and deploy .NET Core application to Function App VideoQueueLoader20241223161411
on:
  push:
    branches:
    - master
env:
  AZURE_FUNCTIONAPP_NAME: VideoQueueLoader20241223161411
  AZURE_FUNCTIONAPP_PACKAGE_PATH: .\published
  CONFIGURATION: Release
  DOTNET_CORE_VERSION: 8.0.x
  WORKING_DIRECTORY: .
  DOTNET_CORE_VERSION_INPROC: 8.0.x
jobs:
  build:
    runs-on: windows-latest
    steps:
    - uses: actions/checkout@v4
    - name: Setup .NET SDK
      uses: actions/setup-dotnet@v3
      with:
        dotnet-version: ${{ env.DOTNET_CORE_VERSION }}
    - name: Setup .NET Core (for inproc extensions)
      uses: actions/setup-dotnet@v1
      with:
        dotnet-version: ${{ env.DOTNET_CORE_VERSION_INPROC }}
    - name: Restore
      run: dotnet restore "${{ env.WORKING_DIRECTORY }}"
    - name: Build
      run: dotnet build "${{ env.WORKING_DIRECTORY }}" --configuration ${{ env.CONFIGURATION }} --no-restore
    - name: Publish
      run: dotnet publish "${{ env.WORKING_DIRECTORY }}" --configuration ${{ env.CONFIGURATION }} --no-build --output "${{ env.AZURE_FUNCTIONAPP_PACKAGE_PATH }}"
    - name: Publish Artifacts
      uses: actions/upload-artifact@v4
      with:
        name: functionapp
        path: ${{ env.AZURE_FUNCTIONAPP_PACKAGE_PATH }}
  deploy:
    runs-on: windows-latest
    needs: build
    steps:
    - name: Download artifact from build job
      uses: actions/download-artifact@v4
      with:
        name: functionapp
        path: ${{ env.AZURE_FUNCTIONAPP_PACKAGE_PATH }}
    - name: Deploy to Azure Function App
      uses: Azure/functions-action@v1
      with:
        app-name: ${{ env.AZURE_FUNCTIONAPP_NAME }}
        publish-profile: ${{ secrets.VideoQueueLoader20241223161411_F99C }}
        package: ${{ env.AZURE_FUNCTIONAPP_PACKAGE_PATH }}
```