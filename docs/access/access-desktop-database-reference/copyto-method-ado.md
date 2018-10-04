﻿---
title: CopyTo Method (ADO)
TOCTitle: CopyTo Method (ADO)
ms:assetid: 1c1ab950-51f7-7ecc-ccd8-e689db02f06a
ms:mtpsurl: https://msdn.microsoft.com/library/JJ248958(v=office.15)
ms:contentKeyID: 48543558
ms.date: 09/18/2015
mtps_version: v=office.15
---

# CopyTo Method (ADO)


**Applies to**: Access 2013 | Office 2013

**In this article**  
Syntax  
Parameters  
Remarks  

Copies the specified number of characters or bytes (depending on [Type](type-property-ado-stream.md)) in the [Stream](stream-object-ado.md) to another **Stream** object.

## Syntax

*Stream*.CopyTo *DestStream*, *NumChars*

## Parameters

  - *DestStream*

  - An object variable value that contains a reference to an open **Stream** object. The current **Stream** is copied to the destination **Stream** specified by *DestStream*. The destination **Stream** must already be open. If not, a run-time error occurs.
    

    > [!NOTE]
    > <P>The <EM>DestStream</EM> parameter may not be a proxy of <STRONG>Stream</STRONG> object because this requires access to a private interface on the <STRONG>Stream</STRONG> object that cannot be remoted to the client.</P>



  - *NumChars*

  - Optional. An **Integer** value that specifies the number of bytes or characters to be copied from the current position in the source **Stream** to the destination **Stream**. The default value is –1, which specifies that all characters or bytes are copied from the current position to [EOS](eos-property-ado.md).

## Remarks

This method copies the specified number of characters or bytes, starting from the current position specified by the [Position](position-property-ado.md) property. If the specified number is more than the available number of bytes until **EOS**, then only characters or bytes from the current position to **EOS** are copied. If the value of *NumChars* is –1, or omitted, all characters or bytes starting from the current position are copied.

If there are existing characters or bytes in the destination stream, all contents beyond the point where the copy ends remain, and are not truncated. **Position** becomes the byte immediately following the last byte copied. If you want to truncate these bytes, call [SetEOS](seteos-method-ado.md).

**CopyTo** should be used to copy data to a destination **Stream** of the same type as the source **Stream** (their **Type** property settings are both **adTypeText** or both **adTypeBinary**). For text **Stream** objects, you can change the [Charset](charset-property-ado.md) property setting of the destination **Stream** to translate from one character set to another. Also, text **Stream** objects can be successfully copied into binary **Stream** objects, but binary **Stream** objects cannot be copied into text **Stream** objects.

