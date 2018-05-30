---
title: "DTCTL"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.DTCTL
api_type:
- COM
ms.assetid: 6d1589e9-b171-427a-9a3e-b4154ee8ceb6
description: "Last modified: March 09, 2015"
---

# DTCTL

**Applies to**: Outlook 
  
Describes a control that will be used in a dialog box built from a display table. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
   
```cpp
typedef struct
{
  ULONG ulCtlType;
  ULONG ulCtlFlags;
  LPBYTE lpbNotif;
  ULONG cbNotif;
  LPSTR lpszFilter;
  ULONG ulItemID;
  union
  {
    LPVOID lpv;
    LPDTBLLABEL lplabel;
    LPDTBLEDIT lpedit;
    LPDTBLLBX lplbx;
    LPDTBLCOMBOBOX lpcombobox;
    LPDTBLDDLBX lpddlbx;
    LPDTBLCHECKBOX lpcheckbox;
    LPDTBLGROUPBOX lpgroupbox;
    LPDTBLBUTTON lpbutton;
    LPDTBLRADIOBUTTON lpradiobutton;
    LPDTBLMVLISTBOX lpmvlbx;
    LPDTBLMVDDLBX lpmvddlbx;
    LPDTBLPAGE lppage;
  } ctl;
} DTCTL, FAR *LPDTCTL;

```

## Members

**ulCtlType**
  
> Type of control that is included in the **ctl** member and corresponds to the control's **PR_CONTROL_TYPE** ([PidTagControlType](pidtagcontroltype-canonical-property.md)) property. Possible values are as follows:
    
DTCT_LABEL 
  
> Label control.
    
DTCT_EDIT 
  
> Edit control.
    
DTCT_LBX 
  
> List box control.
    
DTCT_COMBOBOX 
  
> Combo box control.
    
DTCT_DDLBX 
  
> Drop-down list control.
    
DTCT_CHECKBOX 
  
> Check box control.
    
DTCT_GROUPBOX 
  
> Group box control.
    
DTCT_BUTTON 
  
> Button control.
    
DTCT_PAGE 
  
> Tabbed page control.
    
DTCT_RADIOBUTTON 
  
> Radio button control.
    
DTCT_MVLISTBOX 
  
> Multi-valued list control.
    
DTCT_MVDDLBX 
  
> Multi-valued drop-down list control.
    
**ulCtlFlags**
  
> Bitmask of flags that describes the control's features and corresponds to the control's **PR_CONTROL_FLAGS** ([PidTagControlFlags](pidtagcontrolflags-canonical-property.md)) property. These flags can be set for check boxes, combo boxes, list boxes, and edit controls only. Possible values are as follows:
    
DT_ACCEPT_DBCS 
  
> Either the ANSI or DBCS format is accepted. This flag is valid for edit controls only.
    
DT_EDITABLE 
  
> A user can modify the text in the control. 
    
DT_MULTILINE 
  
> The control can contain multiple text lines. This flag is valid for edit controls only.
    
DT_PASSWORD_EDIT 
  
> The control contains a password; therefore, the contents of the control should not be displayed to the user. This flag is valid for edit controls only.
    
DT_REQUIRED 
  
> The dialog box control is required. This flag is valid only for edit and combo box controls.
    
DT_SET_IMMEDIATE 
  
> Enables immediate output of a value upon a change in the control. This allows a dependency relationship to be established between two controls. 
    
**lpbNotif**
  
> Pointer to a structure that consists of a [GUID](guid.md) structure, to represent the service provider and an identifier for the control. The **lpbNotif** and **cbNotif** members correspond to the control's **PR_CONTROL_ID** ([PidTagControlId](pidtagcontrolid-canonical-property.md)) property and are used to notify the user interface when the control has to be updated.
    
**cbNotif**
  
> Count of bytes in the structure pointed to by the **lpbNotif** member. 
    
**lpszFilter**
  
> Pointer to a character string that describes which characters can be entered into an edit or combo box control. For other types of controls, the **lpszFilter** member can be NULL. For edit and combo box controls, it should be a regular expression that applies to a single character at a time. The same filter is applied to all characters in the control. The format of the filter string is as follows: 
    
|**Character**|**Description**|
|:-----|:-----|
| `*` <br/> | Any character is allowed (for example, `"*"`).  <br/> |
| `[ ]` <br/> |Defines a set of characters (for example, `"[0123456789]"`.)  <br/> |
| `-` <br/> |Indicates a range of characters (for example, `"[a-z]"`).  <br/> |
| `~` <br/> |Indicates that these characters are not allowed (for example, `"[~0-9]")`. <br/>|   
| `\` <br/> |Used to quote any of the previous symbols (for example, `"[\-\\\[\]]"` means -, \, [, and ] characters are allowed).  <br/> |
   
**ulItemID**
  
> Value that identifies the control in the dialog box resource. For tabbed pages controls of type DTCT_PAGE the **ulItemID** member is optionally used to load the component name for the page from a string resource. Position and label information are read from the dialog box resource. 
    
**ctl**
  
> A structure that holds the data for the control and corresponds to the control's **PR_CONTROL_STRUCTURE** ([PidTagControlStructure](pidtagcontrolstructure-canonical-property.md)) property. Each type of control has a different structure.
    
## Remarks

The **DTCTL** structure describes one control of any type. Most of its members are used to set properties on the control. 
  
The **ctl** member is a union of structures that relate to a particular type of control. If the **DTCTL** structure is describing an edit control, for example, the **ctl** member will point to a [DTBLEDIT](dtbledit.md) structure. This structure corresponds to the control's **PR_CONTROL_STRUCTURE** property. The union has as its first member a variable of type LPVOID to allow compile time initialization of the **DTCTL** structure. 
  
Although the [BuildDisplayTable](builddisplaytable.md) function uses the **DTCTL** structure for building the display table from control resources, the **DTCTL** structure never appears in the display table itself. This structure just supplies information to **BuildDisplayTable**.
  
In the **ulCtlFlags** member, four flags DT_ACCEPT_DBCS, DT_EDITABLE, DT_MULTILINE_and DT_PASSWORD_EDIT affect edit controls only. Two others DT_REQUIRED and DT_SET_IMMEDIATE affect any editable control. 
  
The controls available for a dialog box are label, text box, ink-aware text box, list, drop-down list, combo box, check box, group box, button, radio button, and tabbed page.
  
For an overview of display tables, see [Display Tables](display-tables.md). For information about how to implement a display table, see [Implementing a Display Table](display-table-implementation.md).
  
## See also

- [BuildDisplayTable](builddisplaytable.md)
- [DTBLBUTTON](dtblbutton.md)
- [DTBLCHECKBOX](dtblcheckbox.md)
- [DTBLCOMBOBOX](dtblcombobox.md)
- [DTBLDDLBX](dtblddlbx.md)
- [DTBLEDIT](dtbledit.md)
- [DTBLGROUPBOX](dtblgroupbox.md)
- [DTBLLABEL](dtbllabel.md)
- [DTBLLBX](dtbllbx.md)
- [DTBLMVDDLBOX](dtblmvddlbox.md)
- [DTBLMVLISTBOX](dtblmvlistbox.md)
- [DTBLPAGE](dtblpage.md)
- [DTBLRADIOBUTTON](dtblradiobutton.md)
- [MAPI Structures](mapi-structures.md)

