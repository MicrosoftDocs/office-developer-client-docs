---
title: "Accessing Objects by Using the Session"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: ecada707-2960-41ec-be7e-619cad257c57
description: "Last modified: March 09, 2015"
 
 
---

# Accessing Objects by Using the Session

  
  
**Applies to**: Outlook 
  
The session pointer that you receive from your call to [MAPILogonEx](mapilogonex.md) can be used to access a wide variety of objects. The following table lists the methods that are used to access various objects: 
  
|**Object**|**Session method**|
|:-----|:-----|
|Profile section  <br/> |[IMAPISession::OpenProfileSection](imapisession-openprofilesection.md) <br/> |
|Message store  <br/> |[IMAPISession::OpenMsgStore](imapisession-openmsgstore.md) <br/> |
|Address book  <br/> |[IMAPISession::OpenAddressBook](imapisession-openaddressbook.md) <br/> |
|Message service administration object  <br/> |[IMAPISession::AdminServices](imapisession-adminservices.md) <br/> |
|Folder, message, address book container, distribution list, or messaging user  <br/> |[IMAPISession::OpenEntry](imapisession-openentry.md) <br/> |
   
With the **OpenEntry** method and a valid entry identifier, you can open any address book or message store provider object. There are other **OpenEntry** methods in MAPI, in addition to the **IMAPISession** method. **OpenEntry** is implemented in the following objects: 
  
|**Object**|**Method**|
|:-----|:-----|
|Address book provider's logon object  <br/> |[IABLogon::OpenEntry](iablogon-openentry.md) <br/> |
|Address book  <br/> |[IAddrBook::OpenEntry](iaddrbook-openentry.md) <br/> |
|Address book container  <br/> |[IMAPIContainer::OpenEntry](imapicontainer-openentry.md) <br/> |
|Session  <br/> |[IMAPISession::OpenEntry](imapisession-openentry.md) <br/> |
|Message store  <br/> |[IMsgStore::OpenEntry](imsgstore-openentry.md) <br/> |
|Message store provider's logon object  <br/> |[IMSLogon::OpenEntry](imslogon-openentry.md) <br/> |
|Folder  <br/> |[IMAPIContainer::OpenEntry](imapicontainer-openentry.md) <br/> |
|Support object  <br/> |[IMAPISupport::OpenEntry](imapisupport-openentry.md) <br/> |
   
Some **OpenEntry** methods require an entry identifier of the object to be opened, as does **IMAPISession::OpenEntry**; other methods allow NULL to be specified. A NULL entry identifier is interpreted differently depending on the object. For example, when you call **IAddrBook::OpenEntry** with a NULL entry identifier, MAPI opens the root container of the address book. The message store's **OpenEntry** method behaves similarly; it opens the root folder of the message store. **IMAPIContainer::OpenEntry**, implemented by both folders and address book containers, might return MAPI_E_INVALID_PARAMETER or the root container, depending on the implementer. 
  
In addition to disallowing a NULL value for the entry identifier, the session's **OpenEntry** method differs from other **OpenEntry** methods because its job is not to open objects. Instead, it examines the entry identifier and forwards the call to another **OpenEntry** method implemented by the appropriate service provider. For example, if you call **IMAPISession::OpenEntry** with the entry identifier of a message, MAPI calls the **IMSLogon::OpenEntry** method of the message store responsible for the message. 
  
In addition to using the session to open objects, clients use it to compare them. The [IMAPISession::CompareEntryIDs](imapisession-compareentryids.md) method compares objects by comparing their entry identifiers. If the [MAPIUID](mapiuid.md) structures contained within the entry identifiers belong to the same service provider, MAPI forwards the call to that provider. **CompareEntryIDs** returns an error value when the two entry identifiers do not match. Although this method can compare entry identifiers that belong to any type of object, **CompareEntryIDs** works best for higher level objects such as message stores and address book containers. To compare lower level objects, compare directly the objects' search keys ( **PR_SEARCH_KEY** ([PidTagSearchKey](pidtagsearchkey-canonical-property.md))) or record keys ( **PR_RECORD_KEY** ([PidTagRecordKey](pidtagrecordkey-canonical-property.md))). 
  
Like **OpenEntry**, **CompareEntryIDs** is implemented by multiple objects. Choose which **OpenEntry** and **CompareEntryID** method to use according to the amount of information that you have about the object or objects to be opened or compared. Use the following guidelines when deciding which interface method to call: 
  
- If you have no information about the target objects, call [IMAPISession::OpenEntry](imapisession-openentry.md) or [IMAPISession::CompareEntryIDs](imapisession-compareentryids.md). This approach enables access to any object, but is the slowest of the three.
    
- If you know that the target objects are address book entries rather than, for example, folders, call the [IAddrBook::OpenEntry](iaddrbook-openentry.md) or [IAddrBook::CompareEntryIDs](iaddrbook-compareentryids.md) method. **IAddrBook::OpenEntry** opens the root container of the address book when NULL is specified as the target object. This approach enables access to any address book object and is faster than using **IMAPISession**, but slower than using **IMAPIContainer**.
    
- If the entry identifier being used is a short-term entry identifier or if you know that the target objects belong to a particular address book container or folder, call the [IMAPIContainer::OpenEntry](imapicontainer-openentry.md) method. This approach yields the fastest performance, but enables access only to objects in a specific container or folder. 
    

