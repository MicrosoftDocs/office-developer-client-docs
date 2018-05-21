---
title: "xlAsyncReturn"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
localization_priority: Normal
ms.assetid: 159bc9bf-8dd5-4cd2-8384-474c74a3f112
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# xlAsyncReturn

**Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Used to return the result of an asynchronous user-defined function (UDF).
  
```cpp
Excel12(xlAsyncReturn, LPXLOPER12 pxRes, 2, LPXLOPER12 pxAsyncHandle, LPXLOPER12 pxFunctionResult);
```

## Parameters

_pxAsyncHandle_ ( **xltypeBigData**)
  
The asynchronous handle of the UDF to which the result is returned.
  
_pxFunctionResult_
  
The return value of the UDF.
  
## Property value/Return value

If successful, returns **TRUE** ( **xltypeBool**). If unsuccessful, returns **FALSE**.
  
## Remarks

**xlAsyncReturn** is the only callback Excel allows on non-calculation threads during recalculation. The asynchronous portion of an asynchronous UDF must not perform any callbacks other than **xlAsyncReturn**. The XLL must free memory allocated to hold the return value.
  
The _pxAsyncHandle_ and  _pxFunctionResult_ parameters can also be of type **xltypeMulti** when used to return an array of handles and corresponding values in a single callback. When using a single callback, pass an LPXLOPER12 that points to XLOPER12 structures that contain one dimensional arrays that contain the asynchronous handles and return values. These arrays must be in the same order for Excel to correctly match an asynchronous handle with its corresponding value. 
  
The following example shows how you can make a batch call using **xlAsyncReturn**.
  
```cpp
int batchSize = 10;
    LPXLOPER12 pHandles = new XLOPER12[batchSize];
    LPXLOPER12 pValues = new XLOPER12[batchSize];
    /*Add code to fill in LPXLOPER12 arrays (pHandles and pValues)
    with the XOPER12 structures that contain the asynchronous handles
    and values, in respective order*/
    //Create an XLOPER12 of type xltypeMulti, and fill the Handle array
    XLOPER12 handleArray;
    handleArray.xltype = xltypeMulti;
    handleArray.val.array.rows = 1;
    handleArray.val.array.columns = (COL)batchSize;
    handleArray.val.array.lparray = pHandles;
    
    //Create an XLOPER12 if type xltypeMulti, and fill the Values array
    XLOPER12 valueArray;
    valueArray.xltype = xltypeMulti;
    valueArray.val.array.rows = 1;
    valueArray.val.array.columns = (COL)batchSize;
    valueArray.val.array.lparray = pValues;
    //Make the callback with the return value
    int ret = Excel12(xlAsyncReturn, 0, 2, &amp;handleArray, &amp;valueArray);
    //Add code to free the allocated memory here (pHandles, pValues, valueArray, handleArray)
    return ret;

```

## See also

- [Asynchronous User-Defined Functions](asynchronous-user-defined-functions.md)

