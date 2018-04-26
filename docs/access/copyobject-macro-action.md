---
title: "CopyObject Macro Action"
  
  
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
 
f1_keywords:
- vbaac10.chm12836
  
localization_priority: Normal
ms.assetid: 746f61df-d5db-284a-0897-75820c2be11f
description: "You can use the CopyObject action to copy the specified database object to a different Access database or to the same database or Access project under a new name. For example, you can copy or back up an existing object in another database or quickly create a similar object with a few changes."
---

# CopyObject Macro Action

You can use the **CopyObject** action to copy the specified database object to a different Access database or to the same database or Access project under a new name. For example, you can copy or back up an existing object in another database or quickly create a similar object with a few changes. 
  
> [!NOTE]
> This action will not be allowed if the database is not trusted. For more information about enabling macros, see the links in the **See Also** section of this article. 
  
## Setting

The **CopyObject** action has the following arguments. 
  
|**Action argument**|**Description**|
|:-----|:-----|
|**Destination Database** <br/> |A valid path and file name for the destination database. Enter the path and file name in the **Destination Database** box in the **Action Arguments** section of the Macro Builder pane. Leave this argument blank if you want to select the current database.  <br/> > [!NOTE]> This argument is only available in the Access database environment. When using this action in an Access project environment (.adp), the Destination Database argument must be blank.           If you run a macro containing the **CopyObject** action in a library database and leave this argument blank, Microsoft Office Access 2007 will copy the object into the library database.  <br/> |
|**New Name** <br/> |A new name for the object. When copying to a different database, leave this argument blank to keep the same name.  <br/> |
|**Source Object Type** <br/> |The object type you want to copy. Click **Table**, **Query**, **Form**, **Report**, **Macro**, **Module**, **Data Access Page**, **Server View**, **Diagram**, **Stored Procedure**, or **Function**. To copy the object selected in the Navigation Pane, leave this argument blank.  <br/> |
|**Source Object Name** <br/> |The name of the object to be copied. The **Source Object Name** box shows all objects in the database of the type selected by the **Source Object Type** argument. In the **Source Object Name** box, click the object to copy. If you leave the **Source Object Type** argument blank, leave this argument blank also. If you run a macro containing the **CopyObject** action in a library database, Access first looks for the object with this name in the library database, and then in the current database.  <br/> |
   
## Remarks

You must enter a value for either one or both of the **Destination Database** and **New Name** arguments for this action. 
  
If you leave the **Source Object Type** and **Source Object Name** arguments blank, Access copies the object selected in the Navigation Pane. To select an object in the Navigation Pane, you can use the **SelectObject** action with the In Navigation Pane argument set to **Yes**. 
  
The **CopyObject** action is similar to performing the following steps manually: 
  
1. Select an object in the Navigation Pane.
    
2. On the **Home** tab, in the **Clipboard** group, click **Copy**. 
    
3. On the same tab, click **Paste**.The **Paste As** dialog box appears so that you can give the object a new name. The **CopyObject** action performs all of these steps automatically. 
    
> [!NOTE]
>  When copying data access pages, the **CopyObject** action copies only the link to the associated .htm file, not the file itself. 
  
The path and file name of the destination database must exist before the macro runs the **CopyObject** action. If they don't exist, Access displays an error message. 
  
To run the **CopyObject** action in a Visual Basic for Applications (VBA) module, use the **CopyObject** method of the **DoCmd** object. 
  
 You can also manually copy an object selected in the Navigation Pane, or an object that is currently open, by clicking the **File** tab and then clicking **Save As**. This command will make a copy of the object in the current database only. In the **Save As** dialog box, enter the name for the copy, and choose what type of object you want to save it as. If the original object has already been saved and you save it in the current database with a new name, the original version still exists with its old name. 
  
To manually copy an object to a different Access database:
  
1. On the **External Data** tab, in the **Export** group, click **More** and then click **Access Database**.
    
2. In the **Export - Access Database** dialog box, enter the file name of the destination database.-or-Click **Browse** to display the **File Save** dialog box, locate the destination database, and then click **Save**.
    
3. In the **Export - Access Database** dialog box, click **OK**. The **Export** dialog box appears. 
    
4. In the **Export** dialog box, enter a name for the object in the destination database. Choose any applicable options, such as **Export Definition and Data** or **Definition Only** for tables. When you are finished, click **OK**.
    

