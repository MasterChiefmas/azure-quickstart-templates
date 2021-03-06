# Copy data from one folder to another folder in an Azure Blob Storage
Please do the following steps before deploying the template: 

1. Complete the prerequisites mentioned in [prerequisites](https://docs.microsoft.com/azure/data-factory/quickstart-create-data-factory-powershell#prerequisites) article.
2. Update values for the following parameters in **azuredeploy.parameters.json** file. 
	1. dataFactoryName
	2. dataFactoryLocation
	3. storageAccountName
	3. storageAccountKey

3. If you followed the prerequisites mentioned above, you do not need to change values for these parameters. Otherwise, update values for these parameters. 

	1. blobContainer.  
	2. inputBlobFolder
	3. inputBlobName
	4. outputBlobFolder
	5. outputBlobName

Note that currently data factories of version 2 can only be created in **East US** and **East US 2** regions. 

<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2Fazure-quickstart-templates%2Fmaster%2F101-data-factory-v2-blob-to-blob-copy%2Fazuredeploy.json" target="_blank">
    <img src="http://azuredeploy.net/deploybutton.png"/>
</a>
<a href="http://armviz.io/#/?load=https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2Fazure-quickstart-templates%2Fmaster%2F101-data-factory-v2-blob-to-blob-copy" target="_blank">
    <img src="http://armviz.io/visualizebutton.png"/>
</a>

When you deploy this Azure Resource Template, a data factory is created with the following entities: 

- Azure Storage linked service
- Azure Blob datasets (input and output)
- Pipeline with a copy activity

The copy activity in the pipeline copies data from one folder to another folder in the same Azure Blob Storage. After you deploy the template, to run the pipeline and see the data being copied from source to destination, run the following PowerShell command (specify your data factory name and resource group name):

```powershell
$runId = Invoke-AzureRmDataFactoryV2Pipeline -DataFactoryName <your data factory name> -ResourceGroupName <resource group name> -PipelineName "ArmtemplateSampleCopyPipeline" 
```

