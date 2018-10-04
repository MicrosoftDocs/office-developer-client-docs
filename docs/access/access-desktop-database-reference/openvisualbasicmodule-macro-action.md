---
title: OpenVisualBasicModule Macro Action
TOCTitle: OpenVisualBasicModule Macro Action
ms:assetid: 26eb31c8-3c65-b17d-46cd-c8967434a7a0
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff191906(v=office.15)
ms:contentKeyID: 48543826
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- vbaac10.chm50916
f1_categories:
- Office.Version=v15
---

# OpenVisualBasicModule Macro Action


**Applies to**: Access 2013 | Office 2013

You can use the **OpenVisualBasicModule** action to open a specified Visual Basic for Applications (VBA) module at a specified procedure. This can be a Sub procedure, a Function procedure, or an event procedure.


> [!NOTE]
> <P>This action will not be allowed if the database is not trusted. For more information about enabling macros, see the links in the See Also section of this article.</P>



## Setting

The **OpenVisualBasicModule** action has the following arguments.

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
<td><p><strong>Module Name</strong></p></td>
<td><p>The name of the module you want to open. You can leave this argument blank if you want to search all the standard modules in the database for a procedure and open the appropriate module at that procedure. If you run a macro containing the <strong>OpenVisualBasicModule</strong> action in a library database, Microsoft Access first looks for the module with this name in the library database, and then in the current database.</p></td>
</tr>
<tr class="even">
<td><p><strong>Procedure Name</strong></p></td>
<td><p>The name of the procedure you want to open the module to. If you leave this argument blank, the module opens to the Declarations section.</p></td>
</tr>
</tbody>
</table>



> [!NOTE]
> <P>You must enter a valid name in either the <STRONG>Module Name</STRONG> or <STRONG>Procedure Name</STRONG> argument.</P>



## Remarks

You can use this action to open an event procedure by specifying the **Module Name** argument and the **Procedure Name** argument. For example, to open the **Click** event procedure of the PrintInvoice button on the form Orders, set the **Module Name** argument to **Form.Orders** and set the **Procedure Name** argument to **PrintInvoice\_Click**. To view the event procedure for a form or report, the form or report must be open.

Similarly, to open a procedure in a class module, you must specify the module name, although the class module does not have to open.

To open a private procedure, the module containing it must be open.

This action has the same effect as right-clicking a module in the Navigation Pane and then clicking **Design View**. This action also enables you to specify a procedure name and to search the standard modules in a database for procedures.


> [!TIP]
> <P>You can select a module in the Navigation Pane and drag it to a macro action row. This automatically creates an <STRONG>OpenVisualBasicModule</STRONG> action that opens the module to the Declarations section.</P>



To run the **OpenVisualBasicModule** action in a VBA module, use the **OpenModule** method of the **DoCmd** object.

