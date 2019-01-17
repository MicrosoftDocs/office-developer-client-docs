---
title: MinimizeWindow macro action
TOCTitle: MinimizeWindow macro action
ms:assetid: 3a92b654-15ce-1ed1-63e0-eed927dbe26c
ms:mtpsurl: https://msdn.microsoft.com/library/Ff192648(v=office.15)
ms:contentKeyID: 48544265
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- vbaac10.chm174420
f1_categories:
- Office.Version=v15
localization_priority: Normal
---

# MinimizeWindow macro action

**Applies to**: Access 2013, Office 2013

If Access is configured to use overlapping windows instead of tabbed documents, you can use the **MinimizeWindow** action to reduce the active window to a small title bar at the bottom of the Access window.

> [!NOTE]
> This action can't be applied to code windows in the Visual Basic Editor. For information about how to affect code windows, see the **WindowState** property topic.

## Setting

The **MinimizeWindow** action doesn't have any arguments.

## Remarks

You can use this action to remove a window from the screen while leaving the object open. You can also use this action to open an object without displaying its window. To display the object, use the **SelectObject** action with either the **MaximizeWindow** or **RestoreWindow** action. The **RestoreWindow** action restores a minimized window to its previous size.

The **MinimizeWindow** action has the same effect as clicking the **Minimize** button in the window's upper-right corner or clicking **Minimize** on the window's **Control** menu.

**Tips**

- You may first need to use the **SelectObject** action if the window you want to minimize isn't the active window.

- To hide the Navigation Pane, use the **SelectObject** action with the In Navigation Pane argument set to **Yes** and then use the **MinimizeWindow** action. The object you select in the **SelectObject** action can be any object in the database.

- You can hide the active window by clicking **Manage This Window** on the **View** menu, and then clicking **Hide**. Instead of being reduced to an icon, the window becomes invisible. Use the **Unhide** command on the same menu to make the window reappear. You can use the **RunMenuCommand** action to carry out either of these commands from a macro.

- You can also use the **SetValue** action to set a form's **Visible** property to hide or show the form's window.

To run the **MinimizeWindow** action in a Visual Basic for Applications (VBA) module, use the **Minimize** method of the **DoCmd** object.

