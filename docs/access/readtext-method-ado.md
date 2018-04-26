---
title: "ReadText Method (ADO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 08f5bac4-dccd-696c-09a7-e1ba0cb38d79

---

# ReadText Method (ADO)

Reads specified number of characters from a text [Stream](stream-object-ado.md) object. 
  
## Syntax

 *String*  =  *Stream*  . **ReadText** (  *NumChars*  ) 
  
## Parameters

-  *NumChars* 
    
- Optional. A **Long** value that specifies the number of characters to read from the file, or a [StreamReadEnum](streamreadenum.md) value. The default value is **adReadAll**. 
    
## Return Value

The **ReadText** method reads a specified number of characters, an entire line, or the entire stream from a **Stream** object and returns the resulting string. 
  
## Remarks

If  *NumChar*  is more than the number of characters left in the stream, only the characters remaining are returned. The string read is not padded to match the length specified by  *NumChar*  . If there are no characters left to read, a variant whose value is null is returned. **ReadText** cannot be used to read backwards. 
  
> [!NOTE]
> The **ReadText** method is used with text streams ( [Type](type-property-ado-stream.md) is **adTypeText** ). For binary streams ( **Type** is **adTypeBinary** ), use [Read](read-method-ado.md). 
  

