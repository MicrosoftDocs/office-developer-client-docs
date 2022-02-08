---
title: "xlEventRegister"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: b98637d4-02e3-4dbd-8be5-6b46d32980c6

---

# xlEventRegister

 **Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Used to register an event handler. Introduced in Excel 2010.
  
```vb
Excel12(xlEventRegister, LPXLOPER12 pxRes, 2, LPXLOPER12 pxProcedure, LPXLOPER12 pxEvent);
```

## Parameters

 _pxProcedure_ (**xltypeStr**)
  
The name of the event handler function as it appears in the DLL code.
  
 _pxEvent_ (**xltypeInt**)
  
The event handled by the function designated in the _pxProcedure_ parameter. 
  
Starting in Excel 2010, Excel supports the following events:
  
|**Event**|**Description**|
|:-----|:-----|
|**xleventCalculationEnded** <br/> |Raised when Excel completes a calculation. You can free any resources allocated during the calculation after this event.  <br/> |
|**xleventCalculationCanceled** <br/> |Raised when the user interrupts the calculation. The XLL should stop any asynchronous activities. The CalculationEnded event is raised immediately following this event.  <br/> |
   
## Property value/Return value

If successful, pxRes (**xltypeInt**) has a value > 0. If unsuccessful, pxRes ==0.
  
## See also



[Asynchronous User-Defined Functions](asynchronous-user-defined-functions.md)

