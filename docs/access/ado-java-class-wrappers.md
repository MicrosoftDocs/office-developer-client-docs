---
title: "ADO Java Class Wrappers"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: de50faf0-80f3-f295-3d9e-3f70f86c3ede
description: "This code declares an instance of the ADO Recordset class wrapper and initializes it, all on the same line of code. Further, it declares variables for each of the arguments in the Open method, especially for LockType and CursorType (because Java doesn't support enumerated types). It opens and closes the Recordset object. Setting Rs1 to NULL merely schedules that variable to be released when Java performs its systematic and intermittent release of unused objects."
---

# ADO Java Class Wrappers

This code declares an instance of the ADO [Recordset](recordset-object-ado.md) class wrapper and initializes it, all on the same line of code. Further, it declares variables for each of the arguments in the [Open](open-method-ado-recordset.md) method, especially for [LockType](locktype-property-ado.md) and [CursorType](cursortype-property-ado.md) (because Java doesn't support enumerated types). It opens and closes the **Recordset** object. Setting Rs1 to NULL merely schedules that variable to be released when Java performs its systematic and intermittent release of unused objects. 
  
```
 
public static void main( String args[]) 
{ 
 msado15._Recordset Rs1 = new msado15.Recordset(); 
 Variant Source = new Variant( "SELECT * FROM Authors" ); 
 Variant Connect = new Variant( "DSN=AdoDemo;UID=admin;PWD=;" ); 
 int LockType = msado15.CursorTypeEnum.adOpenForwardOnly; 
 int CursorType = msado15.LockTypeEnum.adLockReadOnly; 
 int Options = -1; 
 
 Rs1.Open( Source, Connect, LockType, CursorType, Options ); 
 Rs1.Close(); 
 Rs1 = null; 
 
 System.out.println( "Success!\n" ); 
} 

```


