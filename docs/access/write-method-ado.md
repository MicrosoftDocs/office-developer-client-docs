---
title: "Write Method (ADO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: cabe4581-409f-7f05-bd59-d495bfb2c6fd

---

# Write Method (ADO)

Writes binary data to a [Stream](stream-object-ado.md) object. 
  
## Syntax

 *Stream*  . **Write** *Buffer* 
  
## Parameters

-  *Buffer* 
    
- A **Variant** that contains an array of bytes to be written. 
    
## Remarks

Specified bytes are written to the **Stream** object without any intervening spaces between each byte. 
  
The current [Position](position-property-ado.md) is set to the byte following the written data. The **Write** method does not truncate the rest of the data in a stream. If you want to truncate these bytes, call [SetEOS](seteos-method-ado.md).
  
If you write past the current [EOS](eos-property-ado.md) position, the [Size](http://msdn.microsoft.com/library/deb84313-36d1-fa49-e4cd-daecab96f343%28Office.15%29.aspx) of the **Stream** will be increased to contain any new bytes, and **EOS** will move to the new last byte in the **Stream**. 
  
> [!NOTE]
> The **Write** method is used with binary streams ( [Type](type-property-ado-stream.md) is **adTypeBinary** ). For text streams ( **Type** is **adTypeText** ), use [WriteText](writetext-method-ado.md). 
  

