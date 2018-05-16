---
title: "DTBLPAGE"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.DTBLPAGE
api_type:
- COM
ms.assetid: f899f434-a5d7-4b4f-98f9-c14c9f21b24b
description: "Last modified: March 09, 2015"
---

# DTBLPAGE

  
  
**Applies to**: Outlook 
  
Describes a tabbed page that will be used in a dialog box that is built from a display table. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Related macro:  <br/> |[SizedDtblPage](sizeddtblpage.md) <br/> |
   
```
typedef struct _DTBLPAGE
{
  ULONG ulbLpszLabel;
  ULONG ulFlags;
  ULONG ulbLpszComponent;
  ULONG ulContext;
} DTBLPAGE, FAR *LPDTBLPAGE;

```

## Members

 **ulbLpszLabel**
  
> Position in memory of the character string label for the page tab.
    
 **ulFlags**
  
> Bitmask of flags used to designate the format of the label pointed to by the **ulbLpszLabelName** member. The following flag can be set: 
    
MAPI_UNICODE 
  
> The label is in Unicode format. If the MAPI_UNICODE flag is not set, the label is in ANSI format.
    
 **ulbLpszComponent**
  
> Position in memory of a character string identifying the **[Help File Mappings]** section in the MAPISVC.INF configuration file or 0. The file name appearing in the MAPISVC.INF section can be used by a user to access extended Help for the tabbed page by clicking the **Help** button in the dialog box. For more information about the entries in MAPISVC.INF, see [File Format of MAPISVC.INF](file-format-of-mapisvc-inf.md).
    
 **ulContext**
  
> A unique identifier for the tabbed page in the string defined by the **ulbLpszComponent** member. The **ulbLpszComponent** member and the **ulContext** member must both be nonzero for the **Help** button to work. If this identifier is zero and the component string is NULL, there is no Help associated with the page. 
    
## Remarks

A **DTBLPAGE** structure describes a tabbed page a control that is used to separate several related dialog boxes. Typically, these dialog boxes are property sheets for displaying configuration, message, or recipient options. By clicking the tab, the user can switch from one sheet to another. 
  
The component string and context identifier provide information about whether extended Help is available for the tabbed page. If extended Help is available, the component string and context identifier will provide information about how to access it. The component string maps to the Help file; the context identifier maps to the initial Help topic. If the context identifier is zero and the component string is NULL, extended Help is not available.
  
For an overview of display tables, see [Display Tables](display-tables.md). For information about how to implement a display table, see [Implementing a Display Table](display-table-implementation.md).
  
## See also

#### Reference

[DTCTL](dtctl.md)
#### Concepts

[MAPI Structures](mapi-structures.md)

