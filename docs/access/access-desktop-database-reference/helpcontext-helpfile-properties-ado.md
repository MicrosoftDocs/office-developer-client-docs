---
title: HelpContext, HelpFile Properties (ADO)
TOCTitle: HelpContext, HelpFile Properties (ADO)
ms:assetid: 8a79f994-f17c-2983-0593-095801be762e
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249608(v=office.15)
ms:contentKeyID: 48546194
ms.date: 09/18/2015
mtps_version: v=office.15
---

# HelpContext, HelpFile Properties (ADO)


**Applies to**: Access 2013 | Office 2013

Indicates the help file and topic associated with an [Error](error-object-ado.md) object.

## Return Values

  - **HelpContextID** — returns a context ID, as a **Long** value, for a topic in a Help file.

  - **HelpFile** — returns a **String** value that evaluates to a fully resolved path to a Help file.

## Remarks

If a Help file is specified in the **HelpFile** property, the **HelpContext** property is used to automatically display the Help topic it identifies. If there is no relevant help topic available, the **HelpContext** property returns zero and the **HelpFile** property returns a zero-length string ("").

