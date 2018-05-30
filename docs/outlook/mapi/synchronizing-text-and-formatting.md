---
title: "Synchronizing Text and Formatting"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: d7e166f0-1214-4571-b9a8-366960772a7a
description: "Last modified: March 09, 2015"
 
 
---

# Synchronizing Text and Formatting

  
  
**Applies to**: Outlook 
  
The main challenge in sending Rich Text Format (RTF) messages is keeping the text synchronized with the formatting. To ensure that when messages arrive at their destination they are as their originators intended and that the text and formatting are synchronized, MAPI provides the [RTFSync](rtfsync.md) function. **RTFSync** is typically called by RTF-aware clients before displaying incoming messages and by the MAPI spooler when it downloads messages to a transport provider. Callers specify the area of possible discrepancy by passing one or two flags to **RTFSync**:
  
- RTF_SYNC_BODY_CHANGED to indicate a modification in message text.
    
- RTF_SYNC_RTF_CHANGED to indicate a modification in message formatting.
    
The synchronization process that occurs in **RTFSync** is a sophisticated cyclic redundancy check (CRC) of the message text that ignores some characters and converts others. Characters that most likely were added by transport providers are ignored. MAPI defines several properties for working with RTF as described in the following table. 
  
|**RTF property**|**Description**|
|:-----|:-----|
|**PR_RTF_SYNC_BODY_TAG** ([PidTagRtfSyncBodyTag](pidtagrtfsyncbodytag-canonical-property.md))  <br/> |Indicates the beginning of the real message text.  <br/> |
|**PR_RTF_SYNC_BODY_CRC** ([PidTagRtfSyncBodyCrc](pidtagrtfsyncbodycrc-canonical-property.md))  <br/> |Contains the result of the cyclic redundancy check of the message text.  <br/> |
|**PR_RTF_SYNC_BODY_COUNT** ([PidTagRtfSyncBodyCount](pidtagrtfsyncbodycount-canonical-property.md))  <br/> |Contains the number of characters in **PR_RTF_SYNC_BODY_CRC**.  <br/> |
|**PR_RTF_IN_SYNC** ([PidTagRtfInSync](pidtagrtfinsync-canonical-property.md))  <br/> |Set to TRUE when the message text and formatting have been synchronized.  <br/> |
|**PR_RTF_SYNC_PREFIX_COUNT** ([PidTagRtfSyncPrefixCount](pidtagrtfsyncprefixcount-canonical-property.md))  <br/> |Contains the number of nonwhitespace characters that preceed the message text.  <br/> |
|**PR_RTF_SYNC_TRAILING_COUNT** ([PidTagRtfSyncTrailingCount](pidtagrtfsynctrailingcount-canonical-property.md))  <br/> |Contains the number of nonwhitespace characters that trail the message text.  <br/> |
   

