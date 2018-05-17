---
title: "PidTagAdditionalRenEntryIdsEx Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagAdditionalRenEntryIdsEx
api_type:
- HeaderDef
ms.assetid: b5e896e7-c0c6-4ad1-bf91-9daba3a1e4d4
description: "Last modified: March 09, 2015"
---

# PidTagAdditionalRenEntryIdsEx Canonical Property

  
  
**Applies to**: Outlook 
  
Contains special folder entry IDs for a store object. Each entry in this multi-valued property can be mapped to one or more entry IDs, that is, there is a one-to-many relationship between an entry and its associated entry IDs.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_ADDITIONAL_REN_ENTRYIDS_EX  <br/> |
|Identifier:  <br/> |0x36D9  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |Outlook application  <br/> |
   
## Remarks

If this property is used, it contains an array of blocks that specifies the entry IDs for the folders. The blocks follow the format specified by the following four tables.
  
**PersistData Block**

|**Name**|**Type**|**Size**|**Description**|
|:-----|:-----|:-----|:-----|
|**PersistID** <br/> |WORD  <br/> |2  <br/> |Type identifier value for this **PersistData** entry. See the "PersistBlockType Values" table for the list of valid values.  <br/> |
|**DataElementsSize** <br/> |WORD  <br/> |2  <br/> |Size, in bytes, of the **DataElements** field.  <br/> |
|**DataElements** <br/> |array of **PersistElement** blocks  <br/> |variable  <br/> |Indicates how many **PersistElement** entries exist for the store. See the "PersistElement Block" table for the format of this structure.  <br/> |
   
**PersistBlockType Values**

|**Name**|**Value**|**Description**|
|:-----|:-----|:-----|
|PERSIST_SENTINEL  <br/> |0x0000  <br/> |Indicates that no more **PersistData** blocks will be processed.  <br/> |
|RSF_PID_RSS_SUBSCRIPTION  <br/> |0x8001  <br/> |Indicates that this block contains data for the RSS Subscriptions folder.  <br/> |
|RSF_PID_SEND_AND_TRACK  <br/> |0x8002  <br/> |Indicates that this block contains data for the Tracked Mail Processing folder.  <br/> |
|RSF_PID_TODO_SEARCH  <br/> |0x8004  <br/> |Indicates that this block contains data for the To-Do Search folder.  <br/> |
|RSF_PID_CONV_ACTIONS  <br/> |0x8006  <br/> |Indicates that this block contains data for the Conversation Action Settings folder.  <br/> |
|RSF_PID_COMBINED_ACTIONS  <br/> |0x8007  <br/> |This value is reserved.  <br/> |
|RSF_PID_SUGGESTED_CONTACTS  <br/> |0x8008  <br/> |Indicates that this block contains data for the Suggested Contacts folder.  <br/> |
|RSF_PID_CONTACT_SEARCH  <br/> |0x8009  <br/> |Indicates that this block contains data for the Contacts Search folder.  <br/> Used only by Outlook.  <br/> |
|RSF_PID_BUDDYLIST_PDLS  <br/> |0x800A  <br/> |Indicates that this block contains data for the Instant Messaging (IM) Contact Lists folder. The referenced folder contains Personal Distribution Lists (PDLs) representing each group within the IM Contact list.  <br/> Used by both Outlook and Exchange.  <br/> |
|RSF_PID_BUDDYLIST_CONTACTS  <br/> |0x800B  <br/> |Indicates that this block contains data for the IM Contacts folder. The referenced folder contains the individual contacts referenced by the IM Contact List groups.  <br/> Used by both Outlook and Exchange.  <br/> |
   
If the **PersistBlockType** value is not one of the ones defined here, the **PersistData** block is ignored and processing is continued until either a PERSIST_SENTINEL **PersistID** is processed or the end of the stream is reached. 
  
**PersistElementBlock**

|**Name**|**Type**|**Size**|**Description**|
|:-----|:-----|:-----|:-----|
|**ElementID** <br/> |WORD  <br/> |2  <br/> |Specifies the type identifier value for this **PersistElement** block. See the "PersistElementType Values" table for a list of valid values.  <br/> |
|**ElementDataSize** <br/> |WORD  <br/> |2  <br/> |Specifies the size, in bytes, of the **ElementData** field.  <br/> |
|**ElementData** <br/> |array of binary data  <br/> |variable  <br/> |Contains the data for this **PersistID** + **ElementID** pair.  <br/> |
   
**PersistElementType Values**

|**Name**|**Value**|**Value of ElementDataSize**|**Description**|
|:-----|:-----|:-----|:-----|
|RSF_ELID_HEADER  <br/> |0x0002  <br/> |0x0004  <br/> |Indicates that this block's **ElementData** field contains a DWORD Header value. How this value is interpreted depends on the block's **PersistID** type.  <br/> For all **PersistID** types specified in [[MS-OXOSFLD]](http://msdn.microsoft.com/library/a60e9c16-2ba8-424b-b60c-385a8a2837cb.aspx), this value is zero.  <br/> |
|RSF_ELID_ENTRYID  <br/> |0x0001  <br/> |variable  <br/> |Indicates that this block contains the **EntryID** of the folder specified by **PersistID**.  <br/> |
|ELEMENT_SENTINEL  <br/> |0x0000  <br/> |0x0000  <br/> |Indicates that no more **PersistElement** blocks will be processed.  <br/> |
   
If the **PersistElementType** value is not one of the ones defined here, the **PersistElement** block is ignored and processing is continued until either an ELEMENT_SENTINEL **ElementID** is processed or the end of the stream is reached. 
  
## Related Resources

### Protocol Specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXCSPAM]](http://msdn.microsoft.com/library/522f8587-4aed-4cd6-831b-40bd87862189%28Office.15%29.aspx)
  
> Enables the handling of allow/block lists and the determination of junk e-mail messages.
    
[[MS-OXOSFLD]](http://msdn.microsoft.com/library/a60e9c16-2ba8-424b-b60c-385a8a2837cb%28Office.15%29.aspx)
  
> Specifies the properties and operations for creating and locating the special folders in a mailbox.
    
[[MS-OXPHISH]](http://msdn.microsoft.com/library/ed49ab26-ba13-4d4c-8a94-98d4ceecd4b7%28Office.15%29.aspx)
  
> Identifies and marks e-mail messages that are designed to trick recipients into divulging sensitive information (such as passwords and other personal information) to a non-trustworthy source.
    
### Header Files

Mapitags.h
  
> Contains definitions of properties listed as associated properties.
    
Mapidefs.h
  
> Provides data type definitions.
    
## See also

#### Concepts

[MAPI Property Overview](mapi-property-overview.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

