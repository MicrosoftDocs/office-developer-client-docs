---
title: "Office for Android support for the Android Storage Access Framework"
 
 
manager: soliver
ms.date: 6/18/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 9cfed295-f499-44dc-bac5-9e266df1b5b3
description: "Office for Android integrates with the Android Storage Access Framework, which enables Office to open files stored by another document provider."
---

# Office for Android support for the Android Storage Access Framework

Office for Android integrates with the Android Storage Access Framework, which enables Office to open files stored by another document provider.
  
Android 4.4 (API level 19) introduces the Storage Access Framework (SAF). The SAF enables users to browse and open documents, images, and other files across all their preferred document storage providers. A standard UI lets users browse files and access them in a consistent way across apps and providers.
  
## Implement a document provider

If you're developing an app that provides storage services for documents, you can make your files available through the SAF by [writing a custom document provider](https://developer.android.com/guide/topics/providers/document-provider.mdl). Office apps can then invoke the [ACTION_OPEN_DOCUMENT](https://developer.android.com/reference/android/content/Intent.mdl) and/or [ACTION_CREATE_DOCUMENT](https://developer.android.com/reference/android/content/Intent.mdl) intent to receive the files returned by your document provider. Note that the intent might include filters to further refine the criteria. 
  
## Enable free consumer edits

Users can sign in to the Office apps with a free Microsoft account to create or edit docs that are stored in a consumer-oriented storage service. The following table lists the mandatory properties that providers must supply as part of the cursor, to enable free consumer edit for documents accessed via the Storage Access Framework.
  
|**Property**|**Index**|**Value**|
|:-----|:-----|:-----|
|Document Type  <br/> |com_microsoft_office_doctype  <br/> |\<consumer\>  <br/> |
|Service Friendly Name  <br/> |com_microsoft_office_servicename  <br/> |Any user-friendly name for the service, used to identify a document in the Recent list in the Office apps. Note that the "Terms of Use Agreement" property must be supplied before the friendly name for the service can be displayed.  <br/> |
|Terms of Use Agreement  <br/> |com_microsoft_office_termsofuse  <br/> |\<I agree to the terms located at http://go.microsoft.com/fwlink/p/?LinkId=528381\>  <br/> |
   
## Additional resources
<a name="bk_addresources"> </a>

- [Integrate with Office](integrate-with-office.md)
    
- [Content Provider Basics](https://developer.android.com/guide/topics/providers/content-provider-basics.mdl)
    
- [Creating a Content Provider](https://developer.android.com/guide/topics/providers/content-provider-creating.mdl)
    
- [Storage Access Framework Developer Guide](https://developer.android.com/guide/topics/providers/document-provider.mdl)
    

