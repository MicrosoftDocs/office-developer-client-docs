---
title: MoveAndSizeWindow Macro Action
TOCTitle: MoveAndSizeWindow Macro Action
ms:assetid: 86bcf45f-90ce-4ca2-a7fb-efbe5347d137
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff197001(v=office.15)
ms:contentKeyID: 48546090
ms.date: 09/18/2015
mtps_version: v=office.15
---

# MoveAndSizeWindow Macro Action


_**Applies to:** Access 2013 | Office 2013_

**In this article**  
Setting  
Remarks  
Example  

If you have set your document window options to use overlapping windows instead of tabbed documents, you can use the **MoveAndSizeWindow** action to move or resize the active window. For information on how to set document window options, see the Remarks section.

## Setting

The **MoveAndSizeWindow** action has the following arguments.

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
<td><p><strong>Right</strong></p></td>
<td><p>The new horizontal position of the window's upper-left corner, measured from the left edge of its containing window. Enter the position in the <strong>Right</strong> box in the <strong>Action Arguments</strong> section of the Macro Builder pane.</p></td>
</tr>
<tr class="even">
<td><p><strong>Down</strong></p></td>
<td><p>The new vertical position of the window's upper-left corner, measured from the top edge of its containing window.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Width</strong></p></td>
<td><p>The window's new width.</p></td>
</tr>
<tr class="even">
<td><p><strong>Height</strong></p></td>
<td><p>The window's new height.</p></td>
</tr>
</tbody>
</table>


If you leave an argument blank, Microsoft Access uses the window's current setting.

You must enter a value for at least one argument.


> [!NOTE]
> <P>Each measurement is in inches or centimeters, depending on the regional settings in Windows Control Panel.</P>



## Remarks

To set up an application to use overlapping windows instead of tabbed documents, use the following procedure:

1.  and then click **Options**

2.  Click **Current Database**.

3.  In the **Application Options** section, under **Document Window Options**, click **Overlapping Windows**.

4.  Click **OK**, and then close and reopen the database.

This action is similar to clicking **Move** or **Size** on the window's **Control** menu. With the menu commands, you use the keyboard's arrow keys to move or resize the window. With the **MoveAndSizeWindow** action, you enter the position and size measurements directly. You can also use the mouse to move and size windows.

You can use this action on any window, in any view.

**Tips**

  - To move a window without resizing it, enter values for the **Right** and **Down** arguments but leave the **Width** and **Height** arguments blank.

  - To resize a window without moving it, enter values for the **Width** and **Height** arguments but leave the **Right** and **Down** arguments blank.

To run the **MoveAndSizeWindow** action in a Visual Basic for Applications (VBA) module, use the **MoveSize** method of the **DoCmd** object.

## Example

**Synchronize forms by using a macro**

The following macro opens a Product List form in the lower-right corner of the Suppliers form, displaying the current supplier's products. It shows the use of the **Echo**, **MessageBox**, **GoToControl**, **StopMacro**, **OpenForm**, and **MoveAndSizeWindow** actions. It also shows the use of a conditional expression with the **MessageBox**, **GoToControl**, and **StopMacro** actions. This macro should be attached to the Review Products button on the Suppliers form.

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
<td><p>IsNull([Supplier ID])</p></td>
<td><p><strong>MessageBox</strong></p></td>
<td><p><strong>Message</strong>: Move to the supplier record whose products you want to see, then click the Review Products button again. <strong>Beep</strong>: <strong>YesType</strong>: <strong>NoneTitle</strong>: Select a Supplier</p></td>
<td><p>If there is no current supplier on the Suppliers form, display a message.</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
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
<td><p><strong>Form Name</strong>: Product List <strong>View</strong>: <strong>DatasheetFilter Name</strong>: <strong>Where Condition</strong>: [Supplier ID] = [Forms]![Suppliers]![SupplierID] <strong>Data Mode</strong>: <strong>Read OnlyWindow Mode</strong>: <strong>Normal</strong></p></td>
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

