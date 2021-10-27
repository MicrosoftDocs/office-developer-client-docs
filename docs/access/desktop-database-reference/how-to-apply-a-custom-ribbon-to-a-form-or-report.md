---
title: Apply a custom ribbon to a form or report
TOCTitle: Apply a custom ribbon to a form or report
description: How to apply customized ribbons when loading a form or report in Access 2013.
ms:assetid: 7dcdfa42-3eaa-43f9-b99d-56b2cac97f84
ms:mtpsurl: https://msdn.microsoft.com/library/Ff196428(v=office.15)
ms:contentKeyID: 48545865
ms.date: 10/16/2018
mtps_version: v=office.15
ms.localizationpriority: high
---

# Apply a custom ribbon to a form or report

**Applies to**: Access 2013, Office 2013

The ribbon uses text-based, declarative XML markup that simplifies creating and customizing the ribbon. With a few lines of XML, you can create just the right interface for the user. Access provides flexibility in customizing the ribbon user interface. 

For example, customization markup can be stored in a table, embedded in a VBA procedure, stored in another Access database, or linked to an Excel worksheet. This topic describes how to apply customized ribbons when loading a form or report.

## Make the ribbon customization XML available

### Store ribbon extensibility XML in a table

One method that you can use to make ribbon customizations available is to store them in a table. If you store the customizations in a table named **USysRibbons**, the customizations can be implemented without using macros or VBA code.

**USysRibbons** is a user-created system table. The table must be created using specific column names for the ribbon customizations to be implemented. 

The following table lists the settings to use when creating the **USysRibbons** table.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Column name</p></th>
<th><p>Data type</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>RibbonName</strong></p></td>
<td><p>Text</p></td>
<td><p>Contains the name of the custom ribbon to be associated with this customization.</p></td>
</tr>
<tr class="even">
<td><p><strong>RibbonXML</strong></p></td>
<td><p>Memo</p></td>
<td><p>Contains the ribbon extensibility XML (RibbonX) that defines the ribbon customization.</p></td>
</tr>
</tbody>
</table>


### Load ribbon extensibility XML programmatically

You can use the **[LoadCustomUI](https://docs.microsoft.com/office/vba/api/Access.Application.LoadCustomUI)** method to load ribbon customizations programmatically. Typically, to create and make the ribbon available to the application, you first create a module in the database with a procedure that calls the **LoadCustomUI** method, passing in the name of the ribbon and the XML customization markup.

The XML markup can come from a **Recordset** object created from a table, from a source external to the database such as an XML file that you parse into a string, or from XML markup embedded directly inside the procedure. You can make different ribbons using multiple calls to the **LoadCustomUI** method, passing in different XML markup as long as the name of each ribbon and the **id** attribute of the tabs that make up the ribbon are unique.

After the procedure is complete, you then create an AutoExec macro that calls the procedure by using the RunCode action. That way, when the application is started, the **LoadCustomUI** method is automatically executed and all of the custom ribbons are made available to the application.

## Assign custom ribbons to forms or reports

1.  Follow the process described previously to make the customized ribbon available to the application.

2.  Open the form or report in Design view.

3.  On the Design tab, choose **Property Sheet**.

4.  On the **All** tab of the Property window, choose the **Ribbon Name** list and then select a ribbon.

5.  Save, close, and then reopen the form or report. The ribbon UI you selected is displayed.


> [!NOTE]
> The tabs displayed in the ribbon UI are additive. That is, unless you specifically hide the tabs or set the *Start from Scratch* attribute to **True**, the tabs displayed in a form's or report's ribbon user interface are in addition to the existing tabs.

> [!NOTE]
> For more information about the ribbon UI in other Office applications, see [Overview of the Office Fluent Ribbon](https://docs.microsoft.com/office/vba/Library-Reference/Concepts/overview-of-the-office-fluent-ribbon).


