# PowerShell Commandlets for Azure Machine Learning Studio & Web Service APIs
## Introduction
This is a preview of PowerShell Commandlet Library for Azure Machine Learning. It allows you to interact with Azure Machine Learning Workspace, or Workspace for short. The supported operations are:

* __Manage Workspace__
  * Get the metadata of Workspace(*[Get-AmlWorkspace](#get-amlworkspace)*)
* __Manage Dataset__
  * List all Datasets in Workspace (*[Get-AmlDataset](#get-amldataset)*)
  * Download a Dataset file from Workspace to local file directory (*[Download-AmlDataset](#download-amldataset)*)
  * Upload a Dataset file from local file directory to Workspace (*[Upload-AmlDataset](#upload-amldataset)*)
  * Delete a Dataset file in Workspace (*[Remove-AmlDataset](#remove-amldataset)*)
* __Manage Experiment__
  * List all Experiments in Workspace (*[Get-AmlExperiment](#get-amlexperiment)*)
  * Get the metadata of a specific Experiment (*[Get-AmlExperiment](#get-amlexperiment)*)
  * Run an Experiment (*[Start-AmlExperiment](#start-amlexperiment)*)
  * Delete an Experiment (*[Remove-AmlExperiment](#remove-amlexperiment)*)
  * Copy an Experiment from a Workspace to another Workspace (*[Copy-AmlExperiment](#copy_amlexperiment)*)
* __Manage Web Service__
  * List all Web Services in Workspace (*[Get-AmlWebService](#get-amlwebservice)*)
  * Get the attributes of a specific Seb Service (*[Get-AmlWebService](#get-amlwebservice)*)
  * Deploy a Web Service from a Predictable Experiment (*[New-AmlWebService](#new-amlwebservice)*)
  * Delete a Web Service (*[Remove-AmlWebService](#remove-amlwebservice)*)
* __Manage Web Service Endpoint__
  * List all Endpoints of a Web Service (*[Get-AmlWebServiceEndpoint](get-amlwebserviceendpoint)*)
  * Get attributes of a specific Endpoint of a Web Service (*[Get-AmlWebServiceEndpoint](#get-amlwebserviceendpoint)*)
  * Delete a Web Service Endpoint (*[Remove-AmlWebServiceEndpoint](#remove-amlwebserviceendpoint)*)
  * Create a new Web Service Endpoint in an existing Web Service (*[Add-AmlWebServiceEndpoint](#add-amlwebserviceendpoint)*)
  * Refresh a Web Service Endpoint (*[Refresh-AmlWebServiceEndpoint](#refresh_amlwebserviceendpoint)*)
  * Patch a Web Service Endpoint (*[Patch-AmlWebServiceEndpoint](#patch_amlwebserviceendpoint)*)
* __Call Azure ML Web Service APIs__
  * Execute a RRS (Request-Response Service) API (*[Invoke-AmlWebServiceRRSEndpoint](#invoke-amlwebservicerrsendpoint)*)
  * Execute a BES (Batch Execution Service) API (*[Invoke-AmlWebServiceBESEndpoint](#invoke_amlwebservicebesendpoint)*)

## Installation
Simply download the AzureMLPS.dll, then run the PowerShell command to import the module into the current PowerShell environment:
```
Import-Module .\AzureMLPS.dll
```

## Usage
Details to come. In the interim, use *Get-Help* on any of the commandlet. For example, to understand how to use Get-AmlWorkspace, run the following command: <br/>
```
Get-Help Get-AmlWorkspace
```
### Manage Workspace ###
#### Get-AmlWorkspace ####
``` 
# Returns a list of all attributes of a Workspace
$ws = Get-AmlWorkspace -WorkspaceId '<worksapce_id>' -AuthorizationToken '<auth_token>' -RegionName '<region>
# Display the Workspace Name
$ws.FriendlyName
```

You can find the value of Workspace Id and Workspace Authorization Token after you log onto your Azure Machine Learning Studio Workspace, and navigate to the Settings section. <br/>
The currently supported regions are: 'South Central US', 'Western Europe' and 'Southeast Asia'.

### Manage Dataset ###
#### Get-AmlDataset ####
```
# List all datasets in a Workspace:
$ds = Get-AmlDataset -WorkspaceId '<worksapce_id>' -AuthorizationToken '<auth_token>' -RegionName '<region>'
# Display the list in a table format
$ds | Format-Table
```

#### Download-AmlDataset ####
```
#Find a dataset named 'Flight Data' in the Workspace using Get-AmlDataset:
$dsFlight = Get-AmlDataset -WorkspaceId '<worksapce_id>' -AuthorizationToken '<auth_token>' -RegionName '<region>' | Where $_.Name = 'Flight Data'
#Download the Flight dataset:
Download-AmlDataset -WorkspaceId '<worksapce_id>' -AuthorizationToken '<auth_token>' -RegionName '<region>' -DatasetId $ds.DatasetId -DownloadFileName 'C:\Temp\FlightData.csv'
```

#### Upload-AmlDataset ####
```
Upload-AmlDataset -WorkspaceId '<workspace_id>' -AuthorizationToken '<auth_token>' -RegionName '<region>' -FileFormat GenericCSV -UploadFromFileName 'Flight.csv' -DatasetName 'Flight Data' -Description 'Flight Data'
```

#### Remove-AmlDataset ####
### Manage Experiment ###
#### Get-AmlExperiment ####
#### Start-AmlExperiment ####
#### Remove-AmlExperiment ####
#### Copy-AmlExperiment ####
### Manage Web Service ###
#### Get-AmlWebService ####
#### Get-AmlWebService ####
#### New-AmlWebService ####
#### Remove-AmlWebService ####
### Manage Web Servcie Endpoint ###
#### Get-AmlWebServiceEndpoint
#### Remove-AmlWebServiceEndpoint
#### Add-AmlWebServiceEndpoint
#### Refresh-AmlWebServiceEndpoint
#### Patch-AmlWebServiceEndpoint
### Call Azure ML Web Service APIs
#### Invoke-AmlWebServiceRRSEndpoint
#### Invoke-AmlWebServiceBESEndpoint


