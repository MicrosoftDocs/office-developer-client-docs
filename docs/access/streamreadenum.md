---
title: "StreamReadEnum"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 12432c0d-dc2e-10ea-13db-0c07b6ba29bc

---

# StreamReadEnum

Specifies whether the whole stream or the next line should be read from a [Stream](stream-object-ado.md) object. 
  
|**Constant**|**Value**|**Description**|
|:-----|:-----|:-----|
|**adReadAll** <br/> |-1  <br/> |Default. Reads all bytes from the stream, from the current position onwards to the [EOS](eos-property-ado.md) marker. This is the only valid **StreamReadEnum** value with binary streams ( [Type](type-property-ado-stream.md) is **adTypeBinary** ).  <br/> |
|**adReadLine** <br/> |-2  <br/> |Reads the next line from the stream (designated by the [LineSeparator](lineseparator-property-ado.md) property).  <br/> |
   
 **ADO/WFC Equivalent**
  
These constants do not have ADO/WFC equivalents.
  

