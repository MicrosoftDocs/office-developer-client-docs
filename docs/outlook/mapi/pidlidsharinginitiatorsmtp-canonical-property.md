---
title: "PidLidSharingInitiatorSmtp Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidLidSharingInitiatorSmtp
api_type:
- COM
ms.assetid: 4fb7d91d-4c51-41c1-9cb6-7b837dd12f11
description: "Last modified: March 09, 2015"
---

# PidLidSharingInitiatorSmtp Canonical Property

  
  
**Applies to**: Outlook 
  
Specifies the SMTP address of the user who initiated the sharing message. This is a property of a sharing message. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |dispidSharingInitiatorSmtp  <br/> |
|Property set:  <br/> |PSETID_Sharing  <br/> |
|Long ID (LID):  <br/> |0x00008A08  <br/> |
|Data type:  <br/> |PT_UNICODE  <br/> |
|Area:  <br/> |Sharing  <br/> |
   
## Remarks

This property must be set to the value of the **PR_SMTP_ADDRESS** ( [PidTagSmtpAddress](pidtagsmtpaddress-canonical-property.md)) property from the Address Book identified by the **dispidSharingInitiatorEid** ( [PidLidSharingInitiatorEntryId](pidlidsharinginitiatorentryid-canonical-property.md)) property and should be ignored.
  
## Related Resources

### Protocol Specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides property set definitions and references to related Exchange Server protocol specifications.
    
[[MS-OXSHARE]](http://msdn.microsoft.com/library/e4e5bd27-d5e0-43f9-a6ea-550876724f3d%28Office.15%29.aspx)
  
> Shares mailbox folders between clients.
    
### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
## See also

#### Concepts

[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

