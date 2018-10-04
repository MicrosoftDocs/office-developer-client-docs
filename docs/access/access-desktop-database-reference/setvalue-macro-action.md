---
title: SetValue Macro Action
TOCTitle: SetValue Macro Action
ms:assetid: a08be0c1-a053-45f9-b4ae-709fedc58e8b
ms:mtpsurl: https://msdn.microsoft.com/library/Ff820771(v=office.15)
ms:contentKeyID: 48546712
ms.date: 09/18/2015
mtps_version: v=office.15
---

# SetValue Macro Action


**Applies to**: Access 2013 | Office 2013

**In this article**  
Setting  
Remarks  
Example  

You can use the **SetValue** action to set the value of a Microsoft Access field, control, or property on a form, a form datasheet, or a report.


> [!NOTE]
> <P>You cannot use the <STRONG>SetValue</STRONG> action to set the value of an Access property that returns an object.</P>




> [!NOTE]
> <P>This action will not be allowed if the database is not trusted. For more information about enabling macros, see the links in the See Also section of this article.</P>



## Setting

The **SetValue** action has the following arguments.

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
<td><p><strong>Item</strong></p></td>
<td><p>The name of the field, control, or property whose value you want to set. Enter the field, control, or property name in the <strong>Item</strong> box in the <strong>Action Arguments</strong> section of the Macro Builder pane. You must use the full syntax to refer to this item, such as <em>controlname</em> (for a control on the form or report from which the macro was called) or <strong>Forms</strong>!<em>formname</em>!<em>controlname</em>. This is a required argument.</p></td>
</tr>
<tr class="even">
<td><p><strong>Expression</strong></p></td>
<td><p>The expression Access uses to set the value for this item. You must always use the full syntax to refer to any objects in the expression. For example, to increase the value in a Salary control on an Employees form by 10 percent, use Forms!Employees!Salary*1.1. This is a required argument.</p>

> [!NOTE]
> <P>You shouldn't use an equal sign (<STRONG>=</STRONG>) before the expression in this argument. If you do, Access evaluates the expression and then uses this value as the expression in this argument. This can produce unexpected results if the expression is a string.</P>


<p>For example, if you type <strong>=&quot;String1&quot;</strong> for this argument, Access first evaluates the expression as String1. Then it uses String1 as the expression in this argument, expecting to find a control or property named String1 on the form or report that called the macro.</p></td>
</tr>
</tbody>
</table>



> [!NOTE]
> <P>In an Access database (.mdb or .accdb), click the <STRONG>Build</STRONG> button to use the Expression Builder to create an expression for either of these arguments.</P>



## Remarks

You can use this action to set a value for a field or control on a form, a form datasheet, or a report. You can also set the value for almost all control, form, and report properties in any view. To find out whether a particular property can be set by using a macro and which views it can be set in, see the Help topic for that property in the Visual Basic Editor.

You can also set the value for a field in a form's underlying table even if the form doesn't contain a control bound to the field. Use the syntax **Forms**\!*formname*\!*fieldname* in the **Item** box to set the value for such a field. You can also refer to a field in a report's underlying table by using the syntax **Reports**\!*reportname*\!*fieldname*, but there must be a control on the report bound to this field, or the field must be referred to in a calculated control on the report.

If you set the value of a control on a form, the **SetValue** action doesn't trigger the control's form-level validation rules, but it does trigger the underlying field's table-level validation rules if the control is a bound control. The **SetValue** action also triggers recalculation, but the recalculation may not happen immediately. To trigger immediate repainting and force the recalculation to completion, use the **RepaintObject** action. The value you set in a control by using the **SetValue** action is also not affected by an input mask set in the control's or underlying field's **InputMask** property.

To change the value of a control, you can use the **SetValue** action in a macro specified by the control's **AfterUpdate** event property. However, you can't use the **SetValue** action in a macro specified by a control's **BeforeUpdate** event property to change the value of the control (although you can use the **SetValue** action to change the value of other controls). You can also use the **SetValue** action in a macro specified by the **BeforeUpdate** or **AfterUpdate** property of a form to change the value of any controls in the current record.


> [!NOTE]
> <P>You can't use the <STRONG>SetValue</STRONG> action to set the value of the following controls:</P>
> <UL>
> <LI>
> <P>Bound controls and calculated controls on reports.</P>
> <LI>
> <P>Calculated controls on forms.</P></LI></UL>




> [!TIP]
> <P>You can use the <STRONG>SetValue</STRONG> action to hide or show a form in Form view. Enter <STRONG>Forms</STRONG>!<EM>formname</EM><STRONG>.Visible</STRONG> in the <STRONG>Item</STRONG> box and <STRONG>No</STRONG> or <STRONG>Yes</STRONG> in the <STRONG>Expression</STRONG> box. Setting a modal form's <STRONG>Visible</STRONG> property to <STRONG>No</STRONG> hides the form and makes it modeless. Setting the property to <STRONG>Yes</STRONG> displays the form and makes it modal again.</P>



Changing the value of or adding new data in a control by using the **SetValue** action in a macro doesn't trigger events such as **BeforeUpdate**, **BeforeInsert**, or **Change** that occur when you change or enter data in these controls in the user interface. These events also don't occur if you set the value of the control by using a Visual Basic for Applications (VBA) module.

This action isn't available in a VBA module. Set the value directly in VBA.

## Example

**Set the value of a control by using a macro**

The following macro opens the Add Products form from a button on the Suppliers form. It shows the use of the **Echo**, **CloseWindow**, **OpenForm**, **SetValue**, and **GoToControl** actions. The **SetValue** action sets the SupplierID control on the Products form to the current supplier on the Suppliers form. The **GoToControl** action then moves the focus to the CategoryID field, where you can begin to enter data for the new product. This macro should be attached to the Add Products button on the Suppliers form.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Action</p></th>
<th><p>Arguments: Setting</p></th>
<th><p>Comment</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Echo</strong></p></td>
<td><p><strong>Echo On</strong>: <strong>No</strong></p></td>
<td><p>Stop screen updating while the macro is running.</p></td>
</tr>
<tr class="even">
<td><p><strong>CloseWindow</strong></p></td>
<td><p><strong>Object Type</strong>: <strong>FormObject Name</strong>: Product List <strong>Save</strong>: <strong>No</strong></p></td>
<td><p>Close the Product List form.</p></td>
</tr>
<tr class="odd">
<td><p><strong>OpenForm</strong></p></td>
<td><p><strong>Form Name</strong>: Products <strong>View</strong>: <strong>FormData Mode</strong>: <strong>AddWindow Mode</strong>: <strong>Normal</strong></p></td>
<td><p>Open the Products form.</p></td>
</tr>
<tr class="even">
<td><p><strong>SetValue</strong></p></td>
<td><p><strong>Item</strong>: [Forms]![Products]![SupplierID] <strong>Expression</strong>: SupplierID</p></td>
<td><p>Set the SupplierID control to the current supplier on the Suppliers form.</p></td>
</tr>
<tr class="odd">
<td><p><strong>GoToControl</strong></p></td>
<td><p><strong>Control Name</strong>: CategoryID</p></td>
<td><p>Go to the CategoryID control.</p></td>
</tr>
</tbody>
</table>

