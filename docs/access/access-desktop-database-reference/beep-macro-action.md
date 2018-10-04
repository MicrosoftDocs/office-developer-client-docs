---
title: Beep Macro Action
TOCTitle: Beep Macro Action
ms:assetid: 5ca1600f-7934-3b3d-19fd-f305cda0e5d8
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff194572(v=office.15)
ms:contentKeyID: 48545092
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- vbaac10.chm11853
f1_categories:
- Office.Version=v15
---

# Beep Macro Action


**Applies to**: Access 2013 | Office 2013

You can use the **Beep** action to sound a beep tone through the computer's speaker.

## Setting

The **Beep** action doesn't have any arguments.

## Remarks

You can use the **Beep** action to signal the following occurrences:

  - Important screen changes have occurred.

  - The wrong kind of data has been entered in a control. For example, the user has entered numeric data in a text box control.

  - A macro has reached a specified point or has completed its actions.

The frequency and duration of the beep depend on the hardware, which may vary between computers.

To run the **Beep** action in a Visual Basic for Applications (VBA) module, use the **Beep** method of the **DoCmd** object.

