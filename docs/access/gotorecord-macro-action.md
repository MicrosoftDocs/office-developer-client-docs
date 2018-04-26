---
title: "GoToRecord Macro Action"
 
 
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vbaac10.chm58124
  
localization_priority: Normal
ms.assetid: 76f936de-739b-63be-9b28-5b0e111408e6

description: "You can use the GoToRecord action to make the specified record the current record in an open table, form, or query result set."
---

# GoToRecord Macro Action

You can use the **GoToRecord** action to make the specified record the current record in an open table, form, or query result set. 
  
## Setting

The **GoToRecord** action has the following arguments. 
  
|**Action argument**|**Description**|
|:-----|:-----|
|**Object Type** <br/> |The type of object that contains the record you want to make current. Click **Table**, **Query**, **Form**, **Server View**, **Stored Procedure**, or **Function** in the **Object Type** box in the **Action Arguments** section of the Macro Builder pane. Leave this argument blank to select the active object.  <br/> |
|**Object Name** <br/> |The name of the object that contains the record you want to make the current record. The **Object Name** box shows all objects in the current database of the type selected by the **Object Type** argument. If you leave the **Object Type** argument blank, leave this argument blank also.  <br/> |
|**Record** <br/> |The record to make the current record. Click **Previous**, **Next**, **First**, **Last**, **Go To**, or **New** in the **Record** box. The default is **Next**.  <br/> |
|**Offset** <br/> | An integer or expression that evaluates to an integer. An expression must be preceded by an equal sign ( **=** ). This argument specifies the record to make the current record. You can use the **Offset** argument in two ways:  <br/>  When the **Record** argument is **Next** or **Previous**, Microsoft Office Access 2007 moves the number of records forward or backward specified in the **Offset** argument.  <br/>  When the **Record** argument is **Go To**, Access moves to the record with the number equal to the **Offset** argument. The record number is shown in the record number box at the bottom of the window.  <br/> > [!NOTE]>  If you use the **First**, **Last**, or **New** setting for the **Record** argument, Access ignores the **Offset** argument. If you enter an **Offset** argument that is too large, Access displays an error message. You can't enter negative numbers for the **Offset** argument.            When the **Record** argument is **Next** or **Previous**, Microsoft Office Access 2007 moves the number of records forward or backward specified in the **Offset** argument.  <br/>  When the **Record** argument is **Go To**, Access moves to the record with the number equal to the **Offset** argument. The record number is shown in the record number box at the bottom of the window.  <br/> |
   
## Remarks

If the focus is in a particular control in a record, this action leaves it in the same control for the new record.
  
You can use the **New** setting for the **Record** argument to move to the blank record at the end of a form or table so you can enter new data. 
  
This action is similar to clicking the arrow below the **Find** button on the **Home** tab and then clicking **Go To**. The **First**, **Last**, **Next**, **Previous**, and **New Record** subcommands of the **Go To** command have the same effect on the selected object as the **First**, **Last**, **Next**, **Previous**, and **New** settings for the **Record** argument. You can also move to records by using the navigation buttons at the bottom of the window. 
  
You can use the **GoToRecord** action to make a record on a hidden form the current record if you specify the hidden form in the **Object Type** and **Object Name** arguments. 
  
To run the **GoToRecord** action in a Visual Basic for Applications (VBA) module, use the **GoToRecord** method of the **DoCmd** object. 
  

