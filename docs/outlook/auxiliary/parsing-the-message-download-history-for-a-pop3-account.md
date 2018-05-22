---
title: "Parsing the message download history for a POP3 account"
 
 
manager: soliver
ms.date: 9/17/2015
ms.audience: Developer
ms.topic: overview
 
localization_priority: Normal
ms.assetid: 394e1430-04d6-4d61-be13-eb695309fa73
description: "This topic describes the structure of the POP3 BLOB that represents the message download history of a POP3 account, to identify the messages that have been downloaded or deleted on that account."
---

# Parsing the message download history for a POP3 account

This topic describes the structure of the POP3 BLOB that represents the message download history of a POP3 account, to identify the messages that have been downloaded or deleted on that account.
  
## Why parse the message download history?
<a name="OL15Con_AuxRef_ParsingMsgsHistory_WhyParseHistory"> </a>

The Post Office Protocol (POP) provider for Outlook allows users to retrieve and download new email messages on their local device, and subsequently to leave or delete these email messages on the mail server. When the mail client checks for new messages to download, it has to be able to identify and download only the new messages for that Inbox. The mail client does this by first using the UIDL (Unique ID Listing) command to obtain a map of each message that has ever been delivered to that Inbox to a unique identifier (UID). The client also gets the message download history for messages that have been downloaded or deleted for the Inbox on that client. Using the message UID map and download history, the client can then identify those messages that are absent from the history as new and, hence, should be downloaded.
  
To get the messages download history for an Inbox:
  
- Follow the steps in [Locating the message download history for a POP3 account](locating-the-message-download-history-for-a-pop3-account.md) to find the [PidTagAttachDataBinary](http://msdn.microsoft.com/library/3b0a8b28-863e-4b96-a4c0-fdb8f40555b9%28Office.15%29.aspx) property, which contains a binary large object (BLOB) that represents the message history for a POP3 account. 
    
- Read this topic, which describes the structure of the BLOB, and shows an example BLOB to identify messages that have been downloaded or deleted for the Inbox of the POP3 account.
    
## POP BLOB structure
<a name="OL15Con_AuxRef_ParsingMsgsHistory_BLOBStructure"> </a>

The POP BLOB structure, as described in Table 1, begins with two fields, **Version** and **Count**, followed by a **Count** number of resource tags, each of which is null-terminated. 
  
**Table 1. Structure of the BLOB that represents the message download history of a POP3 account**

|**Field in BLOB**|**Size**|**Description**|
|:-----|:-----|:-----|
|**Version** <br/> |2 bytes  <br/> |Must be 3 (**PBLOB_VERSION_NUM**).  <br/> |
|**Count** <br/> |2 bytes  <br/> |The number of resource tags in this BLOB.  <br/> |
|Resource tag  <br/> |Variable  <br/> |0 or more null-terminated UTF-8 strings that encode the resource tags. The number of null-terminated strings must match **Count**.  <br/> |
   
Each resource tag specifies the operation that is applied to a message, some date-time metadata about the operation, and encodes the UID of the message. The format of a resource tag string is broken down as follows, and is further explained in Table 2. 
  
 `Ocyyyymmddhhmmssuuu...`
  
**Table 2. Structure of a resource tag**

|**Field in a resource tag**|**Size**|**Description**|
|:-----|:-----|:-----|
| `O` <br/> |1 character  <br/> |The operation performed on the email message. The value must be "+", "-", or "&amp;", which indicates a successful get, delete, or get-and-delete operation, respectively.  <br/> |
| `c` <br/> |1 character  <br/> |The part of the message content involved in the operation. The value must be " ", "h", or "b", which indicates the content of none, header, or body, respectively.  <br/> |
| `yyyy` <br/> |4 characters  <br/> |The four-digit year of the operation.  <br/> |
| `MM` <br/> |2 characters  <br/> |The two-digit month of the operation.  <br/> |
| `dd` <br/> |2 characters  <br/> |The two-digit day of the operation.  <br/> |
| `hh` <br/> |2 characters  <br/> |The two-digit hour of the operation.  <br/> |
| `mm` <br/> |2 characters  <br/> |The two-digit minute of the operation.  <br/> |
| `ss` <br/> |2 characters  <br/> |The two-digit second of the operation.  <br/> |
| `uuu…` <br/> |Variable length  <br/> |The encoded UID of a message.  <br/> |
   
## Example
<a name="OL15Con_AuxRef_ParsingMsgsHistory_Example"> </a>

Figure 1 shows an example of a BLOB that represents the message download history of a POP account. 
  
**Figure 1. Example BLOB structure for the message download history of a POP3 account**

![BLOB for messages download history of POP3 account](media/OL15Con_AuxRef_ParsingMsgsHistory_Blob.gif)
  
Based on the structure described in Table 1 and Table 2, this BLOB represents the download history of 23 email messages.
  
To parse the raw UID in each resource tag, be aware that the UID follows this encoding: characters in a UID are mostly alphanumeric characters, and each non-alphanumeric character is preceded by the ASCII character "$" (0x24). So the ASCII characters $2d represent the non-alphanumeric character "-". Figure 2 shows an example of first converting the raw UID in resource tag 1 to the ASCII representation, then converting any non-alphanumeric character preceded by "$" to produce the actual UID:
  
 `0BC535DB-EA63-11E1-A75C-00215AD7BB74`
  
**Figure 2. Converting the raw UID in a resource tag to the actual message UID**

![Converting raw UID in BLOB to actual message UID](media/OL15Con_AuxRef_ParsingMsgsHistory_BlobRscTag.gif)
  
To interpret resource tag 1 in this BLOB: the message with the UID  `0BC535DB-EA63-11E1-A75C-00215AD7BB74` was successfully retrieved on September 6, 2012, at 13:11:38. 
  
You can similarly parse the remaining 22 resource tags for that BLOB.
  
## See also
<a name="OL15Con_AuxRef_ParsingMsgsHistory_AdditionalRsc"> </a>

- [Managing message downloads for POP3 accounts](managing-message-downloads-for-pop3-accounts.md)
    
- [Locating the message download history for a POP3 account](locating-the-message-download-history-for-a-pop3-account.md)
    
- [Parsing the POP3 UIDL History](http://blogs.msdn.com/b/stephen_griffin/archive/2012/12/04/parsing-the-pop3-uidl-history.aspx)
    

