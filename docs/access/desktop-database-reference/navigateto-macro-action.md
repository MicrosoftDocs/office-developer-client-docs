---
title: NavigateTo macro action
TOCTitle: NavigateTo macro action
ms:assetid: 6594d614-3ea6-7851-b70e-1661d24f8ba0
ms:mtpsurl: https://msdn.microsoft.com/library/Ff195165(v=office.15)
ms:contentKeyID: 48545324
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- vbaac10.chm119055
f1_categories:
- Office.Version=v15
localization_priority: Normal
---

# NavigateTo macro action

**Applies to**: Access 2013, Office 2013

You can use the **NavigateTo** action to control the display of database objects in the Navigation Pane. For example, you can change how the database objects are categorized, and you can filter the objects so that only certain ones are displayed.

## Setting

The **NavigateTo** action has the following arguments.

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
<td><p><strong>Category</strong></p></td>
<td><p>Required. The category by which you want the Navigation Pane to display objects. Click <strong>Object Type</strong>, <strong>Tables and Views</strong>, <strong>Modified Date</strong>, <strong>Created Date</strong>, or <strong>Custom</strong> in the <strong>Category</strong> box.</p></td>
</tr>
<tr class="even">
<td><p><strong>Group</strong></p></td>
<td><p>Optional. The <strong>Group</strong> argument limits which objects in the category appear in the Navigation Pane. If you leave the <strong>Group</strong> argument blank, the Navigation Pane displays all database objects, categorized by the criteria you specify in the <strong>Category</strong> argument. Examples of valid <strong>Group</strong> arguments for the various <strong>Category</strong> arguments are shown in the following table.</p></td>
</tr>
</tbody>
</table>


## Remarks

- This action is similar to selecting categories and groups from the title bar of the navigation pane.

- Valid **Group** arguments depend on which **Category** argument is used. If you enter an invalid **Group** argument, an error message appears.The following table contains examples of valid **Group** arguments for each **Category** argument.
    
  <table>
  <colgroup>
  <col style="width: 50%" />
  <col style="width: 50%" />
  </colgroup>
  <thead>
  <tr class="header">
  <th><p>Category argument</p></th>
  <th><p>Example Group arguments</p></th>
  </tr>
  </thead>
  <tbody>
  <tr class="odd">
  <td><p>Object Type</p></td>
  <td><p>Tables; Forms; Queries; Pages; Macros; Modules</p></td>
  </tr>
  <tr class="even">
  <td><p>Tables and Views</p></td>
  <td><p>Names of specific tables in your database</p></td>
  </tr>
  <tr class="odd">
  <td><p>Modified Date</p></td>
  <td><p>Today; Yesterday; Last Month; Older</p></td>
  </tr>
  <tr class="even">
  <td><p>Created Date</p></td>
  <td><p>Today; Yesterday; Last Month; Older</p></td>
  </tr>
  <tr class="odd">
  <td><p>Custom category</p></td>
  <td><p>Names of groups you have created for the specified custom category</p></td>
  </tr>
  </tbody>
  </table>

- To run the **NavigateTo** action in a VBA module, use the **NavigateTo** method of the **DoCmd** object.

> [!NOTE]
> To navigate to the top level of a category (for example, **All Tables**, **All Access Objects**, or **All Dates**), you must leave the Group argument blank. For example, when the **Category** argument is **Object Type**, entering **All Access Objects** as a **Group** argument results in an error.


