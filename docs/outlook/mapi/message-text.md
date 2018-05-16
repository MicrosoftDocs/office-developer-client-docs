---
title: "Message Text"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 4d1837f1-494f-481b-9e09-ab8249f1488c
description: "Last modified: July 23, 2011"
 
 
---

# Message Text

  
  
**Applies to**: Outlook 
  
For outbound messages in MIME mode, the content-type depends on whether there are attachments and what the message text looks like. If there are attachments, the Content-type is  _multipart/mixed;_ the message text and each attachment become a separate part of the message content, each with its own content-type. If there are no attachments, the content-type of the message is  _text/plain_ and there is only one part. 
  
The message text is not line-wrapped unless some line exceeds 140 characters in length. If one does, the entire text is wrapped to 76 columns and the  _quoted-printable_ encoding is used to preserve line breaks. The content-type depends on what characters are found in the message text, as follows: 
  
- If only 7-bit characters are found and no line exceeds 140 characters in length, the message is ASCII text. _Content-type: text/plain; charset=us-ascii_ (Content-Transfer-Encoding=7bit is assumed.) 
    
- If long lines or 8-bit characters are found, the message is text and the character set is determined by the locale. It should be chosen from the character sets defined by ISO standard 8859. _Content-type: text/plain; charset=iso-8859-1_ (or another valid charset) 
    
     _Content-Transfer-Encoding: quoted-printable_
    
For inbound MIME messages, if the first message content part has  _Content-type: text/\*_ (that is, any text type) and its character set is recognized, it is mapped to **PR_BODY** ( [PidTagBody](pidtagbody-canonical-property.md)). A first message content part not meeting this criterion becomes an attachment. Any subsequent parts also become attachments.
  
In uuencode mode, message text in outbound messages is line-wrapped to 78 columns, as for MS Mail 3.x. The content-type is "text/plain." To preserve the original message's paragraph breaks under these circumstances, observe the following conventions in the wrapped text. There are three possible reasons for ending a line of text, each with its own character sequence:
  
- Line-break. The original text contained a newline entered by the user (paragraph mark). In the transport, this maps to a newline with no preceding blanks. If the user enters a newline preceded by blanks, the blanks should be stripped out.
    
- Line-nobreak. The original text contained a word too long to fit on a single line of the message. In the transport, this maps to a newline preceded by two blanks.
    
- Line-wrap. The original text contained no newline, the text is too long to fit on a single line of the message, but it can be broken between two words. In the transport, this maps to a newline preceded by a single blank.
    

