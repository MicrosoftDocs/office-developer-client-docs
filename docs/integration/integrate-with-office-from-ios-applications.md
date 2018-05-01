---
title: "Integrate with Office from iOS applications"
 
 
manager: soliver
ms.date: 6/4/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: f3a277ba-7ba1-4eea-83b5-915b409f3093
description: "Office for iOS provides an extensible solution that enables integration with third-party applications. This article describes how you can integrate with Office from your iOS application by passing users from your application to Office, and then returning them to your application."
---

# Integrate with Office from iOS applications

Office for iOS provides an extensible solution that enables integration with third-party applications. This article describes how you can integrate with Office from your iOS application by passing users from your application to Office, and then returning them to your application.
  
You can enable users who are running Office on an iOS device to open and edit files stored in SharePoint or OneDrive from any application, and then quickly return them to the original application when they're done editing the file. To do this, you pass files to Office via protocol handlers, and you make sure that Office is invoked in a way that Office can understand.
  
When a user is done editing a file, they can choose the back arrow in the Office application to close the document and return to the original storage application, provided you pass specific information to the Office application when it launches.
  
## Verify that Office has been installed

Your referring application will first need to verify that a particular Office application is installed. The following Office applications can be installed on iOS devices for document viewing and editing:
  
- Excel
    
- OneNote
    
- PowerPoint
    
- Word
    
Use the [canOpenURL](https://developer.apple.com/library/ios/documentation/UIKit/Reference/UIApplication_Class/index.html) method to determine whether your application can open the resource. This method takes the URL for the resource as a parameter, and returns **No** if the application that accepts the URL is not available. If **canOpenURL** returns **No**, you'll need to prompt the user to install Office.
  
### Prompt the user to install Office

 If a particular Office application is not installed, you can use an [SKProductViewController](https://developer.apple.com/library/ios/documentation/StoreKit/Reference/SKITunesProductViewController_Ref/index.html) object to render the iTunes app store in your application and show the user the Office application to install. The following table lists the iTunes identifier to use to invoke each Office application in the Store Kit Product View Controller. 
  
|**Office application**|**iTunes identifier**|
|:-----|:-----|
|Excel  <br/> |[https://itunes.apple.com/us/app/microsoft-excel/id586683407?mt=8&amp;uo=4](https://itunes.apple.com/us/app/microsoft-excel/id586683407?mt=8&amp;uo=4) <br/> |
|OneNote (iPad)  <br/> |[https://itunes.apple.com/us/app/microsoft-onenote-for-ipad/id478105721?mt=8&amp;uo=4](https://itunes.apple.com/us/app/microsoft-onenote-for-ipad/id478105721?mt=8&amp;uo=4) <br/> |
|OneNote (iPhone)  <br/> |[https://itunes.apple.com/us/app/microsoft-onenote-for-iphone/id410395246?mt=8&amp;uo=4](https://itunes.apple.com/us/app/microsoft-onenote-for-iphone/id410395246?mt=8&amp;uo=4) <br/> |
|PowerPoint  <br/> |[https://itunes.apple.com/us/app/microsoft-powerpoint/id586449534?mt=8&amp;uo=4](https://itunes.apple.com/us/app/microsoft-powerpoint/id586449534?mt=8&amp;uo=4) <br/> |
|Word  <br/> |[https://itunes.apple.com/us/app/microsoft-word/id586447913?mt=8&amp;uo=4](https://itunes.apple.com/us/app/microsoft-word/id586447913?mt=8&amp;uo=4) <br/> |
   
## Invoke Office

When the Office application is installed, your referring application can invoke Office by passing the following details: 
  
- Office protocol
    
- Open mode
    
- URL
    
- Passback protocol
    
- Document context
    
Schema format:
  
 `<Office protocol><open mode>|u|<URL>|p|<passback protocol>|c|<document context>`
  
The following example shows a request to invoke a Word file for editing:
  
 `ms-word:ofe|u|https://contoso/Q4/budget.docx|p|clouddrive|c|folderviewQ4`
  
### Office protocols

The following table lists the protocols for each Office application. 
  
|**Application**|**Protocol**|
|:-----|:-----|
|Excel  <br/> |ms-excel:  <br/> |
|OneNote  <br/> |onenote:  <br/> |
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
  
### Passback protocol (optional)

If you want Office to return users to your iOS application when they choose the back arrow, the invoking application will need to use the passback protocol, which includes the descriptor '|p|' followed by the app protocol (without a colon). You'll need to ensure that your application can properly handle the response from Office.
  
Schema format:
  
 `|p|<passback protocol>`
  
### Document context (optional)

Office doesn't use the document context, but the referring application might need it when Office passes a user back. If you want the document context to be returned to your application, use the descriptor '|c|' followed by the context that you want as a string. Office does not limit the length of the string, beyond any limits imposed by the operating system.
  
Schema format:
  
 `|c|<document context>`
  
## Return users to the referring application

For security reasons, Office only returns users to the referring application if the file opened successfully. When the user chooses the back arrow, Office responds to the invoking application with the passback protocol, open mode, URL, upload pending status, and document context. The upload pending status uses the descriptor |z|, and is either yes or no.
  
Schema format:
  
 `<app protocol>:ofe|u|<URL>|z|<yes or no>|c|<doc context> Example: clouddrive:ofe|u|https://contoso/Q4/budget.docx|z|no|c|folderviewQ4`
  
## Additional resources
<a name="bk_addresources"> </a>

- [canOpenURL method](https://developer.apple.com/library/ios/documentation/UIKit/Reference/UIApplication_Class/index.html)
    
- [UIApplication class](https://developer.apple.com/library/ios/documentation/UIKit/Reference/UIApplication_Class/index.html)
    
- [SKProductViewController object](https://developer.apple.com/library/ios/documentation/StoreKit/Reference/SKITunesProductViewController_Ref/index.html)
    

