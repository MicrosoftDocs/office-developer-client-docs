---
title: "Logging on to a wrapped PST store provider"
description: "The IMSProvider Logon function and the IMSProvider SpoolerLogon function are demonstrated by using code examples from the Sample Wrapped PST Store Provider."
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
ms.assetid: 364bc5fd-2199-0bb2-142b-9b3b686b2268
---

# Logging on to a wrapped PST store provider

**Applies to**: Outlook 2013 | Outlook 2016 
  
Before you can log on MAPI to a wrapped PST store provider, you must initialize and configure the wrapped Personal Folders file (PST) store provider. For more information, see [Initializing a Wrapped PST Store Provider](initializing-a-wrapped-pst-store-provider.md).
  
After you have initialized and configured a wrapped PST store provider, you must implement two logon routines. The **[IMSProvider::Logon](imsprovider-logon.md)** function logs on MAPI to the wrapped PST store provider. The **[IMSProvider::SpoolerLogon](imsprovider-spoolerlogon.md)** function logs on the MAPI spooler to the wrapped PST store provider. 
  
In this topic, the **IMSProvider::Logon** function and the **IMSProvider::SpoolerLogon** function are demonstrated by using code examples from the Sample Wrapped PST Store Provider. The sample implements a wrapped PST provider that is intended to be used in conjunction with the Replication API. For more information about downloading and installing the Sample Wrapped PST Store Provider, see [Installing the Sample Wrapped PST Store Provider](installing-the-sample-wrapped-pst-store-provider.md). For more information about the Replication API, see [About the Replication API](about-the-replication-api.md).
  
After MAPI and the MAPI spooler are logged on to the wrapped PST store provider, it is ready to be used. For more information, see [Using a Wrapped PST Store Provider](using-a-wrapped-pst-store-provider.md).
  
## MAPI Logon routine

After the wrapped PST store provider is initialized, you must implement the **[IMSProvider::Logon](imsprovider-logon.md)** function to log on MAPI to the wrapped PST store. This function validates user credentials and gets the configuration properties for the provider. You must also implement the `SetOLFIInOST` function to set the Offline File Info (**[OLFI](olfi.md)** ). **OLFI** is a queue of long-term ID structures that is used by the wrapped PST store provider to assign an Entry ID for a new message or folder in offline mode. Finally, the **IMSProvider::Logon** function returns a message store object that the MAPI spooler and client applications can log on to in the `ppMDB` parameter. 
  
### CMSProvider::Logon() example

```cpp
STDMETHODIMP CMSProvider::Logon( 
    LPMAPISUP pSupObj, 
    ULONG ulUIParam, 
    LPTSTR pszProfileName, 
    ULONG cbEntryID, 
    LPENTRYID pEntryID, 
    ULONG ulFlags, 
    LPCIID pInterface, 
    ULONG * pcbSpoolSecurity, 
    LPBYTE * ppbSpoolSecurity, 
    LPMAPIERROR * ppMAPIError, 
    LPMSLOGON * ppMSLogon, 
    LPMDB * ppMDB) 
{ 
    HRESULT hRes = S_OK; 
    LPMDB lpPSTMDB = NULL; 
    CMsgStore* pWrappedMDB = NULL; 
 
    Log(true,"CMSProvider::Logon Pst logon Called\n"); 
 
    LPPROFSECT lpProfSect = NULL; 
    CSupport * pMySup = NULL; 
    hRes = GetGlobalProfileObject(pSupObj,&lpProfSect); 
    pMySup = new CSupport(pSupObj, lpProfSect); 
    if (!pMySup) 
    { 
        Log(true,"CMSProvider::Logon: Failed to allocate new CSupport object\n"); 
        hRes = E_OUTOFMEMORY; 
    } 
    if (SUCCEEDED(hRes)) 
    { 
        ulFlags = (ulFlags & ~MDB_OST_LOGON_ANSI) | MDB_OST_LOGON_UNICODE; 
        hRes = m_pPSTMS->Logon( 
            pMySup, 
            ulUIParam,  
            pszProfileName,  
            cbEntryID, 
            pEntryID,  
            ulFlags,  
            pInterface,  
            pcbSpoolSecurity, 
            ppbSpoolSecurity,  
            ppMAPIError,  
            ppMSLogon,  
            &lpPSTMDB); 
    } 
    Log(true,"CMSProvider::Logon returned 0x%08X\n", hRes); 
 
    // Set up the MDB to allow synchronization 
    if (SUCCEEDED(hRes)) 
    { 
        hRes = SetOLFIInOST(lpPSTMDB); 
        Log(true,"SetOLFIInOST returned 0x%08X\n", hRes); 
    } 
    // Wrap the outgoing MDB 
    pWrappedMDB = new CMsgStore (lpPSTMDB); 
    if (NULL == pWrappedMDB) 
    { 
        Log(true,"CMSProvider::Logon: Failed to allocate new CMsgStore object\n"); 
        hRes = E_OUTOFMEMORY; 
    } 
    // Copy pointer to the allocated object back into the return LPMDB object pointer 
    *ppMDB = pWrappedMDB; 
    if (lpProfSect) lpProfSect->Release(); 
 
    return hRes; 
}
```

## MAPI Spooler Logon routine

Similar to **IMSProvider::Logon**, you must implement the **[IMSProvider::SpoolerLogon](imsprovider-spoolerlogon.md)** function to log the MAPI spooler on to the wrapped PST store. A message store object that the MAPI spooler and client applications can log on to is returned in the `ppMDB` parameter. 
  
### CMSProvider::SpoolerLogon() example

```cpp
STDMETHODIMP CMSProvider::SpoolerLogon ( 
    LPMAPISUP pSupObj, 
    ULONG ulUIParam, 
    LPTSTR pszProfileName, 
    ULONG cbEntryID, 
    LPENTRYID pEntryID, 
    ULONG ulFlags, 
    LPCIID pInterface, 
    ULONG cbSpoolSecurity, 
    LPBYTE pbSpoolSecurity, 
    LPMAPIERROR * ppMAPIError, 
    LPMSLOGON * ppMSLogon, 
    LPMDB * ppMDB) 
{ 
    HRESULT hRes = S_OK; 
     
    Log(true,"CMSProvider::SpoolerLogon\n"); 
    LPPROFSECT lpProfSect = NULL; 
    CSupport * pMySup = NULL; 
    hRes = GetGlobalProfileObject(pSupObj,&lpProfSect); 
    pMySup = new CSupport(pSupObj, lpProfSect); 
    if (!pMySup) 
    { 
        Log(true,"CMSProvider::SpoolerLogon: " + 
            "Failed to allocate new CSupport object\n"); 
        hRes = E_OUTOFMEMORY; 
    } 
    if (SUCCEEDED(hRes)) 
    { 
        hRes = m_pPSTMS->SpoolerLogon(  
            pMySup,//pSupObj, 
            ulUIParam, 
            pszProfileName, 
            cbEntryID, 
            pEntryID, 
            ulFlags, 
            pInterface, 
            cbSpoolSecurity, 
            pbSpoolSecurity, 
            ppMAPIError, 
            ppMSLogon, 
            ppMDB); 
    } 
    Log(true,"CMSProvider::SpoolerLogon returned 0x%08X\n", hRes); 
 
    return hRes; 
}
```

## See also

- [About the Sample Wrapped PST Store Provider](about-the-sample-wrapped-pst-store-provider.md) 
- [Installing the Sample Wrapped PST Store Provider](installing-the-sample-wrapped-pst-store-provider.md) 
- [Initializing a Wrapped PST Store Provider](initializing-a-wrapped-pst-store-provider.md)
- [Using a Wrapped PST Store Provider](using-a-wrapped-pst-store-provider.md)
- [Shutting Down a Wrapped PST Store Provider](shutting-down-a-wrapped-pst-store-provider.md)

