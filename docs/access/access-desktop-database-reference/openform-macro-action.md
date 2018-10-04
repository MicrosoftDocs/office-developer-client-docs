---
title: OpenForm Macro Action
TOCTitle: OpenForm Macro Action
ms:assetid: c519a9d7-99d4-4765-ad96-59c3fe1be9e3
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff823095(v=office.15)
ms:contentKeyID: 48547604
ms.date: 09/18/2015
mtps_version: v=office.15
---

# OpenForm Macro Action


_**Applies to:** Access 2013 | Office 2013_

**In this article**  
Setting  
Remarks  
Examples  

You can use the **OpenForm** action to open a form in Form view, Design view, Print Preview, or Datasheet view. You can select data entry and window modes for the form and restrict the records that the form displays.

## Setting

The **OpenForm** action has the following arguments.

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
<td><p><strong>Form Name</strong></p></td>
<td><p>The name of the form to open. The <strong>Form Name</strong> box in the <strong>Action Arguments</strong> section of the Macro Builder pane shows all forms in the current database. This is a required argument. If you run a macro containing the <strong>OpenForm</strong> action in a library database, Microsoft Access first looks for the form with this name in the library database, and then in the current database.</p></td>
</tr>
<tr class="even">
<td><p><strong>View</strong></p></td>
<td><p>The view in which the form will open. Click <strong>Form</strong>, <strong>Design</strong>, <strong>Print Preview</strong>, <strong>Datasheet</strong>, <strong>PivotTable</strong>, or <strong>PivotChart</strong> in the <strong>View</strong> box. The default is <strong>Form</strong>.</p>

> [!NOTE]
> <P>The <STRONG>View</STRONG> argument setting overrides the settings of the form's <STRONG>DefaultView</STRONG> and <STRONG>ViewsAllowed</STRONG> properties. For example, if a form's <STRONG>ViewsAllowed</STRONG> property is set to <STRONG>Datasheet</STRONG>, you can still use the <STRONG>OpenForm</STRONG> action to open the form in Form view.</P>


<p></p></td>
</tr>
<tr class="odd">
<td><p><strong>Filter Name</strong></p></td>
<td><p>A filter that restricts or sorts the form's records. You can enter the name of either an existing query or a filter that was saved as a query. However, the query must include all the fields in the form you are opening or have its <strong>OutputAllFields</strong> property set to <strong>Yes</strong>.</p></td>
</tr>
<tr class="even">
<td><p><strong>Where Condition</strong></p></td>
<td><p>A valid SQL WHERE clause (without the word WHERE) or expression that Access uses to select records from the form's underlying table or query. If you select a filter with the <strong>Filter Name</strong> argument, Access applies this WHERE clause to the results of the filter. To open a form and restrict its records to those specified by the value of a control on another form, use the following expression: <strong>[</strong><em>fieldname</em><strong>] = Forms![</strong><em>formname</em><strong>]![</strong><em>controlname on other form</em><strong>]</strong> Replace <em>fieldname</em> with the name of a field in the underlying table or query of the form you want to open. Replace <em>formname</em> and <em>controlname on other form</em> with the name of the other form and the control on the other form that contains the value you want records in the first form to match.</p>

> [!NOTE]
> <P>The maximum length of the <STRONG>Where Condition</STRONG> argument is 255 characters. If you need to enter a more complex SQL WHERE clause longer than this, use the <STRONG>OpenForm</STRONG> method of the <STRONG>DoCmd</STRONG> object in a Visual Basic for Applications (VBA) module instead. You can enter SQL WHERE clause statements of up to 32,768 characters in VBA.</P>


<p></p></td>
</tr>
<tr class="odd">
<td><p><strong>Data Mode</strong></p></td>
<td><p>The data entry mode for the form. This applies only to forms opened in Form view or Datasheet view. Click <strong>Add</strong> (the user can add new records but can't edit existing records), <strong>Edit</strong> (the user can edit existing records and add new records), or <strong>Read Only</strong> (the user can only view records). The default is <strong>Edit</strong>. <strong>Notes</strong></p>
<ul>
<li><p>The <strong>Data Mode</strong> argument setting overrides the settings of the form's <strong>AllowEdits</strong>, <strong>AllowDeletions</strong>, <strong>AllowAdditions</strong>, and <strong>DataEntry</strong> properties. For example, if a form's <strong>AllowEdits</strong> property is set to <strong>No</strong>, you can still use the <strong>OpenForm</strong> action to open the form in Edit mode.</p></li>
<li><p>If you leave this argument blank, Access opens the form in the data entry mode set by the form's <strong>AllowEdits</strong>, <strong>AllowDeletions</strong>, <strong>AllowAdditions</strong>, and <strong>DataEntry</strong> properties.</p></li>
</ul>
<p></p></td>
</tr>
<tr class="even">
<td><p><strong>Window Mode</strong></p></td>
<td><p>The window mode in which the form opens. Click <strong>Normal</strong> (the form opens in the mode set by its properties), <strong>Hidden</strong> (the form is hidden), <strong>Icon</strong> (the form opens minimized as a small title bar at the bottom of the screen), or <strong>Dialog</strong> (the form's <strong>Modal</strong> and <strong>PopUp</strong> properties are set to <strong>Yes</strong>). The default is <strong>Normal</strong>.</p>

> [!NOTE]
> <P>Some <STRONG>Window Mode</STRONG> argument settings do not apply when using tabbed documents. To switch to overlapping windows:</P>


<p></p>
<ol>
<li><p>Click the File tab and then click <strong>Options</strong>.</p></li>
<li><p>In the <strong>Access Options</strong> dialog box, click <strong>Current Database</strong>.</p></li>
<li><p>In the <strong>Application Options</strong>section, under <strong>Document Window Options</strong>, click <strong>Overlapping Windows</strong>.</p></li>
<li><p>Click <strong>OK</strong>, then close and reopen the database.</p></li>
</ol></td>
</tr>
</tbody>
</table>


## Remarks

This action is similar to double-clicking a form in the Navigation Pane, or right-clicking the form in the Navigation Pane and then selecting a view.

A form can be modal (it must be closed or hidden before the user can perform any other action) or modeless (the user can move to other windows while the form is open). It can also be a pop-up form (a form used to collect or display information that remains on top of all other Access windows). You set the **Modal** and **PopUp** properties when you design the form. If you use **Normal** for the **Window Mode** argument, the form opens in the mode specified by these property settings. If you use **Dialog** for the **Window Mode** argument, these properties are both set to **Yes**. A form opened as hidden or as an icon returns to the mode specified by its property settings when you show or restore it.

When you open a form with the **Window Mode** argument set to **Dialog**, Access suspends the macro until the form is closed or hidden. You can hide a form by setting its **Visible** property to **No** by using the **SetValue** action.


> [!TIP]
> <P>You can select a form in the Navigation Pane and drag it to a macro action row. This automatically creates an <STRONG>OpenForm</STRONG> action that opens the form in Form view.</P>



The filter and WHERE condition you apply become the setting of the form's **Filter** property.

## Examples

**Set the value of a control by using a macro**

The following macro opens the Add Products form from a button on the Suppliers form. It shows the use of the **Echo**, **CloseWindow**, **OpenForm**, **SetValue**, and **GoToControl** actions. The **SetValue** action sets the Supplier ID control on the Products form to the current supplier on the Suppliers form. The **GoToControl** action then moves the focus to the Category ID field, where you can begin to enter data for the new product. This macro should be attached to the Add Products button on the Suppliers form.

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
<td><p>Set the Supplier ID control to the current supplier on the Suppliers form.</p></td>
</tr>
<tr class="odd">
<td><p><strong>GoToControl</strong></p></td>
<td><p><strong>Control Name</strong>: CategoryID</p></td>
<td><p>Go to the Category ID control.</p></td>
</tr>
</tbody>
</table>


The following macro opens a Product List form in the lower-right corner of the Suppliers form, displaying the current supplier's products. It shows the use of the **Echo**, **MessageBox**, **GoToControl**, **StopMacro**, **OpenForm**, and **MoveAndSizeWindow** actions. It also shows the use of a conditional expression with the **MessageBox**, **GoToControl**, and **StopMacro** actions. This macro should be attached to the Review Products button on the Suppliers form.

**Synchronize forms by using a macro**

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Condition</p></th>
<th><p>Action</p></th>
<th><p>Arguments: Setting</p></th>
<th><p>Comment</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p></p></td>
<td><p><strong>Echo</strong></p></td>
<td><p><strong>Echo On</strong>: <strong>No</strong></p></td>
<td><p>Stop screen updating while the macro is running.</p></td>
</tr>
<tr class="even">
<td><p>IsNull([SupplierID])</p></td>
<td><p><strong>MessageBox</strong></p></td>
<td><p><strong>Message</strong>: Move to the supplier record whose products you want to see, then click the Review Products button again. <strong>Beep</strong>: <strong>YesType</strong>: <strong>NoneTitle</strong>: Select a Supplier</p></td>
<td><p>If there is no current supplier on the Suppliers form, display a message.</p></td>
</tr>
<tr class="odd">
<td><p>...</p></td>
<td><p><strong>GoToControl</strong></p></td>
<td><p><strong>Control Name</strong>: CompanyName</p></td>
<td><p>Move focus to the CompanyName control.</p></td>
</tr>
<tr class="even">
<td><p>...</p></td>
<td><p><strong>StopMacro</strong></p></td>
<td><p></p></td>
<td><p>Stop the macro.</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p><strong>OpenForm</strong></p></td>
<td><p><strong>Form Name</strong>: Product List <strong>View</strong>: <strong>DatasheetFilter Name</strong>: <strong>Where Condition</strong>: [SupplierID] = [Forms]![Suppliers]![SupplierID] <strong>Data Mode</strong>: <strong>Read OnlyWindow Mode</strong>: <strong>Normal</strong></p></td>
<td><p>Open the Product List form and show the current supplier's products.</p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p><strong>MoveAndSizeWindow</strong></p></td>
<td><p><strong>Right</strong>: 0.7799&quot; <strong>Down</strong>: 1.8&quot;</p></td>
<td><p>Position the Product List form in the lower right of the Suppliers form.</p></td>
</tr>
</tbody>
</table>

