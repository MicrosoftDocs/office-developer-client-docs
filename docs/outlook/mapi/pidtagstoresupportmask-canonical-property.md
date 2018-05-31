---
title: "PidTagStoreSupportMask Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagStoreSupportMask
api_type:
- COM
ms.assetid: ada5694a-b5b1-471f-be33-906fc052681a
description: "Last modified: March 09, 2015"
---

# PidTagStoreSupportMask Canonical Property

  
  
**Applies to**: Outlook 
  
Contains a bitmask of flags that client applications query to determine the characteristics of a message store. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_STORE_SUPPORT_MASK  <br/> |
|Identifier:  <br/> |0x340D  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Miscellaneous  <br/> |
   
## Remarks

This property discloses the capabilities of a message store to client applications that are planning to send it a message. The flags can support decisions by a client or another store, such as whether to send **PR_BODY** ([PidTagBody](pidtagbody-canonical-property.md)) or only **PR_RTF_COMPRESSED** ([PidTagRtfCompressed](pidtagrtfcompressed-canonical-property.md)). A client should never set **PR_STORE_SUPPORT_MASK**; an attempt to set this flag returns MAPI_E_COMPUTED. 
  
One or more of the following flags can be set for the **PR_STORE_SUPPORT_MASK** bitmask: 
  
STORE_ANSI_OK
  
> (131072, 0x00020000) The message store supports properties that contain ANSI (8-bit) characters.
    
STORE_ATTACH_OK 
  
> (32, 0x00000020) The message store supports attachments (OLE or non-OLE) to messages. 
    
STORE_CATEGORIZE_OK 
  
> (1024, 0x00000400) The message store supports categorized views of tables. 
    
STORE_CREATE_OK 
  
> (16, 0x00000010) The message store supports creation of new messages. 
    
STORE_ENTRYID_UNIQUE 
  
> (1, 0x00000001) Entry identifiers for the objects in the message store are unique, that is, never reused during the life of the store. 
    
STORE_HTML_OK 
  
> (65536, 0x00010000) The message store supports HTML messages, stored in the **PR_BODY_HTML** ([PidTagBodyHtml](pidtagbodyhtml-canonical-property.md)) property. If your development environment uses a MAPIDEFS.H file that does not include STORE_HTML_OK, use the value 0x00010000 instead. 
    
STORE_ITEMPROC
  
> (2097152, 0x00200000) In a wrapped PST store, indicates that when a new message arrives at the store, the store performs rules and spam filter processing on the message separately. The store calls [IMAPISupport::Notify](imapisupport-notify.md), setting **fnevNewMail** in the [NOTIFICATION](notification.md) structure that is passed as a parameter, and then passes the details of the new message to the listening client. Subsequently, when the listening client receives the notification, it does not process rules on the message. 
    
STORE_LOCALSTORE
  
> (524288, 0x00080000) This flag is reserved and should not be used.
    
STORE_MODIFY_OK 
  
> (8, 0x00000008) The message store supports modification of its existing messages. 
    
STORE_MV_PROPS_OK 
  
> (512, 0x00000200) The message store supports multivalued properties, guarantees the stability of value order in a multivalued property throughout a save operation, and supports instantiation of multivalued properties in tables. 
    
STORE_NOTIFY_OK 
  
> (256, 0x00000100) The message store supports notifications. 
    
STORE_OLE_OK 
  
> (64, 0x00000040) The message store supports OLE attachments. The OLE data can be accessed through an **IStorage** interface, such as that available through the **PR_ATTACH_DATA_OBJ** ([PidTagAttachDataObject](pidtagattachdataobject-canonical-property.md)) property. 
    
STORE_PUBLIC_FOLDERS 
  
> (16384, 0x00004000) The folders in this store are public (multi-user), not private (possibly multi-instance but not multi-user). 
    
STORE_PUSHER_OK
  
> (8388608, 0x00800000) The MAPI Protocol Handler will not crawl the store, and the store is responsible for pushing any changes through notifications to the indexer to have messages indexed.
    
STORE_READONLY 
  
> (2, 0x00000002) All interfaces for the message store have a read-only access level. 
    
STORE_RESTRICTION_OK 
  
> (4096, 0x00001000) The message store supports restrictions. 
    
STORE_RTF_OK 
  
> (2048, 0x00000800) The message store supports Rich Text Format (RTF) messages, usually compressed, and the store itself keeps **PR_BODY** and **PR_RTF_COMPRESSED** synchronized. 
    
STORE_RULES_OK
  
> (268435456, 0x10000000) Indicates that rules should be stored in this PST store even if it is not the default store. When **STORE_RULES_OK** is used in conjunction with **NON_EMS_XP_SAVE**, rules are able to run on non-default PST wrapped stores.
    
STORE_SEARCH_OK 
  
> (4, 0x00000004) The message store supports search-results folders. 
    
STORE_SORT_OK 
  
> (8192, 0x00002000) The message store supports sorting views of tables. 
    
STORE_SUBMIT_OK 
  
> (128, 0x00000080) The message store supports marking a message for submission. 
    
STORE_UNCOMPRESSED_RTF 
  
> (32768, 0x00008000) The message store supports storage of RTF messages in uncompressed form. An uncompressed RTF stream is identified by the value **dwMagicUncompressedRTF** in the stream header. The **dwMagicUncompressedRTF** value is defined in the RTFLIB.H file. 
    
STORE_UNICODE_OK
  
> (262144, 0x00040000) Indicates that the message store supports Unicode storage. A client can look for the presence of the flag to decide whether to request or to save Unicode information to the store. 
    
An RTF version of a message can always be stored, even if the message store is non-RTF-aware. If the STORE_RTF_OK bit is not set for a particular store, a client maintaining RTF versions must itself call the [RTFSync](rtfsync.md) function to keep the **PR_BODY** and **PR_RTF_COMPRESSED** versions synchronized for text content. RTF is always stored in **PR_RTF_COMPRESSED**, whether it is actually compressed or not. 
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXMSG]](http://msdn.microsoft.com/library/b046868c-9fbf-41ae-9ffb-8de2bd4eec82%28Office.15%29.aspx)
  
> Describes the format of messages used to send information related to sharing folders on the client.
    
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

