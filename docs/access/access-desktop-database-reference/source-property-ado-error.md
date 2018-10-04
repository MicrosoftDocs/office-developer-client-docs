---
title: Source Property (ADO Error)
TOCTitle: Source Property (ADO Error)
ms:assetid: ffc6c77f-1494-d63a-d832-416faa4c6f07
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ250316(v=office.15)
ms:contentKeyID: 48548969
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Source Property (ADO Error)


**Applies to**: Access 2013 | Office 2013

Indicates the name of the object or application that originally generated an error.

## Return Value

Returns a **String** value that indicates the name of an object or application.

## Remarks

Use the **Source** property on an [Error](error-object-ado.md) object to determine the name of the object or application that originally generated an error. This could be the object's class name or programmatic ID. For errors in ADO, the property value will be **ADODB.***ObjectName*, where *ObjectName* is the name of the object that triggered the error. For ADOX and ADO MD, the value will be **ADOX.***ObjectName* and **ADOMD.***ObjectName,* respectively.

Based on the error documentation from the **Source**, [Number](number-property-ado.md), and [Description](description-property-ado.md) properties of **Error** objects, you can write code that will handle the error appropriately.

The **Source** property is read-only for **Error** objects.

