---
title: "Integrate with Office from Android applications"
 
 
manager: soliver
ms.date: 6/18/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: a765fa49-a272-4047-9147-59cc68e5dd27
description: "Office for Android provides an extensible solution that enables integration with third-party applications. You can integrate with Office from your Android application by passing users from your application to Office."
---

# Integrate with Office from Android applications

Office for Android provides an extensible solution that enables integration with third-party applications. You can integrate with Office from your Android application by passing users from your application to Office.
  
You can enable users who are running Office on an Android device to open and edit files stored in SharePoint or OneDrive from any application. To do this, you pass files to Office via protocol handlers, and you make sure that Office is invoked in a way that Office can understand.
  
When a user is done editing a file, they can choose the back key on the device to return to the original storage application.
  
## Verify that Office has been installed

Your referring application will first need to verify that a particular Office application is installed. The following Office applications can be installed on Android devices for document viewing and editing: 
  
- Excel
    
- PowerPoint
    
- Word
    
Use Android PackageManager to determine whether a particular Office application is installed on the device. The following table lists the package names for the Office applications that you can use in this process.
  
|**Application**|**Package name**|
|:-----|:-----|
|Excel  <br/> |com.microsoft.office.excel  <br/> |
|PowerPoint  <br/> |com.microsoft.office.powerpoint  <br/> |
|Word  <br/> |com.microsoft.office.word  <br/> |
   
### Prompt the user to install Office

If a particular Office application is not installed, you can prompt the user to install the application. The following table lists the available install locations for Office applications.
  
|**Application**|**Google Play Store**|
|:-----|:-----|
|Excel  <br/> |[https://play.google.com/store/apps/details?id=com.microsoft.office.excel](https://play.google.com/store/apps/details?id=com.microsoft.office.excel) <br/> |
|PowerPoint  <br/> |[https://play.google.com/store/apps/details?id=com.microsoft.office.powerpoint](https://play.google.com/store/apps/details?id=com.microsoft.office.powerpoint) <br/> |
|Word  <br/> |[https://play.google.com/store/apps/details?id=com.microsoft.office.word](https://play.google.com/store/apps/details?id=com.microsoft.office.word) <br/> |
   
## Invoke Office

When the Office application is installed, your referring application can invoke Office by passing the following details:
  
- Office protocol
    
- Open mode
    
- URL
    
Schema format:
  
 `<Office protocol><open mode>|u|<URL>`
  
The following example shows a request to invoke a Word file for editing.
  
 `ms-word:ofe|u|https://contoso/Q4/budget.docx`
  
### Office protocols

The following table lists the protocols for each Office application.
  
|**Application**|**Protocol**|
|:-----|:-----|
|Excel  <br/> |ms-excel:  <br/> |
|PowerPoint  <br/> |ms-powerpoint:  <br/> |
|Word  <br/> |ms-word:  <br/> |
   
### Open mode

Office applications can open files directly into view (ofv) or edit (ofe) mode. Edit mode is the default.
  
Schema format:
  
 `<ofv or ofe>`
  
### URL

The URL includes three parts:
  
- The declaration that the file will be opened for edit (ofe)
    
- The URL descriptor (|u|)
    
- The URL
    
The URL has to be encoded and must be a direct link to the file (not a redirect). If the URL is in a format that Office cannot handle, or the download simply fails, Office will not return the user to the invoking application.
  
Schema format:
  
 `|u|<document URL>`
  
## See also
<a name="bk_addresources"> </a>

- [Integrate with Office](integrate-with-office.md)
    
- [PackageManager](http://developer.android.com/reference/android/content/pm/PackageManager.html)
    
- [GetPackageManager()](http://developer.android.com/reference/android/content/Context.html)
    

