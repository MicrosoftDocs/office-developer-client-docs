---
title: Handling Errors in Visual C++
TOCTitle: Handling Errors in Visual C++
ms:assetid: 75e15699-0c84-1dca-654e-f9ac465c2a30
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ249483(v=office.15)
ms:contentKeyID: 48545684
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Handling Errors in Visual C++


_**Applies to:** Access 2013 | Office 2013_

In COM, most operations return an HRESULT return code that indicates whether a function completed successfully. The \#import directive generates wrapper code around each "raw" method or property and checks the returned HRESULT. If the HRESULT indicates failure, the wrapper code throws a COM error by calling \_com\_issue\_errorex() with the HRESULT return code as an argument. COM error objects can be caught in a **try-catch** block. (For efficiency's sake, catch a reference to a \_com\_error object.)

Remember, these are ADO errors: they result from the ADO operation failing. Errors returned by the underlying provider appear as **Error** objects in the **Connection** object's **Errors** collection.

The \#import directive only creates error-handling routines for methods and properties declared in the ADO .dll. However, you can take advantage of this same error-handling mechanism by writing your own error-checking macro or inline function. See the topic Visual C++ Extensions for examples.

