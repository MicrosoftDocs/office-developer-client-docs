---
title: "Cancel Method (ADO)"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
f1_keywords:
- ado210.chm1231032
  
localization_priority: Normal
ms.assetid: 747edc04-a5cc-3631-2d0b-82e7e41a76b7
---

# Cancel Method (ADO)

Cancels execution of a pending, asynchronous method call.
  
## Syntax

 *object*  . **Cancel**
  
## Remarks

Use the **Cancel** method to terminate execution of an asynchronous method call (that is, a method invoked with the **adAsyncConnect**, **adAsyncExecute**, or **adAsyncFetch** option). 
  
The following table shows what task is terminated when you use the **Cancel** method on a particular type of object. 
  
|**         If  *object*  is a**|**The last asynchronous call to this method is terminated**|
|:-----|:-----|
|[Command](command-object-ado.md) <br/> |[Execute](http://msdn.microsoft.com/library/01812c8c-403e-4428-23f6-86bda747bd0e%28Office.15%29.aspx) <br/> |
|[Connection](connection-object-ado.md) <br/> |[Execute](http://msdn.microsoft.com/library/af190bd9-7167-df59-29ca-a9a86c4957fd%28Office.15%29.aspx) or [Open](open-method-ado-connection.md) <br/> |
|[Record](record-object-ado.md) <br/> |[CopyRecord](copyrecord-method-ado.md), [DeleteRecord](deleterecord-method-ado.md), [MoveRecord](moverecord-method-ado.md), or [Open](open-method-ado-record.md) <br/> |
|[Recordset](recordset-object-ado.md) <br/> |[Open](open-method-ado-recordset.md) <br/> |
|[Stream](stream-object-ado.md) <br/> |[Open](open-method-ado-stream.md) <br/> |
   

