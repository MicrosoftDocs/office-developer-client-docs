---
title: "PositionEnum"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 2a6f294b-74f2-b951-e32a-79ff5e782204

---

# PositionEnum

Specifies the current position of the record pointer within a [Recordset](recordset-object-ado.md).
  
|**Constant**|**Value**|**Description**|
|:-----|:-----|:-----|
|**adPosBOF** <br/> |-2  <br/> |Indicates that the current record pointer is at BOF (that is, the [BOF](bof-eof-properties-ado.md) property is **True** ).  <br/> |
|**adPosEOF** <br/> |-3  <br/> |Indicates that the current record pointer is at EOF (that is, the [EOF](bof-eof-properties-ado.md) property is **True** ).  <br/> |
|**adPosUnknown** <br/> |-1  <br/> |Indicates that the **Recordset** is empty, the current position is unknown, or the provider does not support the [AbsolutePage](absolutepage-property-ado.md) or [AbsolutePosition](absoluteposition-property-ado.md) property.  <br/> |
   
 **ADO/WFC Equivalent**
  
Package: **com.ms.wfc.data**
  
|**Constant**|
|:-----|
|AdoEnums.Position.BOF  <br/> |
|AdoEnums.Position.EOF  <br/> |
|AdoEnums.Position.UNKNOWN  <br/> |
   

