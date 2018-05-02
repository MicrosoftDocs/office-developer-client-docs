---
title: "IMSProviderSpoolerLogon"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMSProvider.SpoolerLogon
api_type:
- COM
ms.assetid: 79d5af23-efad-4013-a330-56babfb2bb0f
description: "Last modified: July 23, 2011"
---

# IMSProvider::SpoolerLogon

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
Logs the MAPI spooler on to a message store.
  
```
HRESULT SpoolerLogon(
  LPMAPISUP lpMAPISup,
  ULONG_PTR ulUIParam,
  LPSTR lpszProfileName,
  ULONG cbEntryID,
  LPENTRYID lpEntryID,
  ULONG ulFlags,
  LPCIID lpInterface,
  ULONG cbSpoolSecurity,
  LPBYTE lpbSpoolSecurity,
  LPMAPIERROR FAR * lppMAPIError,
  LPMSLOGON FAR * lppMSLogon,
  LPMDB FAR * lppMDB     
);
```

## Parameters

 _lpMAPISup_
  
> [in] A pointer to the MAPI support object for the message store.
    
 _ulUIParam_
  
> [in] A handle to the parent window of any dialog boxes or windows this method displays. 
    
 _lpszProfileName_
  
> [in] A pointer to a string that contains the name of the profile being used for the MAPI spooler logon. This string can be displayed in dialog boxes, written out to a log file, or simply ignored. It must be in Unicode format if the MAPI_UNICODE flag is set in the  _ulFlags_ parameter. 
    
 _cbEntryID_
  
> [in] The size, in bytes, of the entry identifier pointed to by the  _lpEntryID_ parameter. 
    
 _lpEntryID_
  
> [in] A pointer to the entry identifier for the message store. Passing NULL in the  _lpEntryID_ parameter indicates that a message store has not yet been selected and that dialog boxes that enable the user to select a message store can be presented. 
    
 _ulFlags_
  
> [in] A bitmask of flags that controls how the logon is performed. The following flags can be set:
    
MAPI_DEFERRED_ERRORS 
  
> The call is allowed to succeed even if the underlying object is not available to the calling implementation. If the object is not available, a subsequent call to the object might raise an error.
    
MAPI_UNICODE 
  
> The passed-in strings are in Unicode format. If MAPI_UNICODE is not set, the strings are in ANSI format.
    
MDB_NO_DIALOG 
  
> Prevents the display of logon dialog boxes. If this flag is set, the error value MAPI_E_LOGON_FAILED is returned if the logon is unsuccessful. If this flag is not set, the message store provider can prompt the user to correct a name or password, to insert a disk, or to perform other actions necessary to establish connection to the store.
    
MDB_WRITE 
  
> Requests read/write permission.
    
 _lpInterface_
  
> [in] A pointer to the interface identifier (IID) for the message store to log on to. Passing NULL indicates the MAPI interface for the message store ([IMsgStore](imsgstoreimapiprop.md)) is returned. The  _lpInterface_ parameter can also be set to an identifier for an appropriate interface for the message store (for example IID_IUnknown or IID_IMAPIProp). 
    
 _cbSpoolSecurity_
  
> [in] A pointer to the size, in bytes, of validation data in the  _lppbSpoolSecurity_ parameter. 
    
 _lpbSpoolSecurity_
  
> [in] A pointer to a pointer to validation data. The **SpoolerLogon** method uses this data to log the MAPI spooler on to the same store as the message store provider previously logged on to by using the [IMSProvider::Logon](imsprovider-logon.md) method. 
    
 _lppMAPIError_
  
> [out] A pointer to a pointer to the returned [MAPIERROR](mapierror.md) structure, if any, that contains version, component, and context information for an error. The  _lppMAPIError_ parameter can be set to NULL if there is no **MAPIERROR** structure to return. 
    
 _lppMSLogon_
  
> [out] A pointer to the pointer to the message store logon object for MAPI to log on to.
    
 _lppMDB_
  
> [out] A pointer to the pointer to the message store object for the MAPI spooler and client applications to log on to.
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
MAPI_E_UNCONFIGURED 
  
> The profile does not contain enough information for the logon to complete. When this value is returned, MAPI calls the message store provider's message service entry point function.
    
MAPI_W_ERRORS_RETURNED 
  
> The call succeeded, but the message store provider has error information available. When this warning is returned, the call should be handled as successful. To test for this warning, use the **HR_FAILED** macro. For more information, see [Using Macros for Error Handling](using-macros-for-error-handling.md). To get the error information from the provider, call the [IMAPISession::GetLastError](imapisession-getlasterror.md) method. 
    
## Remarks

The MAPI spooler calls the **IMSProvider::SpoolerLogon** method to log on to a message store. The MAPI spooler should use the message store object returned by the message store provider in the  _lppMDB_ parameter during and after logon. 
  
For consistency with the [IMSProvider::Logon](imsprovider-logon.md) method, the provider also returns a message store logon object in the  _lppMSLogon_ parameter. The use of the store object and the logon object are identical for usual store logon; there should be a one-to-one correspondence between the logon object and the store object such that the objects act as if they are one object that exposes two interfaces. The two objects are created together and freed together. 
  
The store provider should internally mark the returned message store object to indicate that the store is being used by the MAPI spooler. Some of the methods for this store object behave differently than for the message store object provided to client applications. Keeping this internal mark is the most common way of triggering the behavior specific to the MAPI spooler.
  
## See also

#### Reference

[IMSProvider::Logon](imsprovider-logon.md)
  
[MAPIERROR](mapierror.md)
  
[IMSProvider : IUnknown](imsprovideriunknown.md)

