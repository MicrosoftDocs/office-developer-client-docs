﻿---
title: SingleStep Macro Action
TOCTitle: SingleStep Macro Action
ms:assetid: 2836fe1d-fb9b-6b42-acfd-c52e468161d4
ms:mtpsurl: https://msdn.microsoft.com/library/Ff191989(v=office.15)
ms:contentKeyID: 48543855
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- vbaac10.chm47687
f1_categories:
- Office.Version=v15
---

# SingleStep Macro Action


**Applies to**: Access 2013 | Office 2013

You can use the **SingleStep** action to pause macro execution and open the **Macro Single Step** dialog box.

## Setting

The **SingleStep** action does not have any arguments.

## Remarks

  - Use the **SingleStep** action to troubleshoot a macro that is not working properly. You can add the **SingleStep** action to a macro just before an action that you suspect may be the cause of the problem. The action pauses the macro and opens the **Macro Single Step** dialog box. This dialog box displays information about the current macro action, such as the macro name, any specified conditions, the action name, arguments, and the error number, if applicable. In the dialog box, you can click **Step** to advance to the next macro action, **Stop All Macros** to stop the current macro and any other macros that are running, or **Continue** to stop single stepping and resume normal operation of the macro.

  - The **SingleStep** action has a similar effect to clicking **Single Step** in the **Tools** group on the **Design** tab of the Macro Builder. The difference between doing this and running the **SingleStep** action is that by running the action, you can place the action in the macro exactly where you want single stepping to begin. That way, you don't have to step through all the previous actions to get to the one you want to examine. On the other hand, when you click **Single Step** in the Macro Builder, you must do so before running the macro. In that case, single stepping begins at the first action in the macro.


> [!NOTE]
> <P>If you single-step all the way to the end of a macro without clicking <STRONG>Continue</STRONG>, single stepping will still be in effect when the macro ends. Any subsequent macro you run will start in single step mode. To turn off single stepping, either click <STRONG>Continue</STRONG> in the <STRONG>Macro Single Step</STRONG> dialog box, or, with a macro open in Design view, on the <STRONG>Design</STRONG> tab, in the <STRONG>Tools</STRONG> group, click <STRONG>Single Step</STRONG> so that it is no longer selected.</P>


