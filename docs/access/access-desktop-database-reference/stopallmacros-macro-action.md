---
title: StopAllMacros Macro Action
TOCTitle: StopAllMacros Macro Action
ms:assetid: 6afbf906-03b8-6e68-bbc9-7a4b141cf1c5
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff195440(v=office.15)
ms:contentKeyID: 48545442
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- vbaac10.chm104968
f1_categories:
- Office.Version=v15
---

# StopAllMacros Macro Action


**Applies to**: Access 2013 | Office 2013

You can use the **StopAllMacros** action to stop all macros that are currently running.

## Setting

The **StopAllMacros** action doesn't have any arguments.

## Remarks

You typically use this action when an error condition makes it necessary to stop all macros. You can use a conditional expression in the macro's action row that contains this action. When the expression evaluates to **True** (–1), Microsoft Access stops all macros.

For example, you might have a macro that displays a message box as one of a number of complex actions, including running other macros. If the user clicks **Cancel** in this message box, the **StopAllMacros** action can stop all the macros that are running.

If a macro has used the **Echo** or **SetWarnings** actions to turn echo or the display of system messages off, the **StopAllMacros** action automatically turns them back on.

This action isn't available in a Visual Basic for Applications (VBA) module.

