---
title: "Visual C++ Extensions for ADO"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 38048ae0-1dae-9e5e-c569-04011df8b5aa
description: "The preferred method of programming ADO with Visual C++ is using the #import directive, as discussed in Microsoft Visual C++ ADO Programming. However, earlier versions of ADO shipped with an alternate method of programming using Visual C++: the Visual C++ Extensions. This section documents this feature for those who must maintain Visual C++ Extensions code, but new ADO code should be written using #import ."
---

# Visual C++ Extensions for ADO

The preferred method of programming ADO with Visual C++ is using the **#import** directive, as discussed in [Microsoft Visual C++ ADO Programming](visual-c-plus-plus-ado-programming.md). However, earlier versions of ADO shipped with an alternate method of programming using Visual C++: the Visual C++ Extensions. This section documents this feature for those who must maintain Visual C++ Extensions code, but new ADO code should be written using # **import**. 
  
One of the most tedious jobs Visual C++ programmers face when retrieving data with ADO is converting data returned as a VARIANT data type into a C++ data type, and then storing the converted data in a class or structure. In addition to being cumbersome, retrieving C++ data through a VARIANT data type diminishes performance.
  
ADO provides an interface that supports retrieving data into native C/C++ data types without going through a VARIANT, and also provides preprocessor macros that simplify using the interface. The result is a flexible tool that is easier to use and has great performance.
  
A common C/C++ client scenario is to bind a record in a [Recordset](recordset-object-ado.md) to a C/C++ struct or class containing native C/C++ types. When going through VARIANTs, this involves writing conversion code from VARIANT to C/C++ native types. The Visual C++ Extensions for ADO are targeted at making this scenario much easier for the Visual C++ programmer. 
  
See the following topics to learn more about the Visual C++ Extensions for ADO.
  
- [Using Visual C++ Extensions for ADO](using-visual-c-plus-plus-extensions.md)
    
- [Visual C++ Extensions Header](visual-c-plus-plus-extensions-header.md)
    
- [ADO with Visual C++ Extensions Example](visual-c-plus-plus-extensions-example.md)
    

