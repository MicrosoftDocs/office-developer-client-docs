---
title: "PidTagGender Canonical Property"
description: This article outlines the PidTagGender canonical property, which contains the gender of the messaging user.
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagGender
api_type:
- HeaderDef
ms.assetid: a79a139a-6813-49f6-b622-bb66d62c4462
---

# PidTagGender Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the gender of the messaging user.
  
|Property|Value|
|:-----|:-----|
|Associated properties:  <br/> |PR_GENDER  <br/> |
|Identifier:  <br/> |0x3A4D  <br/> |
|Data type:  <br/> |PT_I2  <br/> |
|Area:  <br/> |MAPI mail user  <br/> |
   
## Remarks

This property provides identification and access information about a messaging user and the content is. The content is defined by the messaging user and the messaging user's organization. 
  
The possible values for this property are defined in the gender enumeration. They are listed as follows:
  
|**Gender enumeration**|**Value**|**Description**|
|:-----|:-----|:-----|
|genderUnspecified  <br/> |0x0000  <br/> |The contact's gender is unspecified. |
|genderFemale  <br/> |0x0001  <br/> |The contact is female. |
|genderMale  <br/> |0x0002  <br/> |The contact is male. |
   
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXOCNTC]](https://msdn.microsoft.com/library/9b636532-9150-4836-9635-9c9b756c9ccf%28Office.15%29.aspx)
  
> Specifies the properties and operations that are permissible for contacts and personal distribution lists.
    
[[MS-OXOABK]](https://msdn.microsoft.com/library/f4cf9b4c-9232-4506-9e71-2270de217614%28Office.15%29.aspx)
  
> Specifies the properties and operations for lists of users, contacts, groups, and resources.
    
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

