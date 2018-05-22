---
title: "About MAPI URLs for Notification-Based Indexing"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
ms.assetid: 9cb35f0a-267e-2d85-1701-02d52578a0b8
description: "Last modified: November 08, 2011"
---

# About MAPI URLs for Notification-Based Indexing

**Applies to**: Outlook 
  
When a store provider notifies an indexer that an object is ready for indexing, it generates a MAPI URL that uniquely identifies the object to the MAPI Protocol Handler. MAPI URLs are encoded in Unicode, and have the following format: 
  
`Mapi://SID/StoreDisplayName ($HashNumber)/StoreType/FolderNameA/…/FolderNameN/[EntryIDEncoded[/at=AttachIDEncoded:FileName]]`

The following sections describe the various parts of a typical URL.

|Part | Description|
|:----|:-----------|  
|*SID* |The current user's security identifier.| 
|*StoreDisplayName* |A string that specifies the display name of the user on that store.|
|*HashNumber* |A **DWORD** in hexadecimal representation that is calculated based on the store entry ID or the store mapping signature. This value is stored in the registry and will be used later to identify the store in the MAPI Protocol Handler.<br/><br/>This number must be calculated in a way that minimizes collisions with other stores. For the algorithm that Microsoft Outlook uses to calculate the hash number, see [Algorithm to Calculate the Store Hash Number](algorithm-to-calculate-the-store-hash-number.md).|
|*StoreType* |A number that identifies the type of the store that contains the object to be indexed. The possible values are as follows:<br/>- 0 - Default store.<br/><br/>- 1 - Delegate store, used for delegate items cached locally.<br/><br/>- 2 - Public folders, used for public folder favorites.<br/><br/>**NOTE**: If the store is being crawled instead of pushed, the value that is used is the character*X*.| 
|*FolderNameA/…/FolderNameN* |The path from the root of the IPM_SUBTREE to the folder or message. For example, a message in the **Family** folder under **Inbox** has **Inbox/Family** for this parameter. |
|*EntryIDEncoded* |MAPI entry ID for the item encoded as a Unicode string. See the following section "Special Characters" for information about how certain special characters are encoded. For more information about the algorithm to encode the entry ID, see [Algorithm to Encode Entry IDs and Attachment IDs](algorithm-to-encode-entry-ids-and-attachment-ids.md).<br/><br/>**NOTE**: When viewed as text, this encoded entry ID appears as random Hangul characters or boxes in compliance with the algorithm, depending on available fonts.  |
|*AttachIDEncoded* |Attachment ID encoded as a Unicode string. See the following section "Special Characters" for information about how certain special characters are encoded. For more information about the algorithm to encode the entry ID, see [Algorithm to Encode Entry IDs and Attachment IDs](algorithm-to-encode-entry-ids-and-attachment-ids.md).
<br/><br/>**NOTE**: When viewed as text, this encoded entry ID appears as random Hangul characters or boxes in compliance with the algorithm, depending on available fonts. |
|*FileName* |Name of the attachment file, as it appears in the message.|
    
## Examples of MAPI URLs

The following are some examples of MAPI URLs.
  
- MAPI URL for a folder: 
    
  `mapi://S-1-5-21-2127521184-1604012920-1887927527-71418/Mailbox - Some User ($be19928f)/2/Office`
    
- MAPI URL for a message: 
    
  `mapi://S-1-5-21-2127521184-1604012920-1887927527-71418/Mailbox - Some User ($484efb89)/0/Calendar/곯가가가걍걝걌곌겷걢곒갑겛개가검걟곔걙곾걤곂갠가`
    
- MAPI URL for an attachment: 
    
  `mapi://S-1-5-21-2127521184-1604012920-1887927527-71418/Mailbox - Some User ($484efb89)/0/Inbox/곯가가가걍걝걌곌겷걢곒갑겛개가검걟곔걙곾간곷갦가/at=겅걋각가:somefile.txt`
    
## Special characters

Certain characters are encoded if they appear in the message or attachment. The following shows which characters are encoded in a MAPI URL:
  
- % > %25
    
- / > %2F 
    
- \ > %5C 
    
- \* > %2A 
    
- ? > %3F 
    
## Blob associated with each MAPI URL

When pushing a MAPI URL for an object to be indexed, a store provider also creates a binary large object (BLOB) that contains certain information for the MAPI Protocol Handler. The store provider associates this BLOB with each MAPI URL and sends it when pushing the MAPI URL to the indexer. The format of the BLOB is as follows: 
  
```
DWORD  dwVersion
DWORD  dwFlags
ULONG  cbProfileName
WCHAR  wszProfileName
ULONG  cbProviderItemID
WCHAR  wszProviderItemID
```

The store provider must write these values to the BLOB in the order shown. The following table describes each field of the BLOB.

|Part | Description|
|:----|:-----------|  
|*dwVersion* |This is the version of the data being sent. Currently this value is 1.|
|*dwFlags* |Reserved for future use. Currently this value should be 0.|
|*cbProfileName* |The size of the profile name, in bytes. This information is useful for the MAPI Protocol Handler to know which profile to use when indexing the item.|
|*wszProfileName* |Null-terminated Unicode string that contains the profile name.|
|*cbProviderItemID* |Size of the provider item ID, in bytes. The store provider should send only the provider item ID for folders, to prevent opening additional folders to get this information.|
|*wszProviderItemID* |Null-terminated Unicode string with the provider item ID that uniquely identifies the item in the store.|
    
## See also

- [About Notification-Based Store Indexing](about-notification-based-store-indexing.md)
- [MAPI Constants](mapi-constants.md)

