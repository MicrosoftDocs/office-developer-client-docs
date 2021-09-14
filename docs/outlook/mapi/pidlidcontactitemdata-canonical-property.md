---
title: "PidLidContactItemData Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidLidContactItemData
api_type:
- COM
ms.assetid: 411e8f81-c2b9-440a-9e9a-d6add5e4be63
description: "Last modified: March 09, 2015"
---

# PidLidContactItemData Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Used to display the contact information.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |dispidContactItemData  <br/> |
|Property set:  <br/> |PSETID_Address  <br/> |
|Long ID (LID):  <br/> |0x00008007  <br/> |
|Data type:  <br/> |PT_MV_LONG  <br/> |
|Area:  <br/> |Contact  <br/> |
   
## Remarks

If present, the property must have six entries, each corresponding to a visible field in the application's user interface.
  
|**One-based index into the multi-valued property**|**The value must be one of the following**|**Description**|
|:-----|:-----|:-----|
|1  <br/> |0x00000001  <br/> |The application should display the contact's home address.  <br/> |
|1  <br/> |0x00000002 or 0x00000000  <br/> |The application should display the contact's work.  <br/> |
|1  <br/> |0x00000003  <br/> |The application should display the contact's other address.  <br/> |
|2  <br/> |0x00008080  <br/> |The application should display Email1.  <br/> |
|2  <br/> |0x00008090  <br/> |The application should display Email2.  <br/> |
|2  <br/> |0x000080A0  <br/> |The application should display Email3.  <br/> |
|3,4,5,6  <br/> |PropertyID of any of the telephone properties or any of the fax numbers that are specified in [[MS-OXOCNTC]](https://msdn.microsoft.com/library/9b636532-9150-4836-9635-9c9b756c9ccf%28Office.15%29.aspx).  <br/> |The application should display the corresponding property.  <br/> |
   
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides property set definitions and references to related Exchange Server protocol specifications.
    
[[MS-OXOCNTC]](https://msdn.microsoft.com/library/9b636532-9150-4836-9635-9c9b756c9ccf%28Office.15%29.aspx)
  
> Specifies the properties and operations that are permissible for contacts and personal distribution lists.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

