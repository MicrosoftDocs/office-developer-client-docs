---
title: 'How to: Apply a Custom Ribbon to a Form or Report'
TOCTitle: 'How to: Apply a Custom Ribbon to a Form or Report'
ms:assetid: 7dcdfa42-3eaa-43f9-b99d-56b2cac97f84
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff196428(v=office.15)
ms:contentKeyID: 48545865
ms.date: 09/18/2015
mtps_version: v=office.15
---

# How to: Apply a Custom Ribbon to a Form or Report


**Applies to**: Access 2013 | Office 2013

The ribbon uses text-based, declarative XML markup that simplifies creating and customizing the ribbon. With a few lines of XML, you can create just the right interface for the user. Access provides flexibility in customizing the ribbon user interface. For example, customization markup can be stored in a table, embedded in a VBA procedure, stored in another Access database, or linked to from an Excel worksheet. This topic describes how to apply customized ribbons when loading a form or report.

## Making the Ribbon Customization XML Available

**Storing Ribbon Extensibility XML in a Table**

One method that you can use to make ribbon customizations available is to store them in a table. If you store the customizations in a table named **USysRibbons**, the customizations can be implemented without using macros or VBA code.

**USysRibbons** is a user-created system table. The table must be created using specific column names in order for the ribbon customizations to be implemented. The following table lists the settings to use when creating the **USysRibbons** table.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Column Name</p></th>
<th><p>Data Type</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>RibbonName</strong></p></td>
<td><p>Text</p></td>
<td><p>Contains the name of the custom ribbon to be associated with this customization</p></td>
</tr>
<tr class="even">
<td><p><strong>RibbonXML</strong></p></td>
<td><p>Memo</p></td>
<td><p>Contains the ribbon Extensibility XML (RibbonX) that defines the ribbon customization</p></td>
</tr>
</tbody>
</table>


**Loading Ribbon Extensibility XML Programmatically**

You can use the **[LoadCustomUI](https://msdn.microsoft.com/en-us/library/ff194416\(v=office.15\))** method to load ribbon customizations programmatically. Typically, to create and make the ribbon available to the application, you first create a module in the database with a procedure that calls the **LoadCustomUI** method, passing in the name of the ribbon and the XML customization markup.

The XML markup can come from a **Recordset** object created from a table, from a source external to the database such as an XML file that you parse into a string, or from XML markup embedded directly inside the procedure. You can make different ribbons using multiple calls to the **LoadCustomUI** method, passing in different XML markup as long as the name of each ribbon and the **id** attribute of the tabs that make up the ribbon are unique.

After the procedure is complete, you then create an AutoExec macro that calls the procedure by using the RunCode action. That way, when the application is started, the **LoadCustomUI** method is automatically executed and all of the custom ribbons are made available to the application.

## Assigning Custom Ribbons to Forms or Reports

1.  Follow the process described previously to make the customized ribbon available to the application.

2.  Open the form or report in Design view.

3.  On the Design tab, click **Property Sheet**.

4.  On the **All** tab of the Property window, click the **Ribbon Name** list and then select a ribbon.

5.  Save, close, and then reopen the form or report. The ribbon UI you selected is displayed.


> [!NOTE]
> <P>The tabs displayed in the ribbon UI are additive. That is, unless you specifically hide the tabs or set the <EM>Start from Scratch</EM> attribute to <STRONG>True</STRONG>, the tabs displayed in a form's or report's ribbon user interface are in addition to the existing tabs.</P>




> [!NOTE]
> <P>For more information about the ribbon UI in other Office applications, see <A href="https://msdn.microsoft.com/en-us/library/ff862537(v=office.15)">Overview of the Office Fluent Ribbon</A>.</P>


