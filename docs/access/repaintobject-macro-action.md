---
title: "RepaintObject Macro Action"
 
 
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vbaac10.chm195788
  
localization_priority: Normal
ms.assetid: e8fa7d0b-578c-5071-2bd5-b772b48637a5
description: "You can use the RepaintObject action to complete any pending screen updates for a specified database object or for the active database object, if none is specified. Such updates include any pending recalculations for the object's controls."
---

# RepaintObject Macro Action

You can use the **RepaintObject** action to complete any pending screen updates for a specified database object or for the active database object, if none is specified. Such updates include any pending recalculations for the object's controls. 
  
## Setting

The **RepaintObject** action has the following arguments. 
  
|**Action argument**|**Description**|
|:-----|:-----|
|**Object Type** <br/> |The type of object to repaint. Click **Table**, **Query**, **Form**, **Report**, **Macro**, **Module**, **Data Access Page**, **Server View**, **Diagram**, **Stored Procedure**, or **Function** in the **Object Type** box in the **Action Arguments** section of the Macro Builder pane. Leave this argument blank to select the active object.  <br/> |
|**Object Name** <br/> |The name of the object to repaint. The **Object Name** box shows all objects in the database of the type selected by the **Object Type** argument. If you leave the **Object Type** argument blank, leave this argument blank also.  <br/> |
   
## Remarks

Microsoft Access waits to complete pending screen updates until it finishes other pending tasks. With this action, you can force immediate repainting of the controls in the specified object. You can use this action:
  
- When you use the **SetValue** action to change values in a number of controls. Access might not show the changes immediately, especially if other controls (such as calculated controls) depend on values in the changed controls. 
    
- When you want to make sure that the form you are viewing displays data in all of its controls. For example, controls containing OLE objects don't display their data immediately after you open a form.
    
> [!NOTE]
>  This action doesn't cause a requery of the database, so it doesn't show new and changed records or remove deleted records from the object's underlying table or query. Use the **Requery** action to requery the source of the object or one of its controls. Use the **ShowAllRecords** action to display the most recent records and remove any applied filters. >  The **RepaintObject** action doesn't have the same effect as clicking **Refresh** in the **Records** group on the **Home** tab, which shows any changes you or other users have made to the currently displayed records in forms and datasheets. 
  
To run the **RepaintObject** action in a Visual Basic for Applications (VBA) module, use the **RepaintObject** method of the **DoCmd** object. 
  

