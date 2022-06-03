---
title: Apply a custom ribbon when starting Access
TOCTitle: Apply a custom ribbon when starting Access
description: How to apply customized ribbons when opening a database in Access 2013. 
ms:assetid: 9e8ddf95-35aa-4e57-8422-d770da14711e
ms:mtpsurl: https://msdn.microsoft.com/library/Ff198313(v=office.15)
ms:contentKeyID: 48546659
ms.date: 10/16/2018
mtps_version: v=office.15
ms.localizationpriority: high
---

# Apply a custom ribbon when starting Access

**Applies to:** Access 2013 | Office 2013

The ribbon uses text-based, declarative XML markup that simplifies creating and customizing the ribbon. With a few lines of XML, you can create just the right interface for the user. Access provides tremendous flexibility in customizing the ribbon UI. For example, customization markup can be stored in a table, embedded in a VBA procedure, stored in another Access database, or linked to from an Excel worksheet. This topic describes how to apply customized ribbons when opening a database.

## Make the ribbon customization XML available

### Store ribbon extensibility XML in a table

One method that you can use to make ribbon customizations available is to store them in a table. If you store the customizations in a table named **USysRibbons**, the customizations can be implemented without using macros or VBA code.

**USysRibbons** is a user-created system table. The table must be created using specific column names for the ribbon customizations to be implemented. 

The following table lists the settings to use when creating the **USysRibbons** table.

<table>
<colgroup>
<col />
<col />
<col />
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

You can use the **[LoadCustomUI](/office/vba/api/Access.Application.LoadCustomUI)** method to load ribbon customizations programmatically. Typically, to create and make the ribbon available to the application, you first create a module in the database with a procedure that calls the **LoadCustomUI** method, passing in the name of the ribbon and the XML customization markup.

The XML markup can come from a **Recordset** object created from a table, from a source external to the database such as an XML file that you parse into a string, or from XML markup embedded directly inside the procedure. You can make different ribbons using multiple calls to the **LoadCustomUI** method, passing in different XML markup as long as the name of each ribbon and the **id** attribute of the tabs that make up the ribbon are unique.

After the procedure is complete, you then create an AutoExec macro that calls the procedure by using the RunCode action. That way, when the application is started, the **LoadCustomUI** method is automatically executed, and all of the custom ribbons are made available to the application.

## Apply customized ribbons when Access starts

To apply a custom UI so that it is available when the application starts, use the following procedure:

1.  Follow the process described previously to make the customized ribbons available to the application.

2.  Close and then restart the application.

3.  Choose the **Microsoft Office Button**![O12FileMenuButton\_ZA10077102](media/access-file-menu-button.gif "O12FileMenuButton_ZA10077102") and then choose **Access Options**.

4.  Choose the **Current Database** option and then, in the **Ribbon and Toolbar Options** section, choose the **Ribbon Name** list and select a ribbon.

5.  Now close and restart the application. The UI you selected is displayed.

> [!NOTE]
> For more information about the ribbon UI in other Office applications, see [Overview of the Office Fluent Ribbon](/office/vba/Library-Reference/Concepts/overview-of-the-office-fluent-ribbon).
