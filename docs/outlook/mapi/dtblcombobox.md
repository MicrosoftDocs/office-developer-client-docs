---
title: "DTBLCOMBOBOX" 
manager: lindalu
ms.date: 02/09/2022
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.DTBLCOMBOBOX
api_type:
- COM
ms.assetid: 73b68614-6aca-4669-b879-5631c5d6483c
description: "Describes a combo box control that will be used in a dialog box built from a display table."
---

# DTBLCOMBOBOX
  
**Applies to**: Outlook 2013 | Outlook 2016
  
Describes a combo box control that will be used in a dialog box built from a display table.
  
|||
|:-----|:-----|
|Header file:  |Mapidefs.h |
|Related macro: [SizedDtblComboBox](sizeddtblcombobox.md) |

```cpp
typedef struct _DTBLCOMBOBOX
{
  ULONG ulbLpszCharsAllowed;
  ULONG ulFlags;
  ULONG ulNumCharsAllowed;
  ULONG ulPRPropertyName;
  ULONG ulPRTableName;
} DTBLCOMBOBOX, FAR *LPDTBLCOMBOBOX;

```

## Members

**ulbLpszCharsAllowed**
  
> An offset from the start of the **DTBLCOMBOBOX** structure to a character string filter that describes restrictions, if any, to the characters that can be entered into the combo box's edit control. The filter is not interpreted as a regular expression and the same filter is applied to every character entered. The format of the filter is as follows:

|**Character**|**Description**|
|:-----|:-----|
| `*`  |Any character is allowed (for example, `"*"`). |
| `[ ]`|Defines a set of characters (for example, `"[0123456789]"`). |
| `-`  |Indicates a range of characters (for example, `"[a-z]"`). |
| `~`  |Indicates that these characters are not allowed. (for example, `"[~0-9]"`). |
| `\`  |Used to quote any of the previous symbols (for example, `"[\-\\\[\]]"` means -, \, [, and ] characters are allowed). |

**ulFlags**
  
> Bitmask of flags used to designate the format of the character string filter. The following flag can be set:

MAPI_UNICODE
  
> The filter is in Unicode format. If the MAPI_UNICODE flag is not set, the filter is in ANSI format.

**ulNumCharsAllowed**
  
> Maximum number of characters that can be entered in the combo box's text box.

**ulPRPropertyName**
  
> Property tag for a property of type PT_TSTRING.

**ulPRTableName**
  
> Property tag for a property of type PT_OBJECT on which an **IMAPITable** interface can be opened by using an **OpenProperty** call. The table must have one column with a property that is the same type as the property identified by the **ulPRPropertyName** member. The rows of the table are used to populate the list.

## Remarks

A **DTBLCOMBOBOX** structure describes a combo box a control that consists of a list and a selection field. The list presents the information from which a user can select, and the selection field displays the current selection. The selection field is an edit control that can also be used to enter text not already in the list.
  
The two property tag members work together to coordinate the list display with the edit control. When MAPI first displays the combo box, it calls the **OpenProperty** method of the **IMAPIProp** implementation that is associated with the display table to retrieve the table represented by the **ulPRTableName** member. This table has one column a column that contains values for the property represented by the **ulPRPropertyName** member. Therefore, this column must be of the same type as the **ulPRPropertyName** property and both columns must be character strings.
  
The values for the column are displayed in the list section of the combo box. Therefore, **PR_NULL** ([PidTagNull](pidtagnull-canonical-property.md)) is not a valid property tag for **ulPRPropertyName**. When a user either selects one of the rows or enters new data into the text box, the **ulPRPropertyName** property is set to the selected or entered value.
  
To display an initial value for the edit control, MAPI calls [IMAPIProp::GetProps](imapiprop-getprops.md) to retrieve the property values for the display table. If one of the retrieved properties matches the property represented by the **ulPRPropertyName** member, its value becomes the initial value.
  
For an overview of display tables, see [Display Tables](display-tables.md). For information about how to implement a display table, see [Implementing a Display Table](display-table-implementation.md).
  
## See also

[DTCTL](dtctl.md)  
[PidTagControlType Canonical Property](pidtagcontroltype-canonical-property.md)
[MAPI Structures](mapi-structures.md)
