---
title: "StreamWriteEnum"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: b4356999-d7a8-abfa-f6a8-6c2dd04b9257

---

# StreamWriteEnum

Specifies whether a line separator is appended to the string written to a [Stream](stream-object-ado.md) object. 
  
|**Constant**|**Value**|**Description**|
|:-----|:-----|:-----|
|**adWriteChar** <br/> |0  <br/> |Default. Writes the specified text string (specified by the  *Data*  parameter) to the **Stream** object.  <br/> |
|**adWriteLine** <br/> |1  <br/> |Writes a text string and a line separator character to a **Stream** object. If the [LineSeparator](lineseparator-property-ado.md) property is not defined, then this returns a run-time error.  <br/> |
   
 **ADO/WFC Equivalent**
  
These constants do not have ADO/WFC equivalents.
  

