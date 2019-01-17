---
title: Hide the ribbon when Access starts
TOCTitle: Hide the ribbon when Access starts
description: How to load a customized ribbon that hides all of the built-in tabs in Access 2013.
ms:assetid: f98bab58-8094-1c56-f70b-ced2e7849574
ms:mtpsurl: https://msdn.microsoft.com/library/Ff837012(v=office.15)
ms:contentKeyID: 48548817
ms.date: 10/16/2018
mtps_version: v=office.15
localization_priority: Priority
---

# Hide the ribbon when Access starts

**Applies to:** Access 2013 | Office 2013

By default, Microsoft Access does not provide a method for hiding the ribbon. This topic describes how to load a customized ribbon that hides all of the built-in tabs.

To load the customized ribbon when Access starts, you should store its settings in a table named **USysRibbons**.

The **USysRibbons** table must be created using specific column names for the ribbon customizations to be implemented. 

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

<br/>

The following table lists the ribbon customization settings to store in the **USysRibbons** table.

|Column name|Value|
|:----------|:----|
|**RibbonName**|HideTheRibbon|
|**RibbonXML**|`<CustomUI xmlns="https://schemas.microsoft.com/office/2006/01/CustomUI"> <ribbon startFromScratch="true"/></CustomUI>`|


## Apply a custom ribbon when Access starts

To apply a custom ribbon so that it is available when the application starts, use the following procedure:

1.  Follow the process described previously to make the customized ribbon available to the application.

2.  Close and then restart the application.

3.  Choose the **Microsoft Office Button**![O12FileMenuButton\_ZA10077102](media/access-file-menu-button.gif "O12FileMenuButton_ZA10077102"), and then choose **Access Options**.

4.  Choose the **Current Database** option and then, in the **Ribbon and Toolbar Options** section, choose the **Ribbon Name** list and select **HideTheRibbon**.

5.  Close and then restart the application.

> [!NOTE]
> For more information about the ribbon UI in other Office applications, see [Overview of the Office Fluent Ribbon](https://docs.microsoft.com/office/vba/Library-Reference/Concepts/overview-of-the-office-fluent-ribbon).


