---
title: RestoreWindow macro action
TOCTitle: RestoreWindow macro action
ms:assetid: 507a6452-2be0-a523-1201-0108d2b9d23c
ms:mtpsurl: https://msdn.microsoft.com/library/Ff193815(v=office.15)
ms:contentKeyID: 48544796
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- vbaac10.chm11103
f1_categories:
- Office.Version=v15
---

# RestoreWindow macro action

**Applies to**: Access 2013, Office 2013

You can use the **RestoreWindow** action to restore a maximized or minimized window to its previous size.

> [!NOTE]
> This action can't be applied to code windows in the Visual Basic Editor. For information about how to affect code windows, see the **WindowState** property topic.

## Setting

The **RestoreWindow** action doesn't have any arguments.

## Remarks

This action works on the selected object. If an object has been minimized, you can first select it by using the **SelectObject** action and then restore it to its previous size by using the **RestoreWindow** action.

You can use the **MoveAndSizeWindow** action to move or size a window that you have restored.

The **RestoreWindow** action has the same effect as clicking the **Restore** button in the window's upper-right corner or clicking the **Restore** command on the window's **Control** menu.

To run the **RestoreWindow** action in a Visual Basic for Applications (VBA) module, use the **Restore** method of the **DoCmd** object.

