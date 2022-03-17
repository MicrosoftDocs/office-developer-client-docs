---
title: "DTPAGE"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.DTPAGE
api_type:
- COM
ms.assetid: 500f60ed-fdec-4d70-8cf5-664c46643956
description: "Last modified: March 09, 2015"
---

# DTPAGE

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Describes the dialog box that is built from a display table by the [BuildDisplayTable](builddisplaytable.md) function. 
  
|Key |Value |
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
   
```cpp
typedef struct DTPAGE
{
  ULONG cctl;
  LPSTR lpszResourceName;
  union
  {
    LPSTR lpszComponent;
    ULONG ulItemID;
  }
  LPDTCTL lpctl;
} DTPAGE, FAR *LPDTPAGE;

```

## Members

 **cctl**
  
> Count of controls pointed to by the **lpctl** member. 
    
 **lpszResourceName**
  
> Pointer to the name or integer identifier for the dialog box resource. 
    
 **lpszComponent**
  
> Pointer to the string that appears in the **[Help File Mappings]** section in MAPISVC.INF. Because **lpszComponent** is in a union with the **ulItemID** member, only one of these members has valid data. 
    
 **ulItemID**
  
> Integer resource identifier with a value less than or equal to 65535 from which the Help file name can be read. Because **ulItemID** is in a union with the **lpszComponent** member, only one of these members has valid data. 
    
 **lpctl**
  
> Pointer to an array of [DTCTL](dtctl.md) structures, one for each control on the page. 
    
## Remarks

To identify the Help file for the tabbed page, set either the **lpszComponent** member to a hard-coded string or the **ulItemID** member to an integer resource identifier. 
  
Each entry in the **[Help File Mappings]** section in MAPISVC.INF consists of a component string, no longer than 30 characters, on the left side and a Help file path on the right. Both **ulItemID** and **lpszResourceName** are found in the _hInstance_ parameter of **BuildDisplayTable**. For more information, see [MAPISVC.INF [Help File Mappings] Section](mapisvc-inf-help-file-mappings-section.md).
  
Although **BuildDisplayTable** uses this structure to build the display table from control resources, the **DTPAGE** structure never appears in the display table itself. 
  
For an overview of display tables, see [Display Tables](display-tables.md). For information about how to implement a display table, see [Implementing a Display Table](display-table-implementation.md).
  
## See also



[BuildDisplayTable](builddisplaytable.md)
  
[DTBLPAGE](dtblpage.md)
  
[DTCTL](dtctl.md)


[MAPI Structures](mapi-structures.md)

