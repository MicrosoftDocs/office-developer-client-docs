---
title: "Message Store Provider Sample"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: f1e4077b-7a95-440d-a326-a8dc9cdab4fe
description: "Last modified: March 09, 2015"
 
 
---

# Message Store Provider Sample

  
  
**Applies to**: Outlook 
  
The Sample Wrapped PST Store Provider uses a Personal Folders file (PST) provider as the back end for storing data. The wrapped PST store provider should be used together with the Replication API. 
  
The Replication API enables you to replicate items from a back-end data repository into a Microsoft Outlook PST store. You use the Replication API to replicate the data into a dedicated PST store and keep track of the synchronization state. For more information, see [About the Replication API](about-the-replication-api.md).
  
Most of the functions in the Sample Wrapped PST Store Provider pass their arguments directly to the underlying PST provider. Certain functions require special implementation and are described in the following topics.
  
|||
|:-----|:-----|
|Executable:  <br/> |WrpPST32.dll  <br/> |
|Source code directory:  <br/> |SampleWrappedPSTStoreProvider\WrapPST  <br/> |
|Language:  <br/> |C++  <br/> |
|Platforms:  <br/> |Microsoft Visual Studio 2008 to compile for Windows Vista, Windows Server 2008, Windows XP SP2, and Windows Server 2003 SP1  <br/> |
   
## Supported Features

This sample supports Microsoft Outlook 2010 64-bit and has now been revised for Outlook 2013. See the following topics for additional information:
  
- [About the Replication API](about-the-replication-api.md)
    
- [Initializing a Wrapped PST Store Provider](initializing-a-wrapped-pst-store-provider.md)
    
- [Logging On to a Wrapped PST Store Provider](logging-on-to-a-wrapped-pst-store-provider.md)
    
- [Using a Wrapped PST Store Provider](using-a-wrapped-pst-store-provider.md)
    
- [Shutting Down a Wrapped PST Store Provider](shutting-down-a-wrapped-pst-store-provider.md)
    
 **To install the Sample Wrapped PST Store Provider**
  
1. To download the Sample Wrapped PST Provider, see [Downloading the Outlook MAPI Samples](downloading-the-outlook-mapi-samples.md).
    
2. Locate the folder where you saved the Outlook MAPI Samples. Right-click the **OutlookMAPISamples-\<version number\>** zip folder and then click **Extract All**.
    
3. Click **Browse**, select the location where you want to save the sample, and then click **Extract**.
    
4. Run Microsoft Visual Studio 2008.
    
5. In Microsoft Visual Studio 2008, click **File**, select **Open**, and then click **Project/Solution**.
    
6. Browse to the location where you saved the sample, click **WrapPST.vcproj**, and then click **Open**.
    
7. On the **Build** menu, click **Build Solution**.
    
8. In the **Save File As** dialog box, click **Save**.
    
9. In the folder where you saved the sample, right-click the **install.bat** file and then click **Run as administrator**.
    
10. In the **User Account Control** dialog box, click **Continue**.
    

