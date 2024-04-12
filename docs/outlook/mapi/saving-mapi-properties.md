---
title: "Saving MAPI Properties"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: ed0c14f9-3dcf-49ad-928e-ba872d4d6b5a
 
 
---

# Saving MAPI Properties

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Many objects support a transaction model of processing whereby changes to properties are not made permanent until they are committed at a later time. Whereas changes to properties are handled by the [IMAPIProp::SetProps](imapiprop-setprops.md) and [IMAPIProp::DeleteProps](imapiprop-deleteprops.md) methods, the commit step is handled by [IMAPIProp::SaveChanges](imapiprop-savechanges.md). It isn't until after a successful call to **SaveChanges** that the most recent version of an object's properties can be accessed. 
  
When **SaveChanges** returns the error value MAPI_E_OBJECT_CHANGED, this is a warning that another client is simultaneously committing changes to the object. It is possible, depending on the provider implementing the object, for multiple clients to successfully open an object by calling its **OpenEntry** method with the MAPI_MODIFY flag set, giving them read/write access. The object that is returned from such an **OpenEntry** call is a snapshot of the storage data. Each subsequent attempt to change this data can overwrite the previous attempt. 
  
Upon receiving MAPI_E_OBJECT_CHANGED from **SaveChanges**, a client has the option to: 
  
- Make a copy of the object to hold the changes.
    
- Make another call to **SaveChanges**, specifying FORCE_SAVE. 
    
Calling **SaveChanges** with the FORCE_SAVE flag overwrites the previous save and makes a client's changes permanent. 
  
## See also



[MAPI Property Overview](mapi-property-overview.md)

