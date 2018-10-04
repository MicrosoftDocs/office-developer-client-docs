---
title: SetReturnVar Macro Action
TOCTitle: SetReturnVar Macro Action
ms:assetid: 53719857-00bb-4f33-b5d2-93aff92d736e
ms:mtpsurl: https://msdn.microsoft.com/library/Ff193989(v=office.15)
ms:contentKeyID: 48544870
ms.date: 09/18/2015
mtps_version: v=office.15
---

# SetReturnVar Macro Action


**Applies to**: Access 2013 | Office 2013

**In this article**  
Setting  
Remarks  
Example  
About the Contributors  

The **SetReturnVar** action creates a return variable and sets it to a specific value.


> [!NOTE]
> <P>The <STRONG>SetReturnVar</STRONG> action is available only in Data Macros.</P>



## Setting

The **SetReturnVar** action has the following arguments.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Argument</p></th>
<th><p>Required</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Name</p></td>
<td><p>Yes</p></td>
<td><p>A string that specifies the name of the variable.</p></td>
</tr>
<tr class="even">
<td><p>Expression</p></td>
<td><p>Yes</p></td>
<td><p>An expression that will be used to set the value for this temporary variable. Do not precede the expression with the equal sign (=). You can click the <strong>Build</strong> button to use the <strong>Expression Builder</strong> to set this argument.</p></td>
</tr>
</tbody>
</table>


## Remarks

The **SetReturnVar** action is used to create a **ReturnVar**, which is variable that can be used by macros that call a data macro by using the **RunDataMacro** action.

Once a **ReturnVar** is created by the **SetReturnVar** action, the calling macro can use it in an expression. For example, if you created a **ReturnVar** named **UpdateSuccess**, you could use the variable by using the following syntax:

    =[ReturnVars]![UpdateSuccess]

The **SetReturnVar** action can be used only in named data macros. It is not available in data macros that are attached to a data macro event.

## Example

The following example shows how to use the SetReturnVar action to return a value from a named data macro. A ReturnVar named **CurrentServiceRequest** is returned to the macro or Visual Basic for Applications (VBA) subroutine that called the named data macro.

**Sample code provided by:** The [Microsoft Access 2010 Programmer’s Reference](https://www.wrox.com/wileycda/wroxtitle/access-2010-programmer-s-reference.productcd-0470591668.html)

    RunDataMacro
        Macro Name tblServiceRequests.dmGetCurrentServiceRequest
    
    Parameters
        prmAssignedTo =[ID]
    
    SetProperty
        Control Name txtCurrentSR
        Property Value
        Value =[ReturnVars]![CurrentServiceRequest]

## About the Contributors

Wrox Press is driven by the Programmer to Programmer philosophy. Wrox books are written by programmers for programmers, and the Wrox brand means authoritative solutions to real-world programming problems.

