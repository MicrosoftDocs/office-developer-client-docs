---
title: "Integrate with Office from Windows universal apps"
 
 
manager: soliver
ms.date: 2/6/2017
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 60b4fa23-0075-4f6a-8bd0-9e53e99432d5

description: "You can integrate your Windows universal app platform third-party apps with Excel Mobile, PowerPoint Mobile, and Word Mobile. Universal apps integrate with Office apps via Windows file picker contracts, expando properties, and Cached File Updater contracts."
---

# Integrate with Office from Windows universal apps

You can integrate your Windows universal app platform third-party apps with Excel Mobile, PowerPoint Mobile, and Word Mobile. Universal apps integrate with Office apps via Windows [file picker contracts](https://msdn.microsoft.com/en-us/library/windows/apps/hh465174.aspx), [expando properties](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh770655.aspx), and [Cached File Updater contracts](https://msdn.microsoft.com/en-us/library/windows/apps/windows.storage.provider.cachedfileupdater.aspx).
  
When you integrate your universal app with Excel, PowerPoint, or Word Mobile, your users can open Office documents that your app provides, either when they browse from within Office or when they use Windows to open files from within your app. Users can also save the file back to your universal app, which uploads the file back to your service.
  
Files opened this way appear in the Recent list in Office, so your users can easily find and reopen them.
  
This integration requires that your universal app:
  
- Runs on .
    
- Implements the Windows [file picker contracts](https://msdn.microsoft.com/en-us/library/windows/apps/hh465174.aspx).
    
- Represents a file store (for example, an app that allows access to cloud storage).
    
## Expando properties

Windows universal apps can use Expando properties to communicate additional information that is associated with files. For information about how this works in Windows, see "System.ExpandoProperties" in [StorageItemContentProperties.SavePropertiesAsync](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh770655.aspx).
  
The following table describes the properties that your app has to provide to Office to enable file open scenarios. If this information is not provided, all files from your app are opened as read only. Whether users can open files for editing depends on the type of Office license they have and the type of document they're trying to open.
  
Set these properties in the **System.ExpandoProperties** property set. 
  
|**Property**|**Description**|**Type**|**Example**|
|:-----|:-----|:-----|:-----|
|**AppDisplayName** <br/> |Provider name to display to the user. Appears in multiple places in Office, such as the recent document list.  <br/> |String  <br/> |Contoso  <br/> |
|**MicrosoftOfficeOwnershipType** <br/> |For licensing, indicate whether the document/location is Personal/Consumer or Work/Business. Allowed values are 1 (personal) and 2 (business). For example, if your user's file is stored in Contoso Business, use the value "2" for business.  <br/> |Unit32  <br/> | 1 or 2  <br/> For example, if your user's file is stored in Contoso Business, this file should be marked 2 for business.  <br/> |
|**MicrosoftOfficeTermsOfUse** <br/> |Legal text to declare that the information you provide is accurate per our terms of use. This text is not displayed to the user. It is an agreement between you, the application provider, and Microsoft.  <br/> See the following for an example.  <br/> | String  <br/> | I agree to the terms located in [https://go.microsoft.com/fwlink/p/?LinkId=528381](third-party-applications-integrating-with-office-mobile-products-on-windows-10-w.md) <br/> |
   
The following code example shows how to set these properties.
  
```
public static async Task SetExpandoProperties(StorageFile file,... other params ...) 
  { 
     var expandoProperties = new PropertySet(); 
     expandoProperties.Add("AppDisplayName", "Contoso",);  
     // String value. 
     expandoProperties.Add("MicrosoftOfficeOwnershipType", 1);  
     // Unit32 value - 1 (for personal), 2 (for business).  
     expandoProperties.Add("MicrosoftOfficeTermsOfUse", "I agree to the terms located at https://go.microsoft.com/fwlink/p/?LinkId=528381");   
    // String value. 
          
       var fileProperties = new PropertySet(); 
       fileProperties.Add("System.ExpandoProperties", expandoProperties); 
       await file.Properties.SavePropertiesAsync(fileProperties); 
  } 

```

## Cached File Updater contracts

If your universal app participates in Cached File Updater contracts, it will be notified of changes another universal app (such as Office) makes to the file. For information about how this works in Windows, see [CachedFileUpdater class](https://msdn.microsoft.com/en-us/library/windows/apps/windows.storage.provider.cachedfileupdater.aspx).
  
Office uses the **AllowOnlyReaders** option to open the read-write files your universal app provides via the file picker contracts. This means the file cannot be moved, deleted, renamed, or written to by another app, including your own, while it is open in Office. Office will autosave the file, but sets CachedFileManager.DeferUpdates to prevent activating your app until Office closes the document, or Office is suspended by Windows (when the user switches to another app). When Office closes the file, your app can write to it. 
  
Your app must handle all communication with your service, including download, refresh, and upload.
  
The following tables lists the parameters to set to handle interactions between your app and Office.
  
|**Parameter**|**Description**|
|:-----|:-----|
|[ReadActivationMode](https://msdn.microsoft.com/en-us/library/windows/apps/windows.storage.provider.readactivationmode.aspx) <br/> |Set **BeforeAccess** to allow your app to update the file before it sends it to Office.  <br/> |
|[WriteActivationMode](https://msdn.microsoft.com/en-us/library/windows/apps/windows.storage.provider.writeactivationmode.aspx) <br/> |Set **ReadOnly** to make the file read only. Set **AfterWrite** to ensure that your app will be triggered by the CacheFileUpdater when Office is finished with the file.  <br/> > [!NOTE]> If you do not set **AfterWrite**, your app will not be notified to upload the changes, which means that the user's changes will only be local.           |
|[CachedFileOptions.RequireUpdateOnAccess](https://msdn.microsoft.com/en-us/library/windows/apps/windows.storage.provider.cachedfileoptions.aspx) <br/> |Set this property to ensure that your app can update the file when a user accesses it from the Recent list.  <br/> |
   
## Invoking Office from your app

When a user opens an Office document from your app, the document can open in Excel Mobile, PowerPoint Mobile, and Word Mobile. For example, when a user selects a \*.docx file in your app, Word Mobile launches with the \*.docx file opened. The Office app that opens is based on which app the user associated with the file type.
  
To open a file from your app in Office, we recommend that you use **LaunchFileAsync()** to launch the file. We don't recommend that you use **LaunchUriAsync()** to launch the file because that will cause the application registered for the URI scheme to launch (the browser) instead of Office. Although **LaunchUriAsync()** with the **LauncherOptions.ContentType()** option can invoke Office, in this case the file opened is marked as temporary and is read-only in Office. 
  
For more information, see [Launcher class](https://msdn.microsoft.com/en-us/library/windows/apps/windows.system.launcher.aspx).
  
## Temporary and read-only files

Set the **FILE_ATTRIBUTE_TEMPORARY** attribute on temporary files and the **FILE_ATTRIBUTE_READONLY** attribute on read-only files in your app. 
  
Files that have the **FILE_ATTRIBUTE_TEMPORARY** or **FILE_ATTRIBUTE_READONLY** attributes set open as read-only in Office. The **FILE_ATTRIBUTE_TEMPORARY** also prevents the file from appearing in the Recent list. 
  
For more information about file attributes, see [SetFileAttributes function](https://msdn.microsoft.com/en-us/library/windows/desktop/aa365535%28v=vs.85%29.aspx).
  
## Other best practices

To optimize for file consistency, for example when conflicting edits or errors occur, apply the following best practices:
  
- Prevent save conflicts.
    
  - Pause uploads when server conflicts occur to avoid forking (only fork when Office no longer has a write file open). Typically, if a file from your app is open in Office, your app is activated only when Office closes or is suspended by Windows.
    
  - ◦If you need UI to handle conflicts, implement toast notifications. Full UI is not available when Office is suspended.
    
- Handle errors.
    
  - When a lock is released, notify users of the conflict and provide a path to resolve it within your app.
    
## See also
<a name="bk_addresources"> </a>

- [Integrate with Office](integrate-with-office.md)
    
- [Integrate with Office from Win32 sync clients](integrate-with-office-from-win32-sync-clients.md)
    

