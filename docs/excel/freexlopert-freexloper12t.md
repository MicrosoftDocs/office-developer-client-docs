---
title: "FreeXLOperT/FreeXLOper12T"
 
 
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- FreeXLOper12T
- FreeXLOperT
keywords:
- freexlopert function [excel 2007],FreeXLOper12T function [Excel 2007]
 
ms.localizationpriority: medium
ms.assetid: 8fb3fdfd-8a43-4c50-82ff-e701fed3d83f

---

# FreeXLOperT/FreeXLOper12T

 **Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Framework function that frees memory associated with an **XLOPER**/ **XLOPER12**. The function assumes that the memory was allocated with calls to malloc within the DLL. If the memory was allocated by Microsoft Excel or in some other way or by some other process, this function should not be used to free the memory. Use [xlFree](xlfree.md) to free memory allocated by Excel for **XLOPER**/ **XLOPER12**s. 
  
```cs
void FreeXLOperT(LPXLOPER pxloper);
void FreeXLOper12T(LPXLOPER12 pxloper12);
```

## Parameters

 _pxloper_ (**LPXLOPER**)
  
 _pxloper12_ (**LPXLOPER12**)
  
Pointer to the **XLOPER**/ **XLOPER12** to be freed. 
  
## Example

 `\SAMPLES\FRAMEWRK\FRAMEWRK.C`
  
```cs
void FreeXLOper12T(LPXLOPER12 pxloper12)
{
   DWORD xltype;
   int cxloper12;
   LPXLOPER12 pxloper12Free;
   xltype = pxloper12->xltype;
   switch (xltype)
   {
   case xltypeStr:
      if (pxloper12->val.str != NULL)
         free(pxloper12->val.str);
      break;
   case xltypeRef:
      if (pxloper12->val.mref.lpmref != NULL)
         free(pxloper12->val.mref.lpmref);
      break;
   case xltypeMulti:
      cxloper12 = pxloper12->val.array.rows * pxloper12->val.array.columns;
      if (pxloper12->val.array.lparray)
      {
         pxloper12Free = pxloper12->val.array.lparray;
         while (cxloper12 > 0)
         {
            FreeXLOper12T(pxloper12Free);
            pxloper12Free++;
            cxloper12--;
         }
         free(pxloper12->val.array.lparray);
      }
      break;
   case xltypeBigData:
      if (pxloper12->val.bigdata.h.lpbData != NULL)
         free(pxloper12->val.bigdata.h.lpbData);
      break;
   }
}
```

## See also



[Functions in the Framework Library](functions-in-the-framework-library.md)

