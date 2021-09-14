---
title: "SMAPIVerb"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.SMAPIVerb
api_type:
- COM
ms.assetid: 45066528-2447-4178-aaa3-7513ed0b3ba4
description: "Last modified: March 09, 2015"
---

# SMAPIVerb

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Describes a MAPI verb.
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiform.h  <br/> |
   
```cpp
typedef struct
{
  ULONG lVerb;
  LPSTR szVerbname;
  DWORD fuFlags;
  DWORD grfAttribs;
  ULONG ulFlags; /* Either 0 or MAPI_UNICODE */
} SMAPIVerb, FAR * LPMAPIVERB;

```

## Members

 **lVerb**
  
> Code representing the verb that is passed to [IMAPIForm::DoVerb](imapiform-doverb.md). Standard verbs are defined in the header file Exchform.h.
    
 **szVerbname**
  
> Display name of the verb as it appears on the form menu.
    
 **fuFlags**
  
> Flags for the verb.
    
 **grfAttribs**
  
> Attributes of the verb. 
    
 **ulFlags**
  
> Flag indicating the format of the verb's display name. The following flag can be set:
    
MAPI_UNICODE 
  
> The display name is in Unicode format. If the MAPI_UNICODE flag is not set, the display name is in ANSI format.
    
## Remarks

The **SMAPIVerb** structure is passed as a parameter in the following methods: 
  
- [IMAPIFormContainer::ResolveMultipleMessageClasses](imapiformcontainer-resolvemultiplemessageclasses.md)
    
- [IMAPIFormMgr::ResolveMultipleMessageClasses](imapiformmgr-resolvemultiplemessageclasses.md)
    
## See also



[CbMessageClassArray](cbmessageclassarray.md)


[MAPI Structures](mapi-structures.md)

