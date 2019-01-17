---
title: RunSavedImportExport macro action
TOCTitle: RunSavedImportExport macro action
ms:assetid: b2449c51-ee20-6e50-87f3-a45adc0b0dde
ms:mtpsurl: https://msdn.microsoft.com/library/Ff822018(v=office.15)
ms:contentKeyID: 48547165
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- vbaac10.chm3022
f1_categories:
- Office.Version=v15
localization_priority: Normal
---

# RunSavedImportExport macro action

**Applies to**: Access 2013, Office 2013

You can use the **RunSavedImportExport** action to run a saved import or export specification that you created by using the Import Wizard or the Export Wizard.

> [!NOTE]
> This action will not be allowed if the database is not trusted.

## Setting

The **RunSavedImportExport** action has the following argument.

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
<td><p><strong>Saved Import Export Name</strong></p></td>
<td><p>Select the name of a saved import or export specification from the drop-down list.</p></td>
</tr>
</tbody>
</table>


## Remarks

- This macro action has the same effect as performing the following procedure in Access:
    
  1.  On the **External Data** tab, click either **Saved Imports** or **Saved Exports**.
    
  2.  In the **Manage Data Tasks** dialog box, on the **Saved Imports** or **Saved Exports** tab (depending on your choice in the preceding step), click the specification that you want to run.
    
  3.  Click **Run**.

- Before running the **RunSavedImportExport** action, make sure that the source and destination files exist, the source data is ready for importing, and that the operation will not accidentally overwrite any data in your destination file.

- Find links to more information about saving and running import and export specifications in the **See Also** section.

- If the saved import or export specification you choose for the **Saved Import Export Name** argument is deleted after the macro is created, Access displays the following error message when the macro is run: **The specification with the specified index does not exist. Specify a different index. '*****specification name*****'.**

