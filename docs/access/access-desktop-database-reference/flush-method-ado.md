---
title: Flush Method (ADO)
TOCTitle: Flush Method (ADO)
ms:assetid: c167e3b1-c133-ce45-6cee-5a1280a1568f
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ249941(v=office.15)
ms:contentKeyID: 48547529
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Flush Method (ADO)


_**Applies to:** Access 2013 | Office 2013_

Forces the contents of the [Stream](stream-object-ado.md) remaining in the ADO buffer to the underlying object with which the **Stream** is associated.

## Syntax

*Stream*.Flush

## Remarks

This method may be used to send the contents of the stream buffer to the underlying object (for example, the node or file represented by the URL that is the source of the **Stream** object). This method should be called when you want to ensure that all changes made to the contents of a **Stream** have been written. However, with ADO it is not usually necessary to call **Flush**, as ADO continuously flushes its buffer as much as possible in the background. Changes to the content of a **Stream** are made automatically, not cached until **Flush** is called.

Closing a **Stream** with the [Close](close-method-ado.md) method flushes the contents of a **Stream** automatically; there is no need to explicitly call **Flush** immediately before **Close**.

