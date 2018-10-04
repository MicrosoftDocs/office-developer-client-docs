---
title: CloseDatabase Macro Action
TOCTitle: CloseDatabase Macro Action
ms:assetid: c4b4278d-932c-99f6-da2d-8953109b44b3
ms:mtpsurl: https://msdn.microsoft.com/library/Ff823085(v=office.15)
ms:contentKeyID: 48547598
ms.date: 09/18/2015
mtps_version: v=office.15
---

# CloseDatabase Macro Action


**Applies to**: Access 2013 | Office 2013

You can use the **CloseDatabase** action to close the current database.

## Setting

The **CloseDatabase** action does not have any arguments.

## Remarks

  - Access will not run any actions that follow the **CloseDatabase** action in a macro.

  - This action has the same effect as clicking the **File** tab and then clicking **Close Database**. If there are any unsaved objects open when you run the **CloseDatabase** action, the dialog boxes that appear are the same as those displayed when you click **Close Database**.

  - To run the **CloseDatabase** action in a Visual Basic for Applications (VBA) module, use the **CloseDatabase** method of the **DoCmd** object.

