---
title: "MFCMAPI as a code sample"
description: "The MFCMAPI sample uses the Messaging API to provide access to MAPI stores through a graphical user interface."
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: f98eb842-fe76-4f60-b5e2-d2217d1a66ad
---

# MFCMAPI as a code sample
 
**Applies to**: Outlook 2013 | Outlook 2016 
  
The MFCMAPI sample uses the Messaging API to provide access to MAPI stores through a graphical user interface. After you download this sample, you can use the source files to examine example usage cases for many of the MAPI interfaces and references. For more information, see [MAPI Interfaces](mapi-interfaces.md).
  
|Property |Value |
|:-----|:-----|
|Platforms:  <br/> |Microsoft Visual Studio 2008 to compile for Windows 7, Windows Vista, Windows Server 2008, Windows XP SP2, and Windows Server 2003 SP1  <br/> |
   
### To download MFCMAPI
  
1. On the [latest MFCMAPI release](https://github.com/microsoft/mfcmapi/releases/latest) page, navigate to **Assets**.
    
2. Click **Source code (zip)**
    
3. In the **File Download** dialog box, click **Save**. In the **Save As** dialog box, locate the folder in which you want to save the source files, and then click **Save**.
    
4. In the **Download Complete** dialog box, click **Open Folder**. You can also click **Close** to close the dialog box and locate the zipped source files in the folder that you saved them in.
    
5. Right-click the **MFCMAPI-\<version number\>.zip** file, and then click **Extract All**. In the dialog box that appears, click **Extract** to extract the files to the folder that is displayed. You can also click **Browse** to select or create a different folder.
    
6. Run Visual Studio 2008 as an administrator.
    
   > [!NOTE]
   > If your computer is running Windows XP, you must be logged in as an administrator. If your computer is running Windows Vista, you must be logged in as an administrator and you must right-click the Visual Studio 2008 icon and then click **Run as administrator**.
  
7. In Visual Studio 2008, click **File**, point to **Open**, and then click **Project/Solution**.
    
8. Browse to the location where you saved the sample, select **MFCMapi.vcxproj**, and then click **Open**.
    
9. On the **Build** menu, click **Build Solution**.
    
10. In the **Save File As** dialog box, click **Save**.
    
### To use MFCMAPI as a code sample
  
In **Solution Explorer**, expand the **MFCMapi** project and examine the files in the **Header Files**, **Resource Files**, and **Source Files** nodes for programming scenarios. 
  
Many method topics in the [MAPI Interfaces](mapi-interfaces.md) section point to MFCMAPI source files for programming examples. For example, in [IMsgStore::GetReceiveFolderTable](imsgstore-getreceivefoldertable.md) you are instructed to look at the function `CMsgStoreDlg::OnDisplayReceiveFolderTable` in the MsgStoreDlg.cpp file. 
  
## See also

- [MAPI Samples](mapi-samples.md)

