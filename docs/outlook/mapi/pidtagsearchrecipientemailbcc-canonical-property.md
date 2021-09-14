---
title: "PidTagSearchRecipientEmailBcc Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
ms.assetid: d9561d13-8d52-500c-5369-15a2cf5c92c3
description: "Last modified: March 09, 2015"
---

# PidTagSearchRecipientEmailBcc Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains a Unicode string that is being queried in the list of email addresses or display names of recipients addressed in the **BCC** line of unsent messages on the store. 
  
## 

|||
|:-----|:-----|
|Associated properties:  <br/> |PR_SEARCH_RECIP_EMAIL_BCC_W  <br/> |
|Identifier:  <br/> |0x0EA8  <br/> |
|Property type:  <br/> |PT_UNICODE  <br/> |
|Access:  <br/> |Search  <br/> |
   
## Remarks

This property is only relevant to messages on the store that have not been sent, because messages that have been sent or received do not contain BCC information.
  
> [!NOTE]
> This MAPI restriction tag, used when searching for email addresses or display names to which the message will be sent as a blind carbon copy, might not be defined in the downloadable header file that you currently have. You can add it to your code by using the following value: >  `#define PR_SEARCH_RECIP_EMAIL_BCC_W PROP_TAG(PT_UNICODE, 0x0EA8)`
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Microsoft Exchange Server protocol specifications.
    
[[MS-OXOSRCH]](https://msdn.microsoft.com/library/c72e49b8-78c7-4483-ad65-e46e9133673b%28Office.15%29.aspx)
  
> Specifies the properties and operations for manipulating a search folder list configuration.
    
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

