---
title: "Type Property (ADO Stream)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 43872c74-51bf-47ae-6bdc-55d25b0dc84a

---

# Type Property (ADO Stream)

Indicates the type of data contained in the [Stream](stream-object-ado.md) (binary or text). 
  
## Settings and Return Values

Sets or returns a [StreamTypeEnum](streamtypeenum.md) value that specifies the type of data contained in the **Stream** object. The default value is **adTypeText**. However, if binary data is initially written to a new, empty **Stream**, the **Type** will be changed to **adTypeBinary**. 
  
## Remarks

The **Type** property is read/write only when the current position is at the beginning of the **Stream** ( [Position](position-property-ado.md) is 0), and read-only at any other position. 
  
The **Type** property determines which methods should be used for reading and writing the **Stream**. For text **Streams**, use [ReadText](readtext-method-ado.md) and [WriteText](writetext-method-ado.md). For binary **Streams**, use [Read](read-method-ado.md) and [Write](write-method-ado.md).
  

