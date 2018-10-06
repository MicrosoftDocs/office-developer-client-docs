---
title: DisplayHourglassPointer Macro Action
TOCTitle: DisplayHourglassPointer Macro Action
ms:assetid: 2c93039a-f75c-abeb-1dfa-e632a5bdf6f2
ms:mtpsurl: https://msdn.microsoft.com/library/Ff192103(v=office.15)
ms:contentKeyID: 48543957
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- vbaac10.chm117200
f1_categories:
- Office.Version=v15
---

# DisplayHourglassPointer Macro Action


**Applies to**: Access 2013 | Office 2013

You can use the **DisplayHourglassPointer** action to change the mouse pointer to an image of an hourglass (or another icon you've chosen) while a macro is running. This action can provide a visual indication that the macro is running. This is especially useful when a macro action or the macro itself takes a long time to run.

## Setting

The **DisplayHourglassPointer** action has the following argument.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Action argument</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Hourglass On</strong></p></td>
<td><p>Click <strong>Yes</strong> (display the icon) or <strong>No</strong> (display the normal mouse pointer) in the <strong>Hourglass On</strong> box in the <strong>Action Arguments</strong> section of the Macro Builder pane. The default is <strong>Yes</strong>.</p></td>
</tr>
</tbody>
</table>


## Remarks

You often use this action if you have turned echo off by using the **Echo** action. When echo is off, Access suspends screen updates until the macro is finished.

Access automatically resets the **Hourglass On** argument to **No** when the macro finishes running.


> [!NOTE]
> <UL>
> <LI>
> <P>In Microsoft Windows, this is the icon you set for <STRONG>Busy</STRONG> in the <STRONG>Mouse Properties</STRONG> dialog box of Windows Control Panel. The default for all Windows operating systems is an animated hourglass icon.</P>
> <LI>
> <P>You can choose another icon if you want.</P></LI></UL>



To run the **DisplayHourglassPointer** action in a Visual Basic for Applications (VBA) module, use the **Hourglass** method of the **DoCmd** object.

