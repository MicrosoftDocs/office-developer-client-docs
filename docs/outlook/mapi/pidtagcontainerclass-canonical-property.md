---
title: "PidTagContainerClass Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagContainerClass
api_type:
- HeaderDef
ms.assetid: db249e9e-f1f0-4b95-8cd9-daa7c53ddb32
description: "Last modified: March 09, 2015"
---

# PidTagContainerClass Canonical Property

  
  
**Applies to**: Outlook 
  
Contains a text string describing the type of a folder. Although this property is generally ignored, versions of Microsoft® Exchange Server prior to Exchange Server 2003 Mailbox Manager expect this property to be present.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_CONTAINER_CLASS, PR_CONTAINER_CLASS_A, PR_CONTAINER_CLASS_W  <br/> |
|Identifier:  <br/> |0x3613  <br/> |
|Data type:  <br/> |PT_STRING8, PT_UNICODE  <br/> |
|Area:  <br/> |Container  <br/> |
   
## Remarks

These properties are not normally used by Exchange Server. However, Microsoft Office Outlook® attaches them to mailbox folders. In addition, versions of Exchange Server prior to Exchange Server 2003 Mailbox Manager might incorrectly handle folders that do not have these properties.
  
These properties can be assigned the string values in the following table.
  
|**Value**|**Contents of Folder**|
|:-----|:-----|
|IPF.Appointment  <br/> |Appointments  <br/> |
|IPF.Contact  <br/> |Contacts  <br/> |
|IPF.Journal  <br/> |Outlook Journal entries  <br/> |
|IPF.Note  <br/> |Mail Messages and notes  <br/> |
|IPF.StickyNote  <br/> |Outlook Sticky Notes  <br/> |
|IPF.Task  <br/> |Outlook Tasks  <br/> |
   
For folders that contain mail messages, these properties should be set to IPF.Note.
  
## Related resources

### Protocol Specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXOSFLD]](http://msdn.microsoft.com/library/a60e9c16-2ba8-424b-b60c-385a8a2837cb%28Office.15%29.aspx)
  
> Specifies the properties and operations for creating and locating the special folders in a mailbox.
    
[[MS-OXOCAL]](http://msdn.microsoft.com/library/09861fde-c8e4-4028-9346-e7c214cfdba1%28Office.15%29.aspx)
  
> Specifies the properties and operations for appointment, meeting request, and response messages.
    
[[MS-OXOCNTC]](http://msdn.microsoft.com/library/9b636532-9150-4836-9635-9c9b756c9ccf%28Office.15%29.aspx)
  
> Specifies the properties and operations that are permissible for contact and personal distribution list objects.
    
### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

