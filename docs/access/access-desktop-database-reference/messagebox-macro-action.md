---
title: MessageBox Macro Action
TOCTitle: MessageBox Macro Action
ms:assetid: 326a0e68-38fb-4f81-b319-5a70caa5aec4
ms:mtpsurl: https://msdn.microsoft.com/library/Ff192304(v=office.15)
ms:contentKeyID: 48544077
ms.date: 09/18/2015
mtps_version: v=office.15
---

# MessageBox Macro Action


**Applies to**: Access 2013 | Office 2013

**In this article**  
  
Setting  
Remarks  
Examples  


You can use the **MessageBox** action to display a message box containing a warning or an informational message. For example, you can use the **MessageBox** action with validation macros. When a control or record fails a validation condition in the macro, a message box can display an error message and provide instructions about the kind of data that should be entered.

## Setting

The **MessageBox** action has the following arguments.

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
<td><p><strong>Message</strong></p></td>
<td><p>The text in the message box. Enter the message text in the <strong>Message</strong> box in the <strong>Action Arguments</strong> section of the Macro Builder pane. You can type up to 255 characters or enter an expression (preceded by an equal sign).</p></td>
</tr>
<tr class="even">
<td><p><strong>Beep</strong></p></td>
<td><p>Specifies whether your computer's speaker sounds a beep tone when the message displays. Click <strong>Yes</strong> (sound the beep tone) or <strong>No</strong> (don't sound the beep tone). The default is <strong>Yes</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Type</strong></p></td>
<td><p>The type of message box. Each type has a different icon. Click <strong>None</strong>, <strong>Critical</strong>, <strong>Warning?</strong>, <strong>Warning!</strong>, or <strong>Information</strong>. The default is <strong>None</strong>.</p></td>
</tr>
<tr class="even">
<td><p><strong>Title</strong></p></td>
<td><p>The text displayed in the message box title bar. For example, you can have the title bar display &quot;Customer ID Validation&quot;. If you leave this argument blank, &quot;Microsoft Access&quot; is displayed.</p></td>
</tr>
</tbody>
</table>


## Remarks

You can use the **MessageBox** action to create a formatted error message similar to built-in error messages displayed by Microsoft Access. The **MessageBox** action permits you to supply a message in three sections for the Message argument. You separate the sections with the "@" character.

The following example displays a formatted message box with a sectioned message. The first section of text in the message is displayed as a bold heading. The second section is displayed as plain text beneath that heading. The third section is displayed as plain text beneath the second section, with a blank line between them.

Type the following string in the **Message** argument:

**Wrong button\!@This button doesn't work.@Try another.**

You can't run the **MessageBox** action in a Visual Basic for Applications (VBA) module. Use the **MsgBox** function instead.

## Examples

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


**Validate data by using a macro**

The following validation macro checks the postal codes entered in a Suppliers form. It shows the use of the **StopMacro**, **MessageBox**, **CancelEvent**, and **GoToControl** actions. A conditional expression checks the country/region and postal code entered in a record on the form. If the postal code isn't in the right format for the country/region, the macro displays a message box and cancels saving the record. It then returns you to the PostalCode control, where you can correct the error. This macro should be attached to the **BeforeUpdate** property of the Suppliers form.

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
<td><p>IsNull([CountryRegion])</p></td>
<td><p><strong>StopMacro</strong></p></td>
<td><p></p></td>
<td><p>If CountryRegion is <strong>Null</strong>, the postal code can't be validated.</p></td>
</tr>
<tr class="even">
<td><p>[CountryRegion] In (&quot;France&quot;,&quot;Italy&quot;,&quot;Spain&quot;) And Len([PostalCode]) &lt;&gt; 5</p></td>
<td><p><strong>MessageBox</strong></p></td>
<td><p><strong>Message</strong>: The postal code must be 5 characters. <strong>Beep</strong>: <strong>YesType</strong>: <strong>InformationTitle</strong>: Postal Code Error</p></td>
<td><p>If the postal code isn't 5 characters, display a message.</p></td>
</tr>
<tr class="odd">
<td><p>...</p></td>
<td><p><strong>CancelEvent</strong></p></td>
<td><p></p></td>
<td><p>Cancel the event.</p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p><strong>GoToControl</strong></p></td>
<td><p><strong>Control Name</strong>: PostalCode</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>[CountryRegion] In (&quot;Australia&quot;,&quot;Singapore&quot;) And Len([PostalCode]) &lt;&gt; 4</p></td>
<td><p><strong>MessageBox</strong></p></td>
<td><p><strong>Message</strong>: The postal code must be 4 characters. <strong>Beep</strong>: <strong>YesType</strong>: <strong>InformationTitle</strong>: Postal Code Error</p></td>
<td><p>If the postal code isn't 4 characters, display a message.</p></td>
</tr>
<tr class="even">
<td><p>...</p></td>
<td><p><strong>CancelEvent</strong></p></td>
<td><p></p></td>
<td><p>Cancel the event.</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p><strong>GoToControl</strong></p></td>
<td><p><strong>Control Name</strong>: PostalCode</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>([CountryRegion] = &quot;Canada&quot;) And ([PostalCode] Not Like&quot;[A-Z][0-9][A-Z] [0-9][A-Z][0-9]&quot;)</p></td>
<td><p><strong>MessageBox</strong></p></td>
<td><p><strong>Message</strong>: The postal code is not valid. Example of Canadian code: H1J 1C3 <strong>Beep</strong>: <strong>YesType</strong>: <strong>InformationTitle</strong>: Postal Code Error</p></td>
<td><p>If the postal code isn't correct for Canada, display a message. (Example of Canadian code: H1J 1C3)</p></td>
</tr>
<tr class="odd">
<td><p>...</p></td>
<td><p><strong>CancelEvent</strong></p></td>
<td><p></p></td>
<td><p>Cancel the event.</p></td>
</tr>
</tbody>
</table>

