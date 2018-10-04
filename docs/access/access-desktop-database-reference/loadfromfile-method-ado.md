---
title: LoadFromFile Method (ADO)
TOCTitle: LoadFromFile Method (ADO)
ms:assetid: 33fd543f-bd24-9199-7540-2889b69221c8
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249107(v=office.15)
ms:contentKeyID: 48544123
ms.date: 09/18/2015
mtps_version: v=office.15
---

# LoadFromFile Method (ADO)


**Applies to**: Access 2013 | Office 2013

**In this article**  
Syntax  
Parameter  
Remarks  

Loads the contents of an existing file into a [Stream](stream-object-ado.md).

## Syntax

*Stream*.LoadFromFile *FileName*

## Parameter

  - *FileName*

  - A **String** value that contains the name of a file to be loaded into the **Stream**. *FileName* can contain any valid path and name in UNC format. If the specified file does not exist, a run-time error occurs.

## Remarks

This method may be used to load the contents of a local file into a **Stream** object. This may be used to upload the contents of a local file to a server.

The **Stream** object must be already open before calling **LoadFromFile**. This method does not change the binding of the **Stream** object; it will still be bound to the object specified by the URL or **Record** with which the **Stream** was originally opened.

**LoadFromFile** overwrites the current contents of the **Stream** object with data read from the file. Any existing bytes in the **Stream** are overwritten by the contents of the file. Any previously existing and remaining bytes following the [EOS](eos-property-ado.md) created by **LoadFromFile**, are truncated.

After a call to **LoadFromFile**, the current position is set to the beginning of the **Stream** ([Position](position-property-ado.md) is 0).

Because 2 bytes may be added to the beginning of the stream for encoding, the size of the stream may not exactly match the size of the file from which it was loaded.

