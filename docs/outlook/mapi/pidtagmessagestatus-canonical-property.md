---
title: "PidTagMessageStatus Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagMessageStatus
api_type:
- HeaderDef
ms.assetid: e479e863-a8de-4f7e-9eae-3f721cd16e9a
description: "Defines the status of a message in a contents table. A message can exist in a contents table and search-results tables, and each with a different status."
---

# PidTagMessageStatus Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains a 32-bit bitmask of flags that defines the status of a message in a contents table. 
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_MSG_STATUS  <br/> |
|Identifier:  <br/> |0x0E17  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |General messaging  <br/> |
   
## Remarks

A message can exist in a contents table and in one or more search-results tables, and each instance of the message can have a different status. This property should not be considered a property on a message but a column in a contents table. 
  
A client application can set one or more of the following flags in this property: 
  
MSGSTATUS_ANSWERED 
  
> The message has been replied to. 
    
MSGSTATUS_DELMARKED 
  
> The message has been marked for subsequent deletion. 
    
MSGSTATUS_DRAFT 
  
> The message is in draft revision status. 
    
MSGSTATUS_HIDDEN 
  
> The message is to be suppressed from recipients' folder displays. 
    
MSGSTATUS_HIGHLIGHTED 
  
> The message is to be highlighted in recipients' folder displays. 
    
MSGSTATUS_REMOTE_DELETE 
  
> The message has been marked for deletion at the remote message store without downloading to the local client. 
    
MSGSTATUS_REMOTE_DOWNLOAD 
  
> The message has been marked for downloading from the remote message store to the local client. 
    
MSGSTATUS_TAGGED 
  
> The message has been tagged for a client-defined purpose.
    
The **MSGSTATUS_DELMARKED**, **MSGSTATUS_HIDDEN**, **MSGSTATUS_HIGHLIGHTED**, and **MSGSTATUS_TAGGED** flags are defined by the client. Transport and store providers pass these bits without any action. 
  
Clients can interpret these values in any way that is appropriate for their applications. One way that many clients use this property is to display messages marked for deletion with a representative icon. 
  
A remote viewer client can set **MSGSTATUS_REMOTE_DELETE** or **MSGSTATUS_REMOTE_DOWNLOAD** on messages in the header folder presented to it by the remote transport provider. The client application can examine each message header in this folder to determine whether the message should be downloaded or deleted at the remote message store. It then uses the [IMAPIFolder::SetMessageStatus](imapifolder-setmessagestatus.md) method to set the appropriate flag. **SetMessageStatus** is the only way to set any of the flags in this property; the [IMAPIProp::SetProps](imapiprop-setprops.md) method cannot be used. To retrieve this property, clients call [IMAPIFolder::GetMessageStatus](imapifolder-getmessagestatus.md) rather than [IMAPIProp::GetProps](imapiprop-getprops.md).
  
Bits 16 through 31 (0x10000 through 0x80000000) of this property are available for use by the interpersonal message (IPM) client application. All other bits are reserved for use by MAPI; those not defined in the preceding table should be initially set to zero and not altered subsequently. 
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXCFXICS]](https://msdn.microsoft.com/library/b9752f3d-d50d-44b8-9e6b-608a117c8532%28Office.15%29.aspx)
  
> Handles synchronizing messaging object data between a server and a client.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also



[IMAPITable::QueryRows](imapitable-queryrows.md)


[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

