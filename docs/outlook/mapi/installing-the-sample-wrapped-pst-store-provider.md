---
title: "Installing the Sample Wrapped PST Store Provider"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
ms.assetid: 90ce0ea3-ba73-cb57-0fa9-8898bc4ac9de
description: "Last modified: July 05, 2012"
 
 
---

# Installing the Sample Wrapped PST Store Provider

 **Last modified:** July 05, 2012 
  
 * **Applies to:** Outlook * 
  
This topic takes you through the steps to download and install the Sample Wrapped PST Store Provider. The Sample Wrapped PST Store Provider, WrapPST, implements a wrapped PST store provider that is intended to be used in conjunction with the Replication API. For more information about the Replication API, see [About the Replication API](about-the-replication-api.md).
  
## Install the Sample Wrapped PST Store Provider

1. To download the Sample Wrapped PST Store Provider, see [Outlook 2007 Auxiliary Reference Code Samples and Redistributable Installer](http://www.microsoft.com/en-us/download/details.aspx?id=24102).
    
2. Open the **SampleWrappedPSTStoreProvider** folder and click **Extract All Files**.
    
3. Click **Browse**, select the location where you want to save the sample, and click **OK**.
    
4. Click **Extract**. The folder you selected appears and contains the extracted files.
    
5. Open Visual Studio 2005 as an administrator.
    
    > [!NOTE]
    > If your computer is running Windows XP, you must be logged in as an Administrator. If your computer is running Windows Vista, you must be logged in as an Administrator and you must right-click the Visual Studio 2005 icon and click **Run as administrator**. 
  
6. In Visual Studio 2005, click **File**, select **Open**, and then click **Project/Solution**.
    
7. Browse to the location where you saved the sample, click **WrapPST**, and then click **Open**.
    
8. On the **Build** menu, click **Build Solution**.
    
9. In the **Save File As** dialog box, click **Save**.
    
10. In the folder where you saved the sample, right-click the **Install.bat** file and click **Run as administrator**.
    
11. In the **User Account Control** dialog box, click **Continue**.
    
## See also

#### Concepts

[About the Sample Wrapped PST Store Provider](about-the-sample-wrapped-pst-store-provider.md)
  
[Initializing a Wrapped PST Store Provider](initializing-a-wrapped-pst-store-provider.md)
  
[Logging On to a Wrapped PST Store Provider](logging-on-to-a-wrapped-pst-store-provider.md)
  
[Using a Wrapped PST Store Provider](using-a-wrapped-pst-store-provider.md)
  
[Shutting Down a Wrapped PST Store Provider](shutting-down-a-wrapped-pst-store-provider.md)

