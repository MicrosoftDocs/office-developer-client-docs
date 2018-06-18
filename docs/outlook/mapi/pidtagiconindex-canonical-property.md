---
title: "PidTagIconIndex Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagIconIndex
api_type:
- HeaderDef
ms.assetid: 35bb0d6d-41d4-47d6-b161-be3721894201
description: "Last modified: March 09, 2015"
---

# PidTagIconIndex Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains a number that indicates which icon to use when you display a group of email objects.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_ICON_INDEX  <br/> |
|Identifier:  <br/> |0x1080  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |General messaging  <br/> |
   
## Remarks

This property, if it exists, is a hint to the client. The client may ignore the value of this property. 
  
|**Mail item state**|**Icon Index**|
|:-----|:-----|
|New mail  <br/> |0xFFFFFFFF  <br/> |
|Post  <br/> |0x00000001  <br/> |
|Other  <br/> |0x00000003  <br/> |
|Read mail  <br/> |0x00000100  <br/> |
|Unread mail  <br/> |0x00000101  <br/> |
|Submitted mail  <br/> |0x00000102  <br/> |
|Unsent mail  <br/> |0x00000103  <br/> |
|Receipt mail  <br/> |0x00000104  <br/> |
|Replied mail  <br/> |0x00000105  <br/> |
|Forwarded mail  <br/> |0x00000106  <br/> |
|Remote mail  <br/> |0x00000107  <br/> |
|Delivery mail  <br/> |0x00000108  <br/> |
|Read mail  <br/> |0x00000109  <br/> |
|Nondelivery mail  <br/> |0x0000010A  <br/> |
|Nonread mail  <br/> |0x0000010B  <br/> |
|Recall_S mail  <br/> |0x0000010C  <br/> |
|Recall_F mail  <br/> |0x0000010D  <br/> |
|Tracking mail  <br/> |0x0000010E  <br/> |
|Out of office mail  <br/> |0x0000011B  <br/> |
|Recall mail  <br/> |0x0000011C  <br/> |
|Tracked mail  <br/> |0x00000130  <br/> |
|Contact  <br/> |0x00000200  <br/> |
|Distribution list  <br/> |0x00000202  <br/> |
|Sticky note blue  <br/> |0x00000300  <br/> |
|Sticky note green  <br/> |0x00000301  <br/> |
|Sticky note pink  <br/> |0x00000302  <br/> |
|Sticky note yellow  <br/> |0x00000303  <br/> |
|Sticky note white  <br/> |0x00000304  <br/> |
|Single instance appointment  <br/> |0x00000400  <br/> |
|Recurring appointment  <br/> |0x00000401  <br/> |
|Single instance meeting  <br/> |0x00000402  <br/> |
|Recurring meeting  <br/> |0x00000403  <br/> |
|Meeting request  <br/> |0x00000404  <br/> |
|Accept  <br/> |0x00000405  <br/> |
|Decline  <br/> |0x00000406  <br/> |
|Tentativly  <br/> |0x00000407  <br/> |
|Cancellation  <br/> |0x00000408  <br/> |
|Informational update  <br/> |0x00000409  <br/> |
|Task/task  <br/> |0x00000500  <br/> |
|Unassigned recurring task  <br/> |0x00000501  <br/> |
|Assignee's task  <br/> |0x00000502  <br/> |
|Assigner's task  <br/> |0x00000503  <br/> |
|Task request  <br/> |0x00000504  <br/> |
|Task acceptance  <br/> |0x00000505  <br/> |
|Task rejection  <br/> |0x00000506  <br/> |
|Journal conversation  <br/> |0x00000601  <br/> |
|Journal email message  <br/> |0x00000602  <br/> |
|Journal meeting request  <br/> |0x00000603  <br/> |
|Journal meeting response  <br/> |0x00000604  <br/> |
|Journal task request  <br/> |0x00000606  <br/> |
|Journal task response  <br/> |0x00000607  <br/> |
|Journal note  <br/> |0x00000608  <br/> |
|Journal fax  <br/> |0x00000609  <br/> |
|Journal phone call  <br/> |0x0000060A  <br/> |
|Journal letter  <br/> |0x0000060C  <br/> |
|Journal Microsoft Office Word  <br/> |0x0000060D  <br/> |
|Journal Microsoft Office Excel  <br/> |0x0000060E  <br/> |
|Journal Microsoft Office PowerPoint  <br/> |0x0000060F  <br/> |
|Journal Microsoft Office Access  <br/> |0x00000610  <br/> |
|Journal document  <br/> |0x00000612  <br/> |
|Journal meeting  <br/> |0x00000613  <br/> |
|Journal meeting cancellation  <br/> |0x00000614  <br/> |
|Journal remote session  <br/> |0x00000615  <br/> |
   
## Related resources

### Protocol specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXOMSG]](http://msdn.microsoft.com/library/daa9120f-f325-4afb-a738-28f91049ab3c%28Office.15%29.aspx)
  
> Specifies the properties and operations that are permissible on email message objects.
    
[[MS-OXOCAL]](http://msdn.microsoft.com/library/09861fde-c8e4-4028-9346-e7c214cfdba1%28Office.15%29.aspx)
  
> Specifies the properties and operations for appointment, meeting request, and response messages.
    
[[MS-OXOTASK]](http://msdn.microsoft.com/library/55600ec0-6195-4730-8436-59c7931ef27e%28Office.15%29.aspx)
  
> Specifies the properties and operations that are permissible on contacts and personal distribution lists.
    
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

