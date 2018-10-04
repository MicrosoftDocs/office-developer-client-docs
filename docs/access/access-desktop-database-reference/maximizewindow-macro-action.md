﻿---
title: MaximizeWindow Macro Action
TOCTitle: MaximizeWindow Macro Action
ms:assetid: 79c9e430-07a7-02b2-ff5a-c6b9ec32c5b6
ms:mtpsurl: https://msdn.microsoft.com/library/Ff196171(v=office.15)
ms:contentKeyID: 48545778
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- vbaac10.chm196948
f1_categories:
- Office.Version=v15
---

# MaximizeWindow Macro Action


**Applies to**: Access 2013 | Office 2013

If Access is configured to use overlapping windows instead of tabbed documents, you can use the **MaximizeWindow** action to enlarge the active window so that it fills the Access window. This action will allow you to see as much of the object in the active window as possible.


> [!NOTE]
> <P>This action can't be applied to code windows in the Visual Basic Editor. For information about how to affect code windows, see the <STRONG>WindowState</STRONG> property topic.</P>



## Setting

The **MaximizeWindow** action doesn't have any arguments.

## Remarks

This action has the same effect as clicking the **Maximize** button in the window's upper-right corner or clicking **Maximize** on the window's **Control** menu.

You can use the **RestoreWindow** action to restore a maximized window to its previous size.

**Tips**

  - You may need to use the **SelectObject** action if the window you want to maximize isn't the active window.

  - When you maximize a window in Access, all other windows are also maximized when you open them or switch to them. However, pop-up forms aren't maximized. If you want a form to maintain its size when other windows are maximized, set its **PopUp** property to **Yes**.

To run the **MaximizeWindow** action in a Visual Basic for Applications module, use the **Maximize** method of the **DoCmd** object.

