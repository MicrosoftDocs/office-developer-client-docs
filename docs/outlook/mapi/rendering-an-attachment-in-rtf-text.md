---
title: "Rendering an Attachment in RTF Text"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 26372539-e9fe-464d-95c7-90b58c20b98f
description: "Last modified: July 23, 2011" 
 
---

# Rendering an Attachment in RTF Text

**Applies to**: Outlook 2013 | Outlook 2016
  
Rich Text Format (RTF)-aware clients can retrieve rendering position information from RTF message text by looking for the following escape sequence in the message's **PR_RTF_COMPRESSED** ([PidTagRtfCompressed](pidtagrtfcompressed-canonical-property.md)) property:
  
 `\objattph`
  
 **To locate rendering information in formatted text**
  
1. Call **IMessage::GetAttachmentTable** to access the message's attachment table. For more information, see [IMessage::GetAttachmentTable](imessage-getattachmenttable.md).

2. Build a property restriction that limits the table to rows that have **PR_RENDERING_POSITION** not equal to -1. For more information, see **PR_RENDERING_POSITION** ([PidTagRenderingPosition](pidtagrenderingposition-canonical-property.md)).

3. Call **IMAPITable::Restrict** to enforce the restriction. For more information, see [IMAPITable::Restrict](imapitable-restrict.md).

4. Call **IMAPITable::SortTable** to sort the attachments. For more information, see [IMAPITable::SortTable](imapitable-sorttable.md).

5. Call **IMAPITable::QueryRows** to retrieve the appropriate rows. For more information, see [IMAPITable::QueryRows](imapitable-queryrows.md).

6. Call the message's **IMAPIProp::OpenProperty** method to retrieve **PR_RTF_COMPRESSED** with the **IStream** interface. For more information, see [IMAPIProp::OpenProperty](imapiprop-openproperty.md) and **PR_RTF_COMPRESSED**.

7. Scan the stream, looking for the rendering placeholder, `\objattph`. The character following this placeholder is the place for the next attachment in the sorted table.
