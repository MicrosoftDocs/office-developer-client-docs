---
title: "xlfGetName"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
keywords:
- xlfgetname 
ms.localizationpriority: medium
ms.assetid: 65780435-aaa2-47af-b44f-07be7aa769ee

---

# xlfGetName

**Applies to**: Excel 2013 | Office 2013 | Visual Studio
  
Returns the definition of a name as it appears in the **Refers to** column of the **Name Manager** dialog box, which is displayed when you click **Name Manager** in the **Defined Names** section on the **Formulas** tab. If the definition contains references, they are given as R1C1-style references. Use **xlfGetName** to check the value defined by a name. To get the name that corresponds to a definition, use [xlfGetDef](xlfgetdef.md).
  
```cpp
Excel12(xlfGetName, LPXLOPER12 pxRes, 2, LPXLOPER12 pxNameText, LPXLOPER12 pxInfoType);
```

## Parameters

_pxNameText_ (**xltypeStr**)
  
Can be a name defined on the sheet; an external reference to a name defined on the active workbook, for example, `"!Sales"`; or an external reference to a name defined on a particular open workbook, for example, `"[Book1]SHEET1!Sales"`.  _pxNameText_ can also be a hidden name.
  
_pxInfoType_ (**xltypeBool**)
  
Specifies the type of information to return about the name. If **FALSE** or omitted, the definition is returned. If **TRUE**, returns **TRUE** if the name is defined for just the sheet, **FALSE** if the name is defined for the entire workbook.
  
## Property value/Return value

_pxRes_ (**xltypeStr**, **xltypeBool**, or **xltypeErr**)
  
Depending on the value passed for  _pxInfoType_, returns the definition of the specified name (**xltypeStr**), or **TRUE** or **FALSE** (**xltypeBool**).
  
## Remarks

If the **Protect worksheet and contents of locked cells** check box has been selected in the **Protect Sheet** dialog box to protect the workbook containing the name, **xlfGetName** returns the  `#N/A` error value. To see the **Protect Sheet** dialog box, click **Protect Sheet** in the **Changes** section of the **Review** tab.
  
The following table lists three examples of the values returned by a call to **xlfGetDef** with the specified  _pxNameText_ argument.
  
|**Definition in Excel**|**_pxNameText_**|**Value Returned**|
|:-----|:-----|:-----|
|The name Sales on a sheet is defined as the number 523. |"Sales"  <br/> |"=523"  <br/> |
|The name Profit on the active sheet is defined as the formula =Sales-Costs. |"!Profit"  <br/> |"=Sales-Costs"  <br/> |
|The name Database on the active sheet is defined as the range A1:F500. |"!Database"  <br/> |"=R1C1:R500C6"  <br/> |

## See also

- [xlfGetDef](xlfgetdef.md)
- [Essential and Useful C API XLM Functions](essential-and-useful-c-api-xlm-functions.md)
