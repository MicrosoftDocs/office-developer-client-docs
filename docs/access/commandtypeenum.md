---
title: "CommandTypeEnum"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 9ad8f155-88a0-00eb-2855-1e1a2a677437
---

# CommandTypeEnum

Specifies how a command argument should be interpreted.
  
|**Constant**|**Value**|**Description**|
|:-----|:-----|:-----|
|**adCmdUnspecified** <br/> |-1  <br/> |Does not specify the command type argument.  <br/> |
|**adCmdText** <br/> |1  <br/> |Evaluates [CommandText](commandtext-property-ado.md) as a textual definition of a command or stored procedure call.  <br/> |
|**adCmdTable** <br/> |2  <br/> |Evaluates **CommandText** as a table name whose columns are all returned by an internally generated SQL query.  <br/> |
|**adCmdStoredProc** <br/> |4  <br/> |Evaluates **CommandText** as a stored procedure name.  <br/> |
|**adCmdUnknown** <br/> |8  <br/> |Default. Indicates that the type of command in the **CommandText** property is not known.  <br/> |
|**adCmdFile** <br/> |256  <br/> |Evaluates **CommandText** as the file name of a persistently stored [Recordset](recordset-object-ado.md). Used with **Recordset.**[Open](open-method-ado-recordset.md) or [Requery](requery-method-ado.md) only.  <br/> |
|**adCmdTableDirect** <br/> |512  <br/> |Evaluates **CommandText** as a table name whose columns are all returned. Used with **Recordset.Open** or **Requery** only. To use the [Seek](seek-method-ado.md) method, the **Recordset** must be opened with **adCmdTableDirect**. This value cannot be combined with the [ExecuteOptionEnum](executeoptionenum.md) value **adAsyncExecute**.  <br/> |
   
 **ADO/WFC Equivalent**
  
Package: **com.ms.wfc.data**
  
|**Constant**|
|:-----|
|AdoEnums.CommandType.UNSPECIFIED  <br/> |
|AdoEnums.CommandType.TEXT  <br/> |
|AdoEnums.CommandType.TABLE  <br/> |
|AdoEnums.CommandType.STOREDPROC  <br/> |
|AdoEnums.CommandType.UNKNOWN  <br/> |
|AdoEnums.CommandType.FILE  <br/> |
|AdoEnums.CommandType.TABLEDIRECT  <br/> |
   

