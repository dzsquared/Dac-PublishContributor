# Sample DacFx Deployment Contributors for Filtering by Object Name or Schema

## Project Description
Scope reduction from the Microsoft [DACExtensions samples](https://github.com/microsoft/DACExtensions).  

## Prerequisites
An installation of SQL Server Data Tools or DacFx is required to run these samples. The sample projects include references to DLLs in a Visual Studio installation with the most recent release of SQL Server Data Tools.

The compiled dlls can be utilized with the DacFx installation included with SQL Server Data Tools, the DacFx [Windows-only DacFx.msi](https://docs.microsoft.com/sql/tools/sqlpackage/sqlpackage-download), or the [cross-platform SqlPackage.exe](https://docs.microsoft.com/sql/tools/sqlpackage/sqlpackage-download).

## Usage
Abbreviate use information:
1. Build the samples in Visual Studio
2. Copy the dll `Public.Dac.SampleDeploymentFilter.dll` into the DacFx extensions folder or folder with SqlPackage
3. Execute the publish command with additional properties `/p:AdditionalDeploymentContributors` and `/p:AdditionalDeploymentContributorArguments`

### Example 1, Does not publish object named "Customer"
```bash
./sqlpackage.exe /a:Publish /sf:"c:\sampledatabase.dacpac" /tsn:yourservername /tu:sa /tp:yourpassword /p:AdditionalDeploymentContributors=Public.Dac.SampleFilters.PlanFilterer /p:AdditionalDeploymentContributorArguments="FilterName=ObjectBasedFilter;ObjectName=Customer"
```

### Example 2, Does not publish the dbo schema
```bash
./sqlpackage.exe /a:Publish /sf:"c:\sampledatabase.dacpac" /tsn:yourservername /tu:sa /tp:yourpassword /p:AdditionalDeploymentContributors=Public.Dac.SampleFilters.PlanFilterer /p:AdditionalDeploymentContributorArguments="FilterName=SchemaBasedFilter;Schema=dbo"
```


## License
This project continues to carry the [MIT License](LICENSE) from the parent project, [DACExtensions samples](https://github.com/microsoft/DACExtensions).

