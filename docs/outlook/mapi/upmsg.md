---
title: "UPMSG"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
ms.assetid: 5fe3956b-819a-3edf-0e49-7a44bcfbabcd
---

# UPMSG

**Applies to**: Outlook 2013 | Outlook 2016 
  
Information for uploading an Outlook item during the [upload message state](upload-message-state.md).
  
## Quick info

```cpp
struct UPMSG 
{ 
    ULONG ulFlags; 
    LPMESSAGE pmsg; 
    MEID meid; 
    SBinary binReserved1; 
    SBinary binReserved2; 
    FEID feid; 
    SBinary binChg; 
    SBinary binPcl; 
    SKEY skeySrc; 
};
```

## Members

 _ulFlags_
  
> [out]/[in] Flags to determine appropriate behavior during the upload. 
    
  - UPM_ASSOC
    
    - [out] Item is associated.
    
  - UPM_NEW
    
    - [out] New item. 
    
  - UPM_MOV
    
    - [out] Item was moved here.
    
  - UPM_MOD_PROPS
    
    - [out] Item properties were modified.
    
  - UPM_HEADER
    
    - [out] Item is a message header.
    
  - UPM_OK
    
    - [in] Upload was successful. The client sets this after uploading information to the server.
    
  - UPM_MOVED
    
    - [in] Item was moved successfully.
    
  - UPM_COMMIT
    
    - [in] Commit upload state now.
    
  - UPM_DELETE
    
    - [in] Delete item now.
    
  - UPM_SAVE
    
    - [in] Save changes to the item.
    
_pmsg_
  
> [out] Open item object. See mapidefs.h for the type definition of **LPMESSAGE**. 
    
_meid_
  
> [out] Entry ID of item.
    
_binReserved1_
  
> [in] This member is reserved for the internal use of Outlook and is not supported. 
    
_binReserved2_
  
> [in] This member is reserved for the internal use of Outlook and is not supported. 
    
_feid_
  
> [out] Entry ID of the source folder, if item was moved.
    
_binChg_
  
> [out] Change key of the destination item, if item was moved. See mapidefs.h for the type definition of **SBinary**. 
    
_binPcl_
  
> [out] Change list of the destination item, if item was moved. See mapidefs.h for the type definition of **SBinary**. 
    
_skeySrc_
  
> [out] Source key of the source item, if item was moved.
    
## See also

- [About the Replication API](about-the-replication-api.md)
- [About the Replication State Machine](about-the-replication-state-machine.md)
- [MAPI Constants](mapi-constants.md)
- [FEID](feid.md)
- [MEID](meid.md)
- [SKEY](skey.md)

