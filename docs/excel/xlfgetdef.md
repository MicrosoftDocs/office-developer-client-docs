---
title: "xlfGetDef"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
keywords:
- xlfgetdef
ms.localizationpriority: medium
ms.assetid: 68f5edbd-9040-46d3-acd5-dd51ca82f6fa

---

# xlfGetDef

**Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Returns the name, as text, that is defined for a particular area, value, or formula in a workbook. In Excel, this value is displayed in the **Name** column of the **Name Manager** dialog box, which is displayed when you click **Name Manager** in the **Defined Names** section on the **Formulas** tab. Use **xlfGetDef** to get the name that corresponds to a definition. To get the definition of a name, use [xlfGetName](xlfgetname.md).
  
```cpp
Excel12(xlfGetDef, LPXLOPER12 pxRes, 3, LPXLOPER12 pxDefText, LPXLOPER12 pxDocumentText, LPXLOPER12 pxTypeNum);
```

## Parameters

_pxDefText_ (**xltypeStr**)
  
Can be anything you can define a name to refer to, including a reference, a value, an object, or a formula.
  
References must be given in R1C1 style, such as  `"R3C5"`. If  _pxDefText_ is a value or formula, it is not necessary to include the equal sign that is displayed in the **Refers To** column in the **Name Manager** dialog box. If there is more than one name for  _pxDefText_, **xlfGetDef** returns the first name. If no name matches  _pxDefText_, **xlfGetDef** returns the  `#NAME?` error value. 
  
_pxDocumentText_ (**xltypeStr**)
  
Specifies the sheet that  _pxDefText_ is on. If  _pxDocumentText_ is omitted, it is assumed to be the active sheet. 
  
_pxTypeNum_ (**xltypeNum**)
  
A number from 1 to 3 specifying which types of names are returned.
  
|**_pxTypeNum_**|**Returns**|
|:-----|:-----|
|1 or omitted  <br/> |Normal names only. |
|2  <br/> |Hidden names only. |
|3  <br/> |All names. |
   
## Property value/Return value

 _pxRes_ (**xltypeStr** or **xltypeErr**)
  
Returns the name associated with the specified definition.
  
## Remarks

The following table lists four examples of the values returned by a call to **xlfGetDef** with the specified arguments. 
  
|**Name defined in Excel**|**_pxDefText_**|**_pxDocumentText_**|**_pxTypeNum_**|**Value Returned**|
|:-----|:-----|:-----|:-----|:-----|
|The specified range in Sheet4 is named Sales. |"R2C2:R9C6"  <br/> |"Sheet4"  <br/> |\<omitted\>  <br/> |"Sales"  <br/> |
|The value 100 in Sheet4 is defined as Constant. |"100"  <br/> |"Sheet4"  <br/> |\<omitted\>  <br/> |"Constant"  <br/> |
|The specified formula in Sheet4 is named SumTotal. |"SUM(R1C1:R10C1)"  <br/> |"Sheet4"  <br/> |\<omitted\>  <br/> |"SumTotal"  <br/> |
|3 is defined as the hidden name Counter on the active sheet. |"3"  <br/> |\<omitted\>  <br/> |2  <br/> |"Counter"  <br/> |
   
## See also

- [xlfGetName](xlfgetname.md)
- [Essential and Useful C API XLM Functions](essential-and-useful-c-api-xlm-functions.md)

