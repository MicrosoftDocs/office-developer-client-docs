---
title: "Registering Services and Service Providers in MapiSvc.inf"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
ms.assetid: a04acf17-4b2d-458e-9852-b6074acac096
description: "Last modified: July 18, 2013"
 
 
---

# Registering Services and Service Providers in MapiSvc.inf

 
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Installing a new provider on a system requires updating the MapiSvc.inf file to point to the new provider. Standard properties set during configuration, which include the following, inform MAPI where to find the provider's dynamic-link library (.dll):
  
- The **PR_SERVICE_DLL_NAME** is specified in the **[Message Service]** section. 
    
- The **PR_PROVIDER_DLL_NAME** is specified in the **[Service Provider]** section. 
    
> [!NOTE]
> The expectation is that you set the name of your provider's .dll (without the suffix "32"). MAPI then loads your provider by looking for it on the path. 
  
## Putting a Path in MapiSvc.inf

Most applications install under Program Files, requiring an update to the path variable to allow MAPI providers to work. With a few restrictions Microsoft Outlook 2010 and Outlook 2013 can accommodate full paths to MAPI providers.
  
When registering your provider in MapiSvc.inf, you could put the full path to the provider in the MAPI properties **PR_SERVICE_DLL_NAME** and **PR_PROVIDER_DLL_NAME**.
  
In either property, the full path must be without the suffix "32", because MAPI continues to append that to the filename before looking for your file. This means that if you register the path "c:\mypath\myprovider.dll", MAPI will attempt to load "c:\mypath\myprovider32.dll".
  
Because Outlook's MAPI was not originally designed to accommodate full paths, it accomplishes this insertion of the "32" suffix by looking for the first period in the string, which means that paths that contain other periods cannot work, so you cannot use paths such as "c:\my.path\myprovider.dll" or "c:\mypath\my.provider.dll".
  
Sometimes in a store provider you will generate entry identifiers using the **WrapStoreEntryID** function, which takes as a parameter the name of your provider. 
  
> [!IMPORTANT]
> If you are using full paths in MapiSvc.inf, you must use the same path in any calls to **WrapStoreEntryID**. 
  
Additionally, the path you use may be converted to and from Unicode using the code page provided by the [GetACP](https://msdn.microsoft.com/library/windows/desktop/dd318070%28v=vs.85%29.aspx/) function. 
  
> [!CAUTION]
> You will experience failure if you choose a path that contains characters that cannot survive such a roundtrip through the [MultiByteToWideChar](https://msdn.microsoft.com/library/windows/desktop/dd319072%28v=vs.85%29.aspx/) and [WideCharToMultiByte](https://msdn.microsoft.com/library/windows/desktop/dd374130%28v=vs.85%29.aspx/) functions. 
  
For a demonstration of this functionality, the [Wrapped PST sample](https://ol2010mapisamples.codeplex.com/) on CodePlex has been revised - the pertinent functionality is in **MergeWithMapiSvc** and **GenerateProviderPath**.
  

