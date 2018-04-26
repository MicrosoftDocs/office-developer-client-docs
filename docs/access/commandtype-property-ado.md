---
title: "CommandType Property (ADO)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
f1_keywords:
- ado210.chm1231125
  
localization_priority: Normal
ms.assetid: c8d4fc1c-502b-11f3-af9d-605a03b6f056
---

# CommandType Property (ADO)

Indicates the type of a [Command](command-object-ado.md) object. 
  
## Settings and Return Values

Sets or returns one or more [CommandTypeEnum](commandtypeenum.md) values. 
  
> [!NOTE]
> Do not use the **CommandTypeEnum** values of **adCmdFile** or **adCmdTableDirect** with **CommandType**. These values can only be used as options with the [Open](open-method-ado-recordset.md) and [Requery](requery-method-ado.md) methods of a [Recordset](recordset-object-ado.md). 
  
## Remarks

Use the **CommandType** property to optimize evaluation of the [CommandText](commandtext-property-ado.md) property. 
  
If the **CommandType** property value equals **adCmdUnknown** (the default value), you may experience diminished performance because ADO must make calls to the provider to determine if the **CommandText** property is an SQL statement, a stored procedure, or a table name. If you know what type of command you're using, setting the **CommandType** property instructs ADO to go directly to the relevant code. If the **CommandType** property does not match the type of command in the **CommandText** property, an error occurs when you call the [Execute](http://msdn.microsoft.com/library/01812c8c-403e-4428-23f6-86bda747bd0e%28Office.15%29.aspx) method. 
  

