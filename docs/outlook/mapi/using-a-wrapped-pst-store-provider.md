---
title: "Using a wrapped PST store provider"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
ms.assetid: 98f08432-e86c-cba6-45fd-5a6c94d50aaf
description: "Last modified: July 03, 2012"
---

# Using a wrapped PST store provider

**Applies to**: Outlook 
  
Before you can use a wrapped Personal Folders file (PST) store provider, you must initialize and configure the wrapped PST store provider. After the wrapped PST store provider is configured, you must implement functions so that MAPI and the MAPI spooler can log on to the message store provider. For more information about initializing and logging on to a wrapped PST store provider, see [Initializing a Wrapped PST Store Provider](initializing-a-wrapped-pst-store-provider.md) and [Logging On to a Wrapped PST Store Provider](logging-on-to-a-wrapped-pst-store-provider.md).
  
The **[IMAPISupport::IUnknown](imapisupportiunknown.md)** interface provides implementations for tasks that are commonly performed by message store providers. This interface must be wrapped for the Sample Wrapped PST Store Provider to work. The **[IMAPISupport::OpenProfileSection](imapisupport-openprofilesection.md)** function requires special implementation. All other functions can pass their parameters to the underlying wrapped object. 
  
In this topic, the **IMAPISupport::OpenProfileSection** function is demonstrated by using a code example from the Sample Wrapped PST Store Provider. The sample implements a wrapped PST provider that is intended to be used in conjunction with the Replication API. For more information about downloading and installing the Sample Wrapped PST Store Provider, see [Installing the Sample Wrapped PST Store Provider](installing-the-sample-wrapped-pst-store-provider.md). For more information about the Replication API, see [About the Replication API](about-the-replication-api.md).
  
When you finish using a wrapped PST store provider, you must properly shut down the wrapped PST store provider. For more information, see [Shutting Down a Wrapped PST Store Provider](shutting-down-a-wrapped-pst-store-provider.md).
  
## Open Profile Section routine

The **[IMAPISupport::OpenProfileSection](imapisupport-openprofilesection.md)** function opens a section of the current profile. The function requires special handling in the wrapped PST store provider implementation. When the  `pgNSTGlobalProfileSectionGuid` is requested, the function returns the profile section that is cached. 
  
### CSupport::OpenProfileSection() example

```cpp
STDMETHODIMP CSupport::OpenProfileSection( 
    LPMAPIUID lpUid,     
    ULONG ulFlags, 
    LPPROFSECT * lppProfileObj) 
{ 
    Log(true,"CSupport::OpenProfileSection\n"); 
    if (lpUid &&  
        IsEqualMAPIUID(lpUid, (void *)&pbNSTGlobalProfileSectionGuid) &&  
        m_lpProfSect) 
    {      
        // Allow the opening of the Global Section 
        if (m_lpProfSect) 
        { 
            *lppProfileObj = m_lpProfSect; 
            (*lppProfileObj)->AddRef(); 
            return S_OK; 
        } 
    } 
    return m_pMAPISup->OpenProfileSection(lpUid, ulFlags, lppProfileObj); 
}
```

## See also

- [About the Sample Wrapped PST Store Provider](about-the-sample-wrapped-pst-store-provider.md)
- [Installing the Sample Wrapped PST Store Provider](installing-the-sample-wrapped-pst-store-provider.md)
- [Initializing a Wrapped PST Store Provider](initializing-a-wrapped-pst-store-provider.md)
- [Logging On to a Wrapped PST Store Provider](logging-on-to-a-wrapped-pst-store-provider.md)
- [Shutting Down a Wrapped PST Store Provider](shutting-down-a-wrapped-pst-store-provider.md)

