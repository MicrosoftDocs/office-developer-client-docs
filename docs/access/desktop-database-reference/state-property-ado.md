---
title: State property (ADO)
TOCTitle: State property (ADO)
ms:assetid: ade0a50c-e2d8-23ac-4ea9-b012fedcd5db
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249819(v=office.15)
ms:contentKeyID: 48547053
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- ado210.chm1231176
f1_categories:
- Office.Version=v15
ms.localizationpriority: medium
---

# State property (ADO)


**Applies to**: Access 2013, Office 2013

Indicates for all applicable objects whether the state of the object is open or closed.

Indicates for all applicable objects executing an asynchronous method, whether the current state of the object is connecting, executing, or retrieving.

## Return value

Returns a **Long** value that can be an [ObjectStateEnum](objectstateenum.md) value. The default value is **adStateClosed**.

## Remarks

You can use the **State** property to determine the current state of a given object at any time.

The object's **State** property can have a combination of values. For example, if a statement is executing, this property will have a combined value of **adStateOpen** and **adStateExecuting**.

The **State** property is read-only.

