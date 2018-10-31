---
title: RunDataMacro Macro Action
TOCTitle: RunDataMacro Macro Action
ms:assetid: fe4ac2f4-7851-7797-ce91-5f2dd3ba4d22
ms:mtpsurl: https://msdn.microsoft.com/library/Ff837269(v=office.15)
ms:contentKeyID: 48548933
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- vbaac10.chm168493
f1_categories:
- Office.Version=v15
---

# RunDataMacro Macro Action

**Applies to**: Access 2013, Office 2013

You can use the **RunDataMacro** action to run a named data macro.

## Setting

The **RunDataMacro** action has the following argument.

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
<td><p>Name</p></td>
<td><p>The name of the data macro to run.</p></td>
</tr>
</tbody>
</table>


## Remarks

You can use the **RunDataMacro** action in macros, named data macros, and the following macro events: **[After Delete Macro Event](after-delete-macro-event.md)**, **[After Insert Macro Event](after-insert-macro-event.md)** and **[After Update Macro Event](after-update-macro-event.md)**.

The name of the data macro must include the table to which it is attached (for example, **Comments.AddComment**, not just **AddComment**).

When you select the data macro that you want to run in the macro designer, Access determines if the data macro requires parameters. If the data macro requires parameters, text boxes appear where you can type in the arguments.

When you run a macro that contains the **RunDataMacro** action and it reaches the **RunDataMacro** action, Access runs the called data macro. When the called data macro has finished, Access returns to the original macro and runs the next action.

## Example

The following example shows how to pass a parameter to a named data macro. The dmGetCurrentServiceRequest data macro of the tblServiceRequests table is called by using the RunDataMacro action. When the dmGetCurrentServiceRequest is finished, the CurrentServiceRequest variable returned form the data macro is written to the txtCurrentSR text box.

**Sample code provided by** the [Microsoft Access 2010 Programmer’s Reference](https://www.amazon.com/Microsoft-Access-2010-Programmers-Reference/dp/8126528125).

```vb
    RunDataMacro
        Macro Name tblServiceRequests.dmGetCurrentServiceRequest
    
    Parameters
        prmAssignedTo =[ID]
    
    SetProperty
        Control Name txtCurrentSR
        Property Value
        Value =[ReturnVars]![CurrentServiceRequest]
```
