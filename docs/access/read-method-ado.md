---
title: "Read Method (ADO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 91c3ad34-f891-5be0-1fc1-c5c8a2ff07a4

---

# Read Method (ADO)

Reads a specified number of bytes from a binary [Stream](stream-object-ado.md) object. 
  
## Syntax

 *Variant*  =  *Stream*  . **Read** (  *NumBytes*  ) 
  
## Parameters

-  *NumBytes* 
    
- Optional. A **Long** value that specifies the number of bytes to read from the file or the [StreamReadEnum](streamreadenum.md) value **adReadAll**, which is the default. 
    
## Return Value

The **Read** method reads a specified number of bytes or the entire stream from a **Stream** object and returns the resulting data as a **Variant**. 
  
## Remarks

If  *NumBytes*  is more than the number of bytes left in the **Stream**, only the bytes remaining are returned. The data read is not padded to match the length specified by  *NumBytes*  . If there are no bytes left to read, a variant with a null value is returned. **Read** cannot be used to read backwards. 
  
> [!NOTE]
>  *NumBytes*  always measures bytes. For text **Stream** objects ( [Type](type-property-ado-stream.md) is **adTypeText** ), use [ReadText](readtext-method-ado.md). 
  

