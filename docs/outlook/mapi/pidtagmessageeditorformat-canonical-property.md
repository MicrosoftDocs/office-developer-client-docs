---
title: "PidTagMessageEditorFormat Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagMessageEditorFormat
api_type:
- HeaderDef
ms.assetid: 197b21ed-9f2f-425f-a6ed-cae1208fa2ca
description: "Last modified: March 09, 2015"
---

# PidTagMessageEditorFormat Canonical Property

  
  
**Applies to**: Outlook 
  
Specifies the format for an editor to use to display a message.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_MSG_EDITOR_FORMAT  <br/> |
|Identifier:  <br/> |0x5909  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Miscellaneous  <br/> |
   
## Remarks

The possible values for **PR_MSG_EDITOR_FORMAT** can be one of the following: 
  
|**Value**|**Description**|
|:-----|:-----|
|**EDITOR_FORMAT_DONTKNOW** <br/> |The format for the editor to use is unknown.  <br/> |
|**EDITOR_FORMAT_PLAINTEXT** <br/> |The editor should display the message in plain text format.  <br/> |
|**EDITOR_FORMAT_HTML** <br/> |The editor should display the message in HTML format.  <br/> |
|**EDITOR_FORMAT_RTF** <br/> |The editor should display the message in Rich Text Format.  <br/> |
   
By default, mail messages (with the message class **IPM.Note** or with a custom message class derived from **IPM.Note**) sent from a POP3/SMTP mail account are sent in the Transport Neutral Encapsulation Format (TNEF). The **PR_MSG_EDITOR_FORMAT** property can be used to enforce only plain text, and not TNEF, when sending a message. If **PR_MSG_EDITOR_FORMAT** is set to **EDITOR_FORMAT_PLAINTEXT**, the message is sent as plain text without TNEF. If **PR_MSG_EDITOR_FORMAT** is set to **EDITOR_FORMAT_RTF**, TNEF encoding is implicitly enabled, and the message is sent by using the default Internet format that is specified in the Outlook client.
  
There are two other ways to enforce the use of TNEF when sending a message.
  
- Setting the **dispidUseTNEF** ([PidLidUseTnef](pidlidusetnef-canonical-property.md)) named property to True on a message indicates TNEF should be included when converting the message from MAPI to MIME/SMTP. Note that **dispidUseTNEF** only applies when the message is sent from a POP3/SMTP mail account, and does not apply when the message is sent by other providers, such as Microsoft Exchange Server. **dispidUseTNEF** overrides the setting in **PR_MSG_EDITOR_FORMAT**.
    
- Using the **CCSF_USE_TNEF** flag when calling [IConverterSession::MAPIToMIMEStm](iconvertersession-mapitomimestm.md) to convert an outgoing MAPI message to a MIME stream can also enforce TNEF. This applies even if **dispidUseTNEF** is not set. 
    
## Related resources

### Protocol Specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXCFXICS]](http://msdn.microsoft.com/library/b9752f3d-d50d-44b8-9e6b-608a117c8532%28Office.15%29.aspx)
  
> Defines the basic data structures that are used in remote operations.
    
[[MS-OXOMSG]](http://msdn.microsoft.com/library/daa9120f-f325-4afb-a738-28f91049ab3c%28Office.15%29.aspx)
  
> Specifies the properties and operations that are permissible for e-mail message objects.
    
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

