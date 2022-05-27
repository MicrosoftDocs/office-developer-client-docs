---
title: "Configure UDFs in Excel Online in Office Online Server"
manager: lindalu
ms.date: 12/03/2019
ms.audience: ITPro
ms.localizationpriority: medium
ms.assetid: 3e0ca274-e9cd-48a1-8cfc-9d5053738972
description: "Use user-defined functions (UDFs) in Excel Online in Office Online Server to call custom functions."
---

# Configure UDFs in Excel Online in Office Online Server

Use user-defined functions (UDFs) in Excel Online in Office Online Server to call custom functions. 
  
User-defined functions (UDFs) in Excel Online enable you to call custom functions written in managed code by using formulas in cells. You can use UDFs to:
  
- Call custom mathematical functions.
    
- Get data from custom data sources into worksheets.
    
- Call web services.
    
You can install UDF binaries in one of two locations:
  
- A local directory. For example: 
    
    C:\UDFs\MySampleUdf.dll
    
- The global assembly cache. For example: 
    
    CompanyName.Hierarchichal.MyUdfNamespace.MyUdfClassName.dll, Version=1.1.0.0, Culture=en, PublicKeyToken=e8123117d7ba9ae38
    
Reference the location when you create a **New-OfficeWebAppsExcelUserDefinedFunction** definition on the Office Online Server. 
  
> [!NOTE]
> Office Online Server does not support UDFs located on network shares. 
  
## Enable UDFs on Office Online Server 

When an administrator creates a new Office Web Apps Server farm by using the [New-OfficeWebAppsFarm](/powershell/module/officewebapps/new-officewebappsfarm) Windows PowerShell cmdlet, UDF assemblies are disabled by default. The default value of the **ExcelUdfsAllowed** flag is false. 
  
To enable UDFs, run the following Windows PowerShell command on the Office Online Server, after the Office Web Apps Server farm has been created.
  
`Set-OfficeWebAppsFarm - ExcelUdfsAllowed:$true`
  
## Create UDF definitions on Office Online Server

After you enable UDFs, you need to create a definition for the binary that contains the UDFs. To create a definition for your UDF binary on the Office Online Server, use the **New-OfficeWebAppsExcelUserDefinedFunction** cmdlet. This cmdlet includes the following parameters: 
  
- **Assembly**
    
- **AssemblyLocation**
    
- **Enable** (set to False by default) 
    
- **Description**
    
The following examples show how create the UDF definitions.
  
`New-OfficeWebAppsExcelUserDefinedFunction -Assembly c:\myudf.dll -AssemblyLocation LocalFile -Enable:$true -Description "My Server UDFs"`
  
`New-OfficeWebAppsExcelUserDefinedFunction -Assembly "CompanyName.Hierarchichal.MyUdfNamespace.MyUdfClassName.dll, Version=1.1.0.0, Culture=en, PublicKeyToken=e8123117d7ba9ae38" -AssemblyLocation GAC -Enable:$true -Description "My GAC Server UDFs"`
  
After you create the new UDF reference, run **iisreset** on the server to pick up the reference immediately. 
  
## Additional Office Online Server UDF Windows PowerShell commands

Use the following Windows PowerShell cmdlets to work with UDFs:
  
- **Get-OfficeWebAppsExcelUserDefinedFunction** (no required parameters) - Returns a list of UDF definitions that are configured on the Office Online Server. 
    
- **Set- OfficeWebAppsExcelUserDefinedFunction** (Identity parameter required) - Sets properties on existing UDF definitions. 
    
- **Remove-OfficeWebAppsExcelUserDefinedFunction** (Identity parameter required) - Removes existing UDF definitions. 
    
## UDF sample

The following sample file provide a sample workbook that uses a UDF and the UDF binary:
  
- [BooleanDataType.xlsx](https://download.microsoft.com/download/6/7/F/67F724FD-1186-4209-BFF1-FBFD99E959D9/User%20Defined%20Function%20Assemblies/BooleanDataType.xlsx): a sample workbook that uses a UDF  
    
## See also

- [Configure Excel Online administrative settings](/officeonlineserver/configure-excel-online-administrative-settings)  
- [Office Online Server](/officeonlineserver/office-online-server)
    

