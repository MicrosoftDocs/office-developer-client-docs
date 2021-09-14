---
title: Write method - ActiveX Data Objects (ADO)
TOCTitle: Write method (ADO)
ms:assetid: cabe4581-409f-7f05-bd59-d495bfb2c6fd
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249986(v=office.15)
ms:contentKeyID: 48547697
ms.date: 09/18/2015
mtps_version: v=office.15
ms.localizationpriority: medium
---

# Write method (ADO)

**Applies to**: Access 2013, Office 2013

Writes binary data to a [Stream](stream-object-ado.md) object.

## Syntax

*Stream*.Write*Buffer*

## Parameters

|Parameter|Description|
|:--------|:----------|
|*Buffer* |A **Variant** that contains an array of bytes to be written.|

## Remarks

Specified bytes are written to the **Stream** object without any intervening spaces between each byte.

The current [Position](position-property-ado.md) is set to the byte following the written data. The **Write** method does not truncate the rest of the data in a stream. If you want to truncate these bytes, call [SetEOS](seteos-method-ado.md).

If you write past the current [EOS](eos-property-ado.md) position, the [Size](https://docs.microsoft.com/office/vba/access/concepts/miscellaneous/size-property-ado-stream) of the **Stream** will be increased to contain any new bytes, and **EOS** will move to the new last byte in the **Stream**.

> [!NOTE]
> The **Write** method is used with binary streams ([Type](type-property-ado-stream.md) is **adTypeBinary**). For text streams (**Type** is **adTypeText**), use [WriteText](writetext-method-ado.md).

