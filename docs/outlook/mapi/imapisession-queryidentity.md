---
title: "IMAPISessionQueryIdentity"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPISession.QueryIdentity
api_type:
- COM
ms.assetid: a2cdda90-5457-49a7-b98c-7273ffe5cbbc
description: "Last modified: March 09, 2015"
---

# IMAPISession::QueryIdentity

  
  
**Applies to**: Outlook 
  
Returns the entry identifier of the object that provides the primary identity for the session.
  
```
HRESULT QueryIdentity(
  ULONG FAR * lpcbEntryID,
  LPENTRYID FAR * lppEntryID
);
```

## Parameters

 _lpcbEntryID_
  
> [out] A pointer to the byte count in the entry identifier pointed to by the  _lppEntryID_ parameter. 
    
 _lppEntryID_
  
> [out] A pointer to a pointer to the entry identifier of the object that provides the primary identity.
    
## Return value

S_OK 
  
> The primary identity was successfully returned.
    
MAPI_W_NO_SERVICE 
  
> The call succeeded, but there is no primary identity for the session. When this warning is returned, the call should be handled as successful. To test for this warning, use the **HR_FAILED** macro. For more information, see [Using Macros for Error Handling](using-macros-for-error-handling.md).
    
## Remarks

The **IMAPISession::QueryIdentity** method retrieves the primary identity for the current session and returns the value through the  _lppEntryID_ parameter. The primary identity is an object, typically a messaging user, that represents the user of a session.  _lppEntryID_ returns the primary identity for an [IMailUser](imailuserimapiprop.md) object, which is also stored as the [PidTagEntryID](pidtagentryid-canonical-property.md) property. You can use the value returned in  _lppEntryID_ to open an **IMailUser** object using [IMAPISession::OpenEntry](imapisession-openentry.md).
  
Although many service providers in multiple message services can provide the primary identity for a session, MAPI designates a single service provider. The service provider that supplies the primary identity sets the following items:
  
- The STATUS_PRIMARY_IDENTITY flag in the **PR_RESOURCE_FLAGS** ( [PidTagResourceFlags](pidtagresourceflags-canonical-property.md)) property.
    
- The **PR_IDENTITY_DISPLAY** ( [PidTagIdentityDisplay](pidtagidentitydisplay-canonical-property.md)) property.
    
- The **PR_IDENTITY_ENTRYID** ( [PidTagIdentityEntryId](pidtagidentityentryid-canonical-property.md)) property.
    
- The **PR_IDENTITY_SEARCH_KEY** ( [PidTagIdentitySearchKey](pidtagidentitysearchkey-canonical-property.md)) property.
    
If the service provider that supplies the primary identity belongs to a message service, the other service providers in the message service also set the PR_IDENTITY properties. These properties are published in the session's status table. 
  
If possible, **QueryIdentity** returns the value for the **PR_IDENTITY_ENTRYID** property from the status row tagged with STATUS_PRIMARY_IDENTITY. If the **PR_IDENTITY_ENTRYID** property is missing from the primary identity row, **QueryIdentity** returns a one-off entry identifier built with other information from that row. 
  
If the STATUS_PRIMARY_IDENTITY flag is missing from all of the **PR_RESOURCE_FLAG** columns in the status table, **QueryIdentity** returns the first entry identifier that it finds. When there is no appropriate entry identifier to return, **QueryIdentity** succeeds with the warning MAPI_W_NO_SERVICE and points  _lppEntryID_ to a hard-coded entry identifier. 
  
## Notes to Callers

You can call the [IMsgServiceAdmin::SetPrimaryIdentity](imsgserviceadmin-setprimaryidentity.md) method to assign a message service the task of supplying the session's primary identity. 
  
Another way to retrieve the primary identity is by searching the status table for the row with the **PR_RESOURCE_FLAGS** columns set to STATUS_PRIMARY_IDENTITY. For more information about this alternate way of retrieving identity information, see [Status Table and Status Objects](status-table-and-status-objects.md).
  
When you are finished using the entry identifier for the primary identity returned by **QueryIdentity**, free its memory by calling the [MAPIFreeBuffer](mapifreebuffer.md) function. 
  
For more information about identity in general, see [MAPI Primary Identity](mapi-primary-identity.md). 
  
For more information about retrieving MAPI session identity, see [Retrieving Primary and Provider Identity](retrieving-primary-and-provider-identity.md). 
  
## MFCMAPI Reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MainDlg.cpp  <br/> |CMainDlg::OnQueryIdentity  <br/> |MFCMAPI uses the **IMAPISession::QueryIdentity** method to open the address book entry for the primary identity of the session.  <br/> |
   
## See also

#### Reference

[IMAPISession::OpenEntry](imapisession-openentry.md)
  
[IMsgServiceAdmin::SetPrimaryIdentity](imsgserviceadmin-setprimaryidentity.md)
  
[MAPIFreeBuffer](mapifreebuffer.md)
  
[IMAPISession : IUnknown](imapisessioniunknown.md)
#### Concepts

[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)
  
[MAPI Primary Identity](mapi-primary-identity.md)
  
[Retrieving Primary and Provider Identity](retrieving-primary-and-provider-identity.md)
  
[Using Macros for Error Handling](using-macros-for-error-handling.md)
  
[Status Table and Status Objects](status-table-and-status-objects.md)

