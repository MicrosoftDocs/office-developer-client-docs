---
title: "Installing the Sample Offline State Add-in"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: e1b6ae6c-dcf2-a07f-c417-3a1049b758ad
description: "Last modified: July 06, 2012"
---

# Installing the Sample Offline State Add-in

 **Last modified:** July 06, 2012 
  
 * **Applies to:** Outlook * 
  
This topic takes you through the steps to download and install the Sample Offline State Add-in. The Sample Offline State Add-in is a COM add-in that adds an **Offline State** menu to Outlook and utilizes the Offline State API. Through the Offline State menu you can enable or disable state monitoring, check the current state, and change the current state. For more information about how the Offline State Add-in is implemented, see [Setting Up an Offline State Add-in](setting-up-an-offline-state-add-in.md).
  
## Install the Sample Offline State Add-in

1. Download the Sample Offline State Add-in here: [Outlook 2007 Auxiliary Reference Code Samples and Redistributable Installer](http://www.microsoft.com/en-us/download/details.aspx?id=24102).
    
2. Run Visual Studio 2005 as an administrator.
    
    > [!NOTE]
    > If your computer is running Windows XP, you must be logged in as an Administrator. If your computer is running Windows Vista, you must be logged in as an Administrator. Right-click the Visual Studio 2005 icon and click **Run as administrator**. 
  
3. In Visual Studio 2005, click **File**, select **Open**, and then click **Project/Solution**.
    
4. Browse to the location where you saved the sample, click **ConnectionStateAddin**, and then click **Open**.
    
5. On the **Build** menu, click **Build Solution**.
    
6. In the **Save File As** dialog box, click **Save**.
    
7. Click the **Start** menu, click **All Programs**, click **Accessories**, right-click **Command Prompt**, and then click **Run as administrator**.
    
    > [!NOTE]
    > If you are running Windows XP, you must be logged in as an Administrator. 
  
8. In the **User Account Control** dialog box, click **Continue**.
    
9. In the **Command Prompt** window, change directories to the Debug folder where you saved the sample. For example, if you saved the sample on your C:\ drive, you would type **cd "C:\ConnectionStateAddin\Debug"** and then press **ENTER**. 
    
10. Type **regsvr32 OfflineStateAddin.dll** and press **ENTER**. 
    
    > [!NOTE]
    > To uninstall the Sample Offline State Add-in, type **regsvr32 -u OfflineStateAddin.dll**
  
11. In the **RegSrv32** dialog box, click **OK**.
    
12. Restart Outlook to see the **Offline State** menu. 
    
## See also

#### Concepts

[About the Offline State API](about-the-offline-state-api.md)
  
[Installing the Sample Offline State Add-in](installing-the-sample-offline-state-add-in.md)
  
[About the Sample Offline State Add-in](about-the-sample-offline-state-add-in.md)
  
[Setting Up an Offline State Add-in](setting-up-an-offline-state-add-in.md)
  
[Monitoring Connection State Changes Using an Offline State Add-in](monitoring-connection-state-changes-using-an-offline-state-add-in.md)
  
[Disconnecting an Offline State Add-in](disconnecting-an-offline-state-add-in.md)

