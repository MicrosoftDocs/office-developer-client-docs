---
title: "SearchDirectionEnum"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: d491000b-47d0-bb28-95ed-7526dbb7c5e9

---

# SearchDirectionEnum

Specifies the direction of a record search within a [Recordset](recordset-object-ado.md).
  
|**Constant**|**Value**|**Description**|
|:-----|:-----|:-----|
|**adSearchBackward** <br/> |-1  <br/> |Searches backward, stopping at the beginning of the **Recordset**. If a match is not found, the record pointer is positioned at [BOF](bof-eof-properties-ado.md).  <br/> |
|**adSearchForward** <br/> |1  <br/> |Searches forward, stopping at the end of the **Recordset**. If a match is not found, the record pointer is positioned at [EOF](bof-eof-properties-ado.md).  <br/> |
   
 **ADO/WFC Equivalent**
  
Package: **com.ms.wfc.data**
  
|**Constant**|
|:-----|
|AdoEnums.SearchDirection.BACKWARD  <br/> |
|AdoEnums.SearchDirection.FORWARD  <br/> |
   

