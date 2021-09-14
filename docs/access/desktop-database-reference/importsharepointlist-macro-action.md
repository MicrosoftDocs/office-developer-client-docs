---
title: ImportSharePointList macro action
TOCTitle: ImportSharePointList macro action
ms:assetid: 6a633d7d-d81d-0e2e-6c1c-706a552c1bf2
ms:mtpsurl: https://msdn.microsoft.com/library/Ff195403(v=office.15)
ms:contentKeyID: 48545429
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- vbaac10.chm152234
f1_categories:
- Office.Version=v15
ms.localizationpriority: medium
---

# ImportSharePointList macro action

**Applies to**: Access 2013, Office 2013

You can use the **ImportSharePointList** action to import or link data from a Microsoft SharePoint Foundation site.

> [!NOTE]
> This action will not be allowed if the database is not trusted. 

## Setting

The **ImportSharePointList** action has the following arguments.

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
<td><p><strong>Transfer Type</strong></p></td>
<td><p>Select the type of transfer.</p>
<ul>
<li><p>Select <strong>Import</strong> to copy the SharePoint Foundation data into a table in Microsoft Access. Updates to the data in Access do not affect the data in SharePoint Foundation. Likewise, updates to the data in SharePoint Foundation do not affect the data in Access.</p></li>
<li><p>Select <strong>Link</strong> to create a linked table in Access that links to the data in SharePoint Foundation. Updates to the data in Access are reflected in SharePoint Foundation. Likewise, updates to the data in SharePoint Foundation are reflected in Access.</p></li>
</ul>
<p></p></td>
</tr>
<tr class="even">
<td><p><strong>Site Address</strong></p></td>
<td><p>Enter the full path of the SharePoint site.</p></td>
</tr>
<tr class="odd">
<td><p><strong>List ID</strong></p></td>
<td><p>Enter the name or GUID of the list to be transferred. Required argument.</p></td>
</tr>
<tr class="even">
<td><p><strong>View ID</strong></p></td>
<td><p>Enter the GUID of the view for the list you want to use. Leave this argument blank to transfer all rows and columns in the list.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Table Name</strong></p></td>
<td><p>Enter the name you want displayed for the table or linked table in Access.</p></td>
</tr>
<tr class="even">
<td><p><strong>Get Lookup Display Values</strong></p></td>
<td><p>Select <strong>Yes</strong> to transfer display values for Lookup fields instead of the ID used to perform the lookup.</p></td>
</tr>
</tbody>
</table>


## Remarks

- This action has the same effect as clicking **SharePoint List** in the **Import** group on the **External Data** tab. The arguments for the action correspond to the choices you make in the Get External Data Wizard.

- To run the **ImportSharePointList** action in a VBA module, use the **TransferSharePointList** method of the **DoCmd** object.

- If you specify a nonexistent list or view, no error occurs, and no data is transferred.

- A GUID is a unique hexadecimal identifier for a list or a view. A GUID must be entered in the following format, where each "F" is a hexadecimal number (0 through 9 or A through F).
    
  `{FFFFFFFF-FFFF-FFFF-FFFF-FFFFFFFFFFFF}`
    
  You can obtain the GUID for a list or view from the SharePoint site by using the following procedure:
    
  1. Open the list in SharePoint Foundation.
    
  2. If the view you want is not displayed, click the **View** drop-down arrow and then select the view you want.
    
  3. Click the **View** drop-down arrow and then select **Modify this View**.The address in the browser's address bar contains the GUIDs for both the list and the view. The GUID for the list follows **List=**, and the GUID for the view follows **View=**. However, in the address, each **{** (left brace) character is represented by the string **%7B**, each **-** (hyphen) character is represented by the string **%2D**, and each **}** (right brace) character is represented by the string **%7D**. For example:
        
     `https://MySite12/_layouts/ViewEdit.aspx?List=%7B2A82A404%2D5529%2D47DC%2DAE13%2DAC1D9BC0A84F%7D&View=%7B357B4FE6%2D44CF%2D4275%2DB91F%2D46558301579B%7D`
        
  Before you can use the GUIDs from the address as arguments in this macro action, you must replace each **%7B** string with the **{** character, replace each **%2D** string with the **-** character, and replace each **%7D** string with the **}** character. Do not include the **&** (ampersand) character that follows the **%7D** string in the list GUID.

