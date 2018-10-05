---
title: SetProperty Macro Action
TOCTitle: SetProperty Macro Action
ms:assetid: 58d2eac3-35b2-e9f8-47e0-62c9b52f2c24
ms:mtpsurl: https://msdn.microsoft.com/library/Ff194340(v=office.15)
ms:contentKeyID: 48545004
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- vbaac10.chm139044
f1_categories:
- Office.Version=v15
---

# SetProperty Macro Action

**Applies to**: Access 2013 | Office 2013

You can use the **SetProperty** action to set a property for a control on a form or a report.

## Setting

The **SetProperty** action has the following arguments.

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
<td><p>Control Name</p></td>
<td><p>Type the name of the field or control for which you want to set the property value. Use only the control name, not the full syntax. Leave this argument blank to set the property for the current form or report.</p></td>
</tr>
<tr class="even">
<td><p>Property</p></td>
<td><p>Select the property that you want to set. See the <strong>Remarks</strong> section in this article for a list of the properties that can be set by using this action.</p></td>
</tr>
<tr class="odd">
<td><p>Value</p></td>
<td><p>Type the value that the property is to be set to. For properties whose values are either Yes or No, use <strong>-1</strong> for Yes and <strong>0</strong> for No.</p></td>
</tr>
</tbody>
</table>


## Remarks

- You can use the **SetProperty** action to set the following properties of a control: **Enabled**, **Visible**, **Locked**, **Left**, **Top**, **Width**, **Height**, **Fore Color**, **Back Color**, or **Caption**.

- If you enter an invalid value for the ***Value*** argument, no error occurs, but Access might change the property to a different value, depending on how it interprets the argument.

- You can use the **SetProperty** action in a stand-alone macro only if you precede it with an action that selects the form or report containing the control for which you are setting the property. If the form or report is not open, you can use the **OpenForm** or **OpenReport** action to open and select it. If the form or report is already open, you can use the **SelectObject** action to select it. You can then use the **SetProperty** action to set the property. Selecting the object is not necessary if you use the **SetProperty** action in a macro which is embedded in a control on the same form or report as the control for which you are setting the property.

- To run the **SetProperty** action in a VBA module, use the **SetProperty** method of the **DoCmd** object.

## Example

The following example shows how to use the SetProperty action to toggle the visibility of the **MyTextBox** text box.

**Sample code provided by** the [Microsoft Access 2010 Programmer’s Reference](https://www.amazon.com/Microsoft-Access-2010-Programmers-Reference/dp/8126528125).

```vb
    Submacro: TestVisible
        SetProperty
            Control Name Text40
            Property Visible
            Value =Not[Text40].[Visible]
    End Submacro
```
