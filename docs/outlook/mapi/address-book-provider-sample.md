---
title: "Address Book Provider Sample"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 2ccf1643-5604-4fee-92cc-3d6af00e7f98
description: "Last modified: March 09, 2015"
 
 
---

# Address Book Provider Sample

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
This sample supports a single read-only container for display names and email addresses, which are read from a flat binary file. The sample supports one-off templates and all configuration options except the Profile Wizard.
  
You can download this sample from [Outlook Messaging API (MAPI) Code Samples](https://go.microsoft.com/fwlink/?LinkId=129740
).
  
|Property |Value |
|:-----|:-----|
|Executable:  <br/> |SABP32.dll  <br/> |
| Source code directory:  <br/> |SampleAddressBookProvider\SABP  <br/> |
|Language:  <br/> |C++  <br/> |
|Platforms:  <br/> |Microsoft Visual Studio 2008 to compile for Windows Vista, Windows Server 2008, Windows XP SP2, and Windows Server 2003 SP1  <br/> |
   
## Supported Features

This sample supports the following features:
  
- Table restrictions. The sample implements prefix-match and ambiguous-name resolution. It does not implement the full MAPI restriction language, and restrictions are supported only on the display name.
    
- A details display table for messaging users. 
    
- One-off addresses.
    
- An advanced search dialog box.
    
- An [IMAPIStatus : IMAPIProp](imapistatusimapiprop.md) interface. This interface is partially supported; its **IMAPIProp** methods are delegated to the **IPropData** interface. For more information, see the [IPropData : IMAPIProp](ipropdataimapiprop.md) interface. 
    
- Interactive and programmatic configuration.
    
## Unsupported Features

This sample does not support the following features:
  
- Sorting.
    
- Distribution lists.
    
- Creating, deleting, and modifying entries.
    
- Properties with multiple values.
    
- Named properties.
    
- Distinguishing between first and last names in display names.
    
 **To install the Sample Address Book Provider**
  
1. To download the Sample Address Book Provider, see [Downloading the Outlook MAPI Samples](downloading-the-outlook-mapi-samples.md).
    
2. Locate the folder where you saved the Outlook MAPI Samples. Right-click the **OutlookMAPISamples-\<version number\>** zip folder and click **Extract All**.
    
3. Click **Browse**, select the location where you want to save the sample, and click **Extract**.
    
4. Run Visual Studio 2008.
    
5. In Visual Studio 2008, click **File**, select **Open**, and then click **Project/Solution**.
    
6. Browse to the location where you saved the sample, click **SABP.vcproj**, and then click **Open**.
    
7. On the **Build** menu, click **Build Solution**.
    
8. In the **Save File As** dialog box, click **Save**.
    
9. In the folder where you saved the sample, right-click the **install.bat** file and click **Run as administrator**.
    
10. In the **User Account Control** dialog box, click **Continue**.
    
    > [!NOTE]
    > **Install.bat** copies the .dll to the default Microsoft Office installation folder, C:\Program Files\Microsoft Office\Office12\. If you have installed Office products in a different location, right-click **Install.bat** and click **Edit**. The file opens in Notepad. Replace the default installation path with the installation path used on your computer. 
  

