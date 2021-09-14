---
title: GoToPage macro action
TOCTitle: GoToPage macro action
ms:assetid: 611aadff-83b7-e74d-4093-93fb5ce6e3ab
ms:mtpsurl: https://msdn.microsoft.com/library/Ff194858(v=office.15)
ms:contentKeyID: 48545199
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- vbaac10.chm129285
f1_categories:
- Office.Version=v15
ms.localizationpriority: medium
---

# GoToPage macro action

**Applies to**: Access 2013, Office 2013

You can use the **GoToPage** action to move the focus in the active form to the first control on a specified page. You can use this action if you have created a form with page breaks that contains groups of related information. For example, you might have an Employees form with personal information on one page, office information on another page, and sales information on a third page. You can use the **GoToPage** action to move to the desired page. You can also present multiple pages of information on a single form by using tab controls.

## Setting

The **GoToPage** action has the following arguments.

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
<td><p><strong>Page Number</strong></p></td>
<td><p>The number of the page to which you want to move the focus. Enter the page number in the <strong>Page Number</strong> box in the <strong>Action Arguments</strong> section of the Macro Builder pane. If you leave this argument blank, the focus stays on the current page. You can use the <strong>Right</strong> and <strong>Down</strong> arguments to display the part of the page you want to see.</p></td>
</tr>
<tr class="even">
<td><p><strong>Right</strong></p></td>
<td><p>The horizontal position of the spot on the page, measured from the left edge of its containing window, that is to appear at the left edge of the window. This is required if you specify a <strong>Down</strong> argument.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Down</strong></p></td>
<td><p>The vertical position of the spot on the page, measured from the top edge of its containing window, that is to appear at the top edge of the window. This is required if you specify a <strong>Right</strong> argument.</p></td>
</tr>
</tbody>
</table>

> [!NOTE]
> The **Right** and **Down** arguments are measured in inches or centimeters, depending on the regional settings in Windows Control Panel.

## Remarks

You can use this action to select the first control (as defined by the form's tab order) on the specified page. Use the **GoToControl** action to move to a particular control on the form.

You can use the **Right** and **Down** arguments for forms with pages larger than the Access window. Use the **Page Number** argument to move to the desired page, and then use the **Right** and **Down** arguments to display the part of the page you want to see. Access displays the part of the page whose upper-left corner is offset the specified distance from the upper-left corner of the page.

You can't use the **GoToPage** action in the following cases:

- To move the focus to a page on a hidden form.

- To move the focus from one page to another within the tab control.

To run the **GoToPage** action in a Visual Basic for Applications (VBA) module, use the **GoToPage** method of the **DoCmd** object.

