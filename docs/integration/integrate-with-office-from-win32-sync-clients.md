---
title: "Integrate with Office from Win32 sync clients"
 
 
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 348555d3-3cd4-4e4a-b5ad-436571c25251
description: "Integrate your third-party Win32 sync clients with Excel Mobile, PowerPoint Mobile, and Word Mobile Office applications."
---

# Integrate with Office from Win32 sync clients

Integrate your third-party Win32 sync clients with Excel Mobile, PowerPoint Mobile, and Word Mobile Office applications. 
  
You can integrate your Windows universal app with Excel Mobile, PowerPoint Mobile, and Word Mobile clients by registering as a sync root provider. This article describes the best practices to apply to ensure that your Win32 sync clients work well with Office applications.
  
This integration requires that your Win32 sync client has a sync engine.
  
## Register as a sync root provider

Unless your sync client is registered as a sync root provider, Office will treat files in your sync folder the way that it treats regular local files. This means that Office will provide "move to OneDrive" options for users when they attempt to share the document. To avoid this for files you sync, you must register as a sync root provider. For information about how to register, see [Integrate a Cloud Storage Provider](https://msdn.microsoft.com/en-us/library/windows/desktop/dn889934%28v=vs.85%29.aspx).
  
## Integrate your app into the root node of the navigation pane

In order for your Win32 sync client to show up as a root node in the navigation pane in the File Explorer and Windows file picker, you need to integrate your app into the root level. For information about how to do this, see [Integrate a Cloud Storage Provider](https://msdn.microsoft.com/en-us/library/windows/desktop/dn889934%28v=vs.85%29.aspx). 
  
## Add your sync folder as a document library (optional)

In Office, users can create documents in their document libraries with a single action. To add your sync location to the document library, use the [SHAddFolderPathToLibrary function](https://msdn.microsoft.com/en-us/library/windows/desktop/dd378432%28v=vs.85%29.aspx). 
  
## Additional resources
<a name="bk_addresources"> </a>

- [Integrate with Office](integrate-with-office.md)
    
- [Integrate with Office from Windows universal apps](integrate-with-office-from-windows-universal-apps.md)
    

