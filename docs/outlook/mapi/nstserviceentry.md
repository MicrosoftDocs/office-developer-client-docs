---
title: "NSTServiceEntry"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 5ada6363-2406-4c0a-8326-a299a8bbefe1
description: "Last modified: March 09, 2015"
---

# NSTServiceEntry

  
  
**Applies to**: Outlook 
  
Message service entry point function for a MAPI store provider to wrap a PST-based local store as an NST store. 
  
## Quick info

|||
|:-----|:-----|
|Implemented by:  <br/> |MAPI provider  <br/> |
|Called by:  <br/> |MAPI  <br/> |
   
```cpp
HRESULT NSTServiceEntry( 
    HINSTANCE hInstance,   
    LPMALLOC lpMalloc, 
    LPMAPISUP lpMAPISup, 
    ULONG ulUIParam, 
    ULONG ulFlags, 
    ULONG ulContext, 
    ULONG cValues, 
    LPSPropValue lpProps, 
    LPPROVIDERADMIN lpProviderAdmin, 
    LPMAPIERROR FAR * lppMapiError 
);
```

## Parameters

 **NSTServiceEntry** uses the **[MSGSERVICEENTRY](msgserviceentry.md)** function prototype. For information on its parameters, see **[MSGSERVICEENTRY](msgserviceentry.md)**. 
  
## Return values

For information on return values, see **[MSGSERVICEENTRY](msgserviceentry.md)**. 
  
## Remarks

When using **[GetProcAddress](http://msdn.microsoft.com/en-us/library/ms683212.aspx)** to look for the address of this function in msmapi32.dll, specify "NSTServiceEntry" as the procedure name. 
  
To use the Replication API, a MAPI store provider must first open and wrap a PST-based local store by calling **[NSTServiceEntry](nstserviceentry.md)**. The provider can then use the major interfaces of the API, **[IOSTX](iostxiunknown.md)** and **[IPSTX](ipstxiunknown.md)**, to carry out replication. 
  
The following remarks apply to an NST store:
  
- Do not store any information in the global profile section when implementing a MAPI provider that uses **NSTServiceEntry**. The global profile section is shared by many providers and data stored in this profile can be overwritten. 
    
- Only items with existing modification time stamps get their stamps updated when they are saved. 
    
- Conflict-checking does not occur automatically when items are saved.
    
-  Duplicate detection does not occur when items are saved. 
    
-  The file representing the cached version of the server is appended with .NST. 
    
- To obtain a pointer to the global profile section, a message service calls **[IMAPISupport::OpenProfileSection](imapisupport-openprofilesection.md)** in the support object using **pbNSTGlobalProfileSectionGuid** as defined below: 
    
  ```
  #define  pbNSTGlobalProfileSectionGuid "\x85\xED\x14\x23\x9D\xF7\x42\x66\x8B\xF2\xFB\xD4\xA5\x21\x29\x41"
  ```

- In this case, the support object of the message service should ensure that **IMAPISupport::OpenProfileSection** returns the profile section that is identified by the **[PR_SERVICE_UID](pidtagserviceuid-canonical-property.md)** property in the default profile section. To get this profile section, the support object can open the default profile section, retrieve **PR_SERVICE_UID**, and pass the result to **IMAPISupport::OpenProfileSection** to retrieve the correct global profile section. The support object in turn returns a pointer to this global profile section to the message service. 
    
## See also



[About the Replication API](about-the-replication-api.md)

