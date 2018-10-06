---
title: onError Event (RDS)
TOCTitle: onError Event (RDS)
ms:assetid: e26a3f7f-0f00-919a-65ad-bf39ffb83e92
ms:mtpsurl: https://msdn.microsoft.com/library/JJ250153(v=office.15)
ms:contentKeyID: 48548292
ms.date: 09/18/2015
mtps_version: v=office.15
---

# onError Event (RDS)


**Applies to**: Access 2013 | Office 2013

The **onError** event is called whenever an error occurs during an operation.

## Syntax

onError*SCode*, *Description*, *Source*, *CancelDisplay*

## Parameters

  - *SCode*

  - An integer that indicates the status code of the error.

  - *Description*

  - A **String** that indicates a description of the error.

  - *Source*

  - A **String** that indicates the query or command that caused the error.

  - *CancelDisplay*

  - A **Boolean** value, which if set to **True**, that prevents the error from being displayed in a dialog box.

