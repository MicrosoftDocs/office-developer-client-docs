---
title: "Copying Address Book Entries"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 285abeb4-45c8-4e82-9a16-b935b4651afe
description: "Last modified: March 09, 2015"
 
 
---

# Copying Address Book Entries

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Your container's [IABContainer::CopyEntries](iabcontainer-copyentries.md) method is called when one or more recipients from the same or another container are to be copied into this container. **CopyEntries** has four input parameters: an array of entry identifiers representing the recipients to be copied, a window handle for the progress indicator, a progress object pointer, and a flags value. Your provider should display progress if the AB_NO_DIALOG flag is not set and use the progress object from the  _lpProgress_ parameter if it is not NULL. If  _lpProgress_ is NULL, call [IMAPISupport::DoProgressDialog](imapisupport-doprogressdialog.md) to use the MAPI progress object. For more information about displaying progress, see [Displaying a Progress Indicator](mapi-progress-indicators.md).
  
In addition to AB_NO_DIALOG to suppress a progress indicator, one of two other flags can be set to request a type of duplicate entry checking: CREATE_CHECK_DUP_LOOSE or CREATE_CHECK_DUP_STRICT. The CREATE_CHECK_DUP_LOOSE and CREATE_CHECK_DUP_STRICT flags are only suggestions as to how your provider determines duplicate entries and can be ignored. MAPI suggests that your provider implement support for these flags as follows.
  
|**Duplicate entry flag**|**Suggested implementation**|
|:-----|:-----|
|CREATE_CHECK_DUP_LOOSE  <br/> |Check if the display name in the entry to be created matches the display name of an entry already in the container.  <br/> |
|CREATE_CHECK_DUP_STRICT  <br/> |Check if both the display name and the search key in the entry to be created match the display name and search key of a container entry.  <br/> |
   
The last flag, CREATE_REPLACE, indicates that the new entry should replace the existing one if your provider has determined that an entry to be created is a duplicate of an entry already in your container. 
  
If your provider is a personal address book, include the **PR_DETAILS_TABLE** ([PidTagDetailsTable](pidtagdetailstable-canonical-property.md)) property in every copy operation. Including the details display table of a copied recipient enables your container to display the details of the recipient rather than having to call the original container to create the display.
  
 **To implement IABContainer::CopyEntries**
  
1. Determine if each entry identifier in the  _lpEntries_ parameter is in a format that your provider handles and if it is not, fail and return MAPI_E_INVALID_ENTRYID. 
    
2. If an entry identifier represents a messaging user, distribution list, or container that your provider handles:
    
1. Call your [IMAPISupport::OpenEntry](imapisupport-openentry.md) method to open the corresponding recipient. 
    
2. Copy the recipient to your container. 
    
3. If the entry identifier represents a foreign recipient:
    
1. Call your container's [IABContainer::CreateEntry](iabcontainer-createentry.md) method to create a new recipient. 
    
2. Set initial properties on the new recipient.
    
4. Call the new object's [IMAPIProp::SaveChanges](imapiprop-savechanges.md) method to save it. 
    
5. Update the container's contents table to reflect the new recipient. 
    
6. Call [IMAPISupport::Notify](imapisupport-notify.md) to send a table notification to registered clients. 
    

