---
title: "DTBLEDIT"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.DTBLEDIT
api_type:
- COM
ms.assetid: ec3566a0-75ad-466d-a61e-f7d61ccb946d
description: "Last modified: March 09, 2015"
---

# DTBLEDIT

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Describes an edit control that will be used in a dialog box built from a display table.
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Related macro:  <br/> |[SizedDtblEdit](sizeddtbledit.md) <br/> |
   
```
typedef struct _DTBLEDIT
{
  ULONG ulbLpszCharsAllowed;
  ULONG ulFlags;
  ULONG ulNumCharsAllowed;
  ULONG ulPropTag;
} DTBLEDIT, FAR *LPDTBLEDIT;

```

## Members

 **ulbLpszCharsAllowed**
  
> An offset from the start of the **DTBLEDIT** structure to a character string filter that describes restrictions, if any, to the characters that can be entered into the edit control. The filter is not interpreted as a regular expression and the same filter is applied to every character entered. The format of the filter is as follows: 
    
|**Character**|**Description**|
|:-----|:-----|
| `*` <br/> |Any character is allowed (for example,  `"*"`).  <br/> |
| `[ ]` <br/> |Defines a set of characters (for example,  `"[0123456789]".`)  <br/> |
| `-` <br/> |Indicates a range of characters (for example,  `"[a-z]"`).  <br/> |
| `~` <br/> |Indicates that these characters are not allowed (for example,  `"[~0-9]"`).  <br/> |
| `\` <br/> |Used to quote any of the previous symbols (for example,  `"[\-\\\[\]]"` means -, \, [, and ] characters are allowed).  <br/> |
   
 **ulFlags**
  
> Bitmask of flags used to designate the format of the character filter. The following flag can be set:
    
MAPI_UNICODE
  
> The filter is in Unicode format. If the MAPI_UNICODE flag is not set, the filter is in ANSI format.
    
 **ulNumCharsAllowed**
  
> Maximum number of characters that the user can type into the text box.
    
 **ulPropTag**
  
> Property tag for a property of type PT_TSTRING. The **ulPropTag** member identifies the string property whose data is displayed and edited in the edit control. 
    
## Remarks

A **DTBLEDIT** structure describes an edit control an area on a dialog box that contains alphanumeric information. Almost all dialog boxes have at least one edit control. Edit controls can be modifiable by a user or read-only. 
  
Edit controls can also be single line or multiline. Multiline edit controls typically have a scroll bar associated with them. 
  
For an overview of display tables, see [Display Tables](display-tables.md). For information about how to implement a display table, see [Implementing a Display Table](display-table-implementation.md).
  
## See also

#### Reference

[DTCTL](dtctl.md)
  
[IMAPIProp::GetProps](imapiprop-getprops.md)
  
[PidTagControlType Canonical Property](pidtagcontroltype-canonical-property.md)
#### Concepts

[MAPI Structures](mapi-structures.md)

