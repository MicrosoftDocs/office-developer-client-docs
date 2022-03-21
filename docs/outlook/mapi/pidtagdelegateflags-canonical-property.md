---
title: "PidTagDelegateFlags Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagDelegateFlags
api_type:
- HeaderDef
ms.assetid: 3a504594-204c-472c-8be7-dca154c94ea2
description: "Specifies whether a delegate can view the delegator's private message objects."
---

# PidTagDelegateFlags Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Specifies whether a delegate can view the delegator's private message objects.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_DELEGATE_FLAGS  <br/> |
|Identifier:  <br/> |0x686B  <br/> |
|Data type:  <br/> |PT_MV_LONG  <br/> |
|Area:  <br/> |Message class-defined transmittable  <br/> |
   
## Remarks

Each entry of this property must be set to one of the following values.
  
|**Flag**|**Value**|**Description**|
|:-----|:-----|:-----|
|HidePrivate  <br/> |0  <br/> |The delegate should not be allowed to view private message objects. |
|ShowPrivate  <br/> |1  <br/> |The delegate should be allowed to view private message objects. |
   
This property must be set in the delegate information object. The value of "ShowPrivate" indicates that the delegator wants to make private message objects visible. This preference is applicable to all folders for which the delegate has a role of reviewer, author, or editor.
  
## Related resources

### Protocol specifications

[[MS-OXODLGT]](https://msdn.microsoft.com/library/01a89b11-9c43-4c40-b147-8f6a1ef5a44f%28Office.15%29.aspx)
  
> Specifies methods for connecting to and configuring mailboxes as delegates, and interactions with message and calendar objects when they act on behalf of another user.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

