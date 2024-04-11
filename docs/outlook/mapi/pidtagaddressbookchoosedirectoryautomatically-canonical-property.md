---
title: "PidTagAddressBookChooseDirectoryAutomatically Canonical Property"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
ms.assetid: cecd0679-4bc2-4399-8f89-a4e17bb909a0
description: "Enables Microsoft Outlook 2010 and Microsoft Outlook 2013 to choose the most appropriate GAL or contact folder for the current mailbox."
---

# PidTagAddressBookChooseDirectoryAutomatically Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Enables Microsoft Outlook 2010 and Microsoft Outlook 2013 to choose the most appropriate global address list (GAL) or contact folder for the current mailbox.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_AB_CHOOSE_DIRECTORY_AUTOMATICALLY  <br/> |
|Identifier:  <br/> |0x3D1C000B  <br/> |
|Property type:  <br/> |PT_BOOLEAN  <br/> |
|Area:  <br/> |Address book  <br/> |
   
## Remarks

This property corresponds to the **Choose automatically** setting in the Address Book Options dialog. When this property exists in the IID_CAPONE_PROF profile section and is set to **true**, the Address Book dialog no longer defaults to the container specified by the [SetDefaultDir](iaddrbook-setdefaultdir.md) method, but chooses an address book that Outlook 2010 or Outlook 2013 considers appropriate for the context in which the dialog was displayed. Note that this may result in a poor experience for third-party address book providers. 
  
## Related resources

### Header files

Mapitags.h
  
> Contains definitions of properties listed as associated properties.
    
Mapidefs.h
  
> Provides data type definitions.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[MAPI Constants](mapi-constants.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

