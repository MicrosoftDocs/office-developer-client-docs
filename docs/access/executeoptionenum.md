---
title: "ExecuteOptionEnum"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: bd6d44a3-e471-7aa0-3e65-6775334de2ff

---

# ExecuteOptionEnum

Specifies how a provider should execute a command.
  
|**Constant**|**Value**|**Description**|
|:-----|:-----|:-----|
|**adAsyncExecute** <br/> |0x10  <br/> |Indicates that the command should execute asynchronously. This value cannot be combined with the [CommandTypeEnum](commandtypeenum.md) value **adCmdTableDirect**.  <br/> |
|**adAsyncFetch** <br/> |0x20  <br/> |Indicates that the remaining rows after the initial quantity specified in the [CacheSize](cachesize-property-ado.md) property should be retrieved asynchronously.  <br/> |
|**adAsyncFetchNonBlocking** <br/> |0x40  <br/> |Indicates that the main thread never blocks while retrieving. If the requested row has not been retrieved, the current row automatically moves to the end of the file. If you open a [Recordset](recordset-object-ado.md) from a [Stream](stream-object-ado.md) containing a persistently stored **Recordset**, **adAsyncFetchNonBlocking** will not have an effect; the operation will be synchronous and blocking. **adAsynchFetchNonBlocking** has no effect when the [adCmdTableDirect](commandtypeenum.md) option is used to open the **Recordset**.  <br/> |
|**adExecuteNoRecords** <br/> |0x80  <br/> |Indicates that the command text is a command or stored procedure that does not return rows (for example, a command that only inserts data). If any rows are retrieved, they are discarded and not returned. **adExecuteNoRecords** can only be passed as an optional parameter to the **Command** or **Connection** **Execute** method.  <br/> |
|**adExecuteStream** <br/> |0x400  <br/> |Indicates that the results of a command execution should be returned as a stream. **adExecuteStream** can only be passed as an optional parameter to the **Command** **Execute** method.  <br/> |
|**adExecuteRecord** <br/> |
  
 <br/> |Indicates that the **CommandText** is a command or stored procedure that returns a single row which should be returned as a **Record** object.  <br/> |
|**adOptionUnspecified** <br/> |-1  <br/> |Indicates that the command is unspecified.  <br/> |
   
 **ADO/WFC Equivalent**
  
Package: **com.ms.wfc.data**
  
|**Constant**|
|:-----|
|AdoEnums.ExecuteOption.ASYNCEXECUTE  <br/> |
|AdoEnums.ExecuteOption.ASYNCFETCH  <br/> |
|AdoEnums.ExecuteOption.ASYNCFETCHNONBLOCKING  <br/> |
|AdoEnums.ExecuteOption.NORECORDS  <br/> |
|AdoEnums.ExecuteOption.UNSPECIFIED  <br/> |
   

