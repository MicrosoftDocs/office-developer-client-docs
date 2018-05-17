---
title: "IABContainerCopyEntries"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IABContainer.CopyEntries
api_type:
- COM
ms.assetid: 4e775228-5ceb-4002-9b68-999fb5889b86
description: "Last modified: July 23, 2011"
---

# IABContainer::CopyEntries

  
  
**Applies to**: Outlook 
  
Copies one or more entries, typically messaging users or distribution lists.
  
```
HRESULT CopyEntries(
  LPENTRYLIST lpEntries,
  ULONG_PTR ulUIParam,
  LPMAPIPROGRESS lpProgress,
  ULONG ulFlags
);
```

## Parameters

 _lpEntries_
  
> [in] A pointer to an array of [ENTRYLIST](entrylist.md) structures that contains the entry identifiers of the entries to copy. 
    
 _ulUIParam_
  
> [in] The handle to the parent window of any dialog boxes or windows that this method displays. The  _ulUIParam_ parameter must be zero if the AB_NO_DIALOG flag is set in the  _ulFlags_ parameter. 
    
 _lpProgress_
  
> [in] A pointer to a progress object that displays a progress indicator, or NULL. If  _lpProgress_ is NULL, a progress indicator should be displayed by using the progress object supplied by MAPI through the [IMAPISupport::DoProgressDialog](imapisupport-doprogressdialog.md) method. The  _lpProgress_ parameter is ignored if the AB_NO_DIALOG flag is set in  _ulFlags_.
    
 _ulFlags_
  
> [in] A bitmask of flags that controls how the copy operation is performed. The following flags can be set:
    
AB_NO_DIALOG 
  
> Suppresses display of a progress indicator. If this flag is not set, a progress indicator is displayed.
    
CREATE_CHECK_DUP_LOOSE 
  
> Indicates that a loose level of duplicate entry checking should be performed. The implementation of loose duplicate entry checking is provider specific. For example, a provider can define a loose match as any two entries that have the same display name.
    
CREATE_CHECK_DUP_STRICT 
  
> Indicates that a strict level of duplicate entry checking should be performed. The implementation of strict duplicate entry checking is provider specific. For example, a provider can define a strict match as any two entries that have both the same display name and messaging address.
    
CREATE_REPLACE 
  
> Indicates that a new entry should replace an existing one if it is determined that the two are duplicates.
    
## Return value

S_OK 
  
> The copy operation succeeded.
    
MAPI_W_PARTIAL_COMPLETION 
  
> The copy operation succeeded overall, but one or more of the entries could not be copied. When this value is returned, the call should be handled as successful. To test for this value, use the **HR_FAILED** macro. For more information, see [Using Macros for Error Handling](using-macros-for-error-handling.md).
    
## Remarks

The **IABContainer::CopyEntries** method copies entries from the same container or a different container. A call to **CopyEntries** is functionally equivalent to making the following calls for each entry to be copied: 
  
1. The [IABContainer::CreateEntry](iabcontainer-createentry.md) method to create the new entry. 
    
2. The [IMAPIProp::GetProps](imapiprop-getprops.md) method to read properties from the entry to be copied. 
    
3. The [IMAPIProp::SetProps](imapiprop-setprops.md) method to write properties to the new entry. 
    
4. The new entry's [IMAPIProp::SaveChanges](imapiprop-savechanges.md) method to perform a save. 
    
5. The new entry's [IUnknown::Release](http://msdn.microsoft.com/en-us/library/ms682317%28VS.85%29.aspx) method to release the container's reference. 
    
## Notes to Implementers

All containers that support the **IABContainer::CopyEntries** method must be modifiable. Set your container's AB_MODIFIABLE flag in its **PR_CONTAINER_FLAGS** ( [PidTagContainerFlags](pidtagcontainerflags-canonical-property.md)) property to indicate that it is modifiable. 
  
You must support all of the flags; however, the interpretation and use of these flags is implementation specific—that is, you can determine what the semantics of the CREATE_CHECK_DUP_LOOSE and CREATE_CHECK_DUP_STRICT flags mean in the context of your implementation. If you cannot or do not determine whether an entry is a duplicate, always allow the entry to be copied. 
  
If the CREATE_REPLACE flag is set, always copy the entry regardless of whether CREATE_CHECK_DUP_LOOSE or CREATE_CHECK_DUP_STRICT is set and whether the entry is a duplicate. 
  
If CREATE_REPLACE is not set and CREATE_CHECK_DUP_STRICT is set, check for duplicates. If an entry is determined to be a duplicate, do not copy the entry. 
  
You do not need to support CREATE_REPLACE; not supporting CREATE_REPLACE means that you can safely ignore it and always perform a copy. 
  
Return the warning MAPI_W_PARTIAL_COMPLETION only if a nonduplicate entry cannot be copied. 
  
## Notes to Callers

Use the CREATE_CHECK_DUP_LOOSE and CREATE_CHECK_DUP_STRICT flags to indicate to the provider how you want the container to perform duplicate-entry checking. If you need to have an entry added regardless of whether it is a duplicate, either do not set either of these flags or set the CREATE_REPLACE flag. CREATE_REPLACE indicates that you do not care if an entry is a duplicate; you always want it to replace the original entry. 
  
## See also

#### Reference

[ENTRYLIST](entrylist.md)
  
[IABContainer::CreateEntry](iabcontainer-createentry.md)
  
[IMAPIProgress : IUnknown](imapiprogressiunknown.md)
  
[IMAPIProp::SaveChanges](imapiprop-savechanges.md)
  
[IABContainer : IMAPIContainer](iabcontainerimapicontainer.md)

