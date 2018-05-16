---
title: "Shutting Down a Wrapped PST Store Provider"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
ms.assetid: 0c9e5917-1b96-323d-bf8b-1d3aa1f677d0
description: "Last modified: July 02, 2012"
 
 
---

# Shutting Down a Wrapped PST Store Provider

 
  
**Applies to**: Outlook 
  
After you finish using a wrapped Personal Folders file (PST) store provider, you must properly shut down the wrapped PST store provider. For more information about using the wrapped PST store provider, see [Using a Wrapped PST Store Provider](using-a-wrapped-pst-store-provider.md).
  
To shut down a wrapped PST store provider, you must call the **[IMSProvider::Shutdown](imsprovider-shutdown.md)** function. This functions closes down the wrapped PST store provider in an orderly fashion. 
  
In this topic, the **IMSProvider::Shutdown** function is demonstrated by using a code example from the Sample Wrapped PST Store Provider. The sample implements a wrapped PST provider that is intended to be used in conjunction with the Replication API. For more information about downloading and installing the Sample Wrapped PST Store Provider, see [Installing the Sample Wrapped PST Store Provider](installing-the-sample-wrapped-pst-store-provider.md). For more information about the Replication API, see [About the Replication API](about-the-replication-api.md).
  
## Shut Down Routine

The MAPI spooler calls the **[IMSProvider::Shutdown](imsprovider-shutdown.md)** function just before it releases the wrapped PST store provider so that the wrapped PST store provider can shut down properly. The function terminates all session objects associated with the wrapped PST store provider. 
  
## CMSProvider::ShutDown() Example

```
STDMETHODIMP CMSProvider::Shutdown(ULONG * pulFlags) 
{ 
    HRESULT hRes = S_OK; 
    Log(true,"CMSProvider::Shutdown\n"); 
    hRes =m_pPSTMS->Shutdown(pulFlags); 
    Log(true,"CMSProvider::Shutdown returned: 0x%08X\n", hRes); 
    return hRes ;  
}
```

## See also

#### Concepts

[About the Sample Wrapped PST Store Provider](about-the-sample-wrapped-pst-store-provider.md)
  
[Installing the Sample Wrapped PST Store Provider](installing-the-sample-wrapped-pst-store-provider.md)
  
[Initializing a Wrapped PST Store Provider](initializing-a-wrapped-pst-store-provider.md)
  
[Logging On to a Wrapped PST Store Provider](logging-on-to-a-wrapped-pst-store-provider.md)
  
[Using a Wrapped PST Store Provider](using-a-wrapped-pst-store-provider.md)

