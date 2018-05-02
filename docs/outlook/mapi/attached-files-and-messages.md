---
title: "Attached Files and Messages"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: b2f2fb72-23ae-4e0b-a8a1-3b78a1862acb
description: "Last modified: July 23, 2011"
 
 
---

# Attached Files and Messages

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
If MIME with TNEF is used while encoding message content,all attachment properties and content are in the TNEF stream. The TNEF itself is a single, binary attached file named Winmail.dat, encoded as described for MIME without TNEF. 
  
If MIME is used without TNEF, attached files are sent as MIME message content parts. The filename is placed in the  *name*  parameter to the  *Content-type*  header for the attachment. The character set for the attachment is placed in the  *charset*  parameter to the  *Content-type*  ; it and the content-transfer-encoding are determined by scanning the entire attachment content. URL attachments are treated specially: 
  
- If the attachment is a URL (an attached file with extension .URL), and the access mode defined in it is anonymous FTP, it is encoded as an external message, and the content of the file (the URL) is copied into the header of the external message. *Content-type: message/external-body; access-type=anon-ftp*  (Content-Transfer-Encoding: 7bit is assumed.) 
    
- If only 7-bit characters are found and no line exceeds 140 characters in length, the attachment is ASCII text. *Content-type: text/plain; charset=us-ascii Content-Transfer-Encoding: 7bit* 
    
- If long lines or up to 25% 8-bit characters are found, the attachment content is text and the character set is determined by the locale. It should be chosen from the character sets defined by ISO standard 8859. *Content-type: text/plain; charset=ISO-8859-1*  (for example) 
    
     *Content-Transfer-Encoding: quoted-printable* 
    
- If 25% or more of the characters have the high bit set, the attachment is binary. It is encoded using the Base64 algorithm. *Content-type: application/octet-stream*  (by default; based on file extension) 
    
     * Content-Transfer-Encoding: base64 * 
    
On outbound messages, the content-type should be derived from the filename's three-letter extension. This mapping exists in the system registry; under there is a string value named "Content Type" that gives the MIME content type if one is defined. This example is for a TIFF image file:
  
HKEY_LOCAL_MACHINE\
  
Software\
  
Microsoft\
  
Classes\
  
.tif
  
Content Type = "image/tiff"
  
If there is no mapping for the file extension, the default  *application/octet*  stream should be used. 
  
On inbound messages, the content-type for an attachment should always be copied to the MAPI property **PR_ATTACH_MIME_TAG** ( [PidTagAttachMimeTag](pidtagattachmimetag-canonical-property.md)). Even if a filename is defined for an attached file, the extension mapped by the content-type should be used in the **PR_ATTACH_FILENAME** ( [PidTagAttachFilename](pidtagattachfilename-canonical-property.md)) and **PR_ATTACH_EXTENSION** ( [PidTagAttachExtension](pidtagattachextension-canonical-property.md)) properties.
  
The  *name*  parameter is officially deprecated by RFC 821. As standards evolve, Microsoft will consider specifying an alternate mapping for attached filenames. 
  
Outbound attached messages are sent as * Content-type: message/rfc822 *  Messages within attached messages are encoded recursively, in their proper place. Inbound message content parts with  *Content-Type: multipart/digest*  are also mapped to embedded messages. 
  
If uuencode with TNEF is used while encoding message content, all attachment properties and content are in the TNEF stream. The TNEF itself is a single, binary attached file named Winmail.dat, encoded as described for Uuencode without TNEF.
  
If uuencode is used without TNEF, all attached files are treated as binary and uuencoded, following the message text. The file name is present in the uuencode header:
  
 begin 0755 Winmail.dat 
  
 ... data ... 
  
 end 
  
Attached messages are textized into the message text. The hierarchy of attached messages is always flattened; that is, messages within attached messages are pulled out to the top level.
  
Embedded OLE objects are discarded.
  
Attachment rendering positions are transmitted literally, using the property **PR_ATTACH_RENDERING** ( [PidTagAttachRendering](pidtagattachrendering-canonical-property.md)) in the TNEF. If TNEF is not used, they are lost. Incoming attachments with no rendering position (including when there is no TNEF) have their rendering position set to 0xFFFFFFFF, that is, no position in the message text.
  
## See also

#### Concepts

[Mapping of Internet Mail Attributes to MAPI Properties](mapping-of-internet-mail-attributes-to-mapi-properties.md)

