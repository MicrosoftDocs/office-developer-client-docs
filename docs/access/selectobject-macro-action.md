---
title: "SelectObject Macro Action"
 
 
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vbaac10.chm41840
  
localization_priority: Normal
ms.assetid: a90539a0-c5a0-e997-9c25-e0972d28f2a6

description: "You can use the SelectObject action to select a specified database object."
---

# SelectObject Macro Action

You can use the **SelectObject** action to select a specified database object. 
  
## Setting

The **SelectObject** action has the following arguments. 
  
|**Action argument**|**Description**|
|:-----|:-----|
|**Object Type** <br/> |The type of database object to select. Click **Table**, **Query**, **Form**, **Report**, **Macro**, **Module**, **Data Access Page**, **Server View**, **Diagram**, **Stored Procedure**, or **Function** in the **Object Type** box in the **Action Arguments** section of the Macro Builder pane. This is a required argument.  <br/> |
|**Object Name** <br/> | The name of the object to select. The **Object Name** box shows all objects in the database of the type selected by the **Object Type** argument. This is a required argument, unless you set the In Navigation Pane argument to **Yes**.  <br/> > [!NOTE]> The object names for **Server View**, **Diagram**, or **Stored Procedure** objects are not displayed in the **Object Name** box of an Access project (.adp).           |
|**In Navigation Pane** <br/> |Specifies whether Microsoft Access selects the object in the Navigation Pane. Click **Yes** (to select the object in the Navigation Pane) or **No** (not to select the object in the Navigation Pane). The default is **No**.  <br/> |
   
## Remarks

The **SelectObject** action works with any Access object that can receive the focus. This action gives the specified object the focus and shows the object if it's hidden. If the object is a form, the **SelectObject** action sets the form's **Visible** property to **Yes** and returns the form to the mode set by its form properties (for example, as a modal or pop-up form). 
  
 If the object isn't open in one of the other Access windows, you can select it in the Navigation Pane by setting the **In Navigation Pane** argument to **Yes**. If you set the **In Navigation Pane** argument to **No**, an error message appears when you try to select an object that isn't open. 
  
Often, you might use this action to select an object on which you want to perform additional actions. For example, if you have Access configured to use overlapping windows instead of tabbed documents, you may want to restore an object that has been minimized (by using the **RestoreWindow** action) or maximize a window that contains an object you want to work with (by using the **MaximizeWindow** action). 
  
If you select a form, you can use the **GoToControl**, **GoToRecord**, and **GoToPage** actions to move to specific areas on the form. The **GoToRecord** action also works for datasheets. 
  
To run the **SelectObject** action in a Visual Basic for Applications (VBA) module, use the **SelectObject** method of the **DoCmd** object. 
  

