---
title: SaveObject Macro Action
TOCTitle: SaveObject Macro Action
ms:assetid: 85716dfc-f76f-ca47-cc40-f8f88162f85a
ms:mtpsurl: https://msdn.microsoft.com/library/Ff196789(v=office.15)
ms:contentKeyID: 48546060
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- vbaac10.chm116962
f1_categories:
- Office.Version=v15
---

# SaveObject Macro Action


**Applies to**: Access 2013 | Office 2013

You can use the **SaveObject** action to save either a specified Access object or the active object if none is specified. You can also save the active object with a new name in some cases (this functions the same as the **Save As** command on the **Quick Access Toolbar**).


> [!NOTE]
> <P>This action will not be allowed if the database is not trusted. For more information about enabling macros, see the links in the See Also section of this article.</P>



## Setting

The **SaveObject** action has the following arguments.

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
<td><p><strong>Object Type</strong></p></td>
<td><p>The type of object you want to save. Click <strong>Table</strong>, <strong>Query</strong>, <strong>Form</strong>, <strong>Report</strong>, <strong>Macro</strong>, <strong>Module</strong>, <strong>Data Access Page</strong>, <strong>Server View</strong>, <strong>Diagram</strong>, <strong>Stored Procedure</strong>, or <strong>Function</strong> in the <strong>Object Type</strong> box in the <strong>Action Arguments</strong> section of the Macro Builder pane. To select the active object, leave this argument blank. If you select an object type in this argument, you must select an existing object's name in the <strong>Object Name</strong> argument.</p></td>
</tr>
<tr class="even">
<td><p><strong>Object Name</strong></p></td>
<td><p>The name of the object to be saved. The <strong>Object Name</strong> box shows all objects in the database of the type selected by the <strong>Object Type</strong> argument. If you leave the <strong>Object Type</strong> argument blank, you can leave this argument blank to save the active object, or, in some cases, enter a new name in this argument to save the active object with this name. If you enter a new name, the name must follow the standard naming conventions for Microsoft Access objects.</p></td>
</tr>
</tbody>
</table>


## Remarks

The **SaveObject** action works on all database objects that the user can explicitly open and save. The specified object must be open for the **SaveObject** action to have any effect on the object. This action has the same effect as selecting an object and then saving it by clicking **Save** on the **Quick Access Toolbar**. Leaving the **Object Type** argument blank and entering a new name in the **Object Name** argument has the same effect as clicking **Save As** on the **Quick Access Toolbar**, and entering a new name for the active object. Using the **SaveObject** action enables you to specify an object to save and to perform a **Save As** command from a macro.


> [!NOTE]
> <P>You can't use the <STRONG>SaveObject</STRONG> action to save any of the following with a new name:</P>



  - A form in Form view or Datasheet view.

  - A report in Print Preview.

  - A module.

  - A server view in Datasheet view or Print Preview.

  - A data access page in Page view.

  - A table in Datasheet view or Print Preview.

  - A query in Datasheet view or Print Preview.

  - A stored procedure in Datasheet view or Print Preview.

The **SaveObject** action, whether it's carried out in a macro run in the current database or in a library database, always saves the specified object or the active object in the database in which the object was created.

If you save the active object with a new name, but the name is the same as the name of an existing object of this type, a dialog box asks if you want to overwrite the existing object. If you've set the **Warnings On** argument of the **SetWarnings** action to **No**, the dialog box isn't displayed and the old object is automatically overwritten.

To run the **SaveObject** action in a Visual Basic for Applications (VBA) module, use the **Save** method of the **DoCmd** object.

