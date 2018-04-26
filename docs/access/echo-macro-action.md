---
title: "Echo Macro Action"
  
  
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 38dfb2cf-8db5-44b3-91fa-e490932b940b
description: "You can use the Echo action to specify whether echo is turned on. For example, you can use this action to hide or show the results of a macro while it runs."
---

# Echo Macro Action

You can use the **Echo** action to specify whether echo is turned on. For example, you can use this action to hide or show the results of a macro while it runs. 
  
## Setting

> [!NOTE]
> This action will not be allowed if the database is not trusted. For more information about enabling macros, see the links in the **See Also** section of this article. 
  
The **Echo** action has the following arguments. 
  
|**Action argument**|**Description**|
|:-----|:-----|
|**Echo On** <br/> |Click **Yes** (turn echo on) or **No** (turn echo off) in the **Echo On** box in the **Action Arguments** section of the Macro Builder pane. The default is **Yes**.  <br/> |
|**Status Bar Text** <br/> |The text to display in the status bar when echo is turned off. For example, when echo is turned off, the status bar can display "The macro is running."  <br/> |
   
When runs a macro, screen updating often shows information not essential to the functioning of the macro. When you set the **Echo On** argument to **No**, the macro runs without updating the screen. When the macro finishes, Access automatically turns echo back on and repaints the window. The **No** setting for the **Echo On** argument doesn't affect the functionality of the macro or its results. 
  
The **Echo** action doesn't suppress the display of modal dialog boxes, such as error messages, or pop-up forms, such as property sheets. You can use dialog boxes and pop-up forms to gather or display information, even if echo is turned off. To suppress all message or dialog boxes except error message boxes and dialog boxes that require the user to enter information, use the **SetWarnings** action. 
  
You can run the **Echo** action more than once in a macro. This allows you to change the status bar text while the macro runs. 
  
If you turn echo off, you can use the **DisplayHourglassPointer** action to change the mouse pointer into an hourglass icon (or whatever mouse pointer icon you've set for "Busy") to provide a visual indication that the macro is running. 
  
To run the **Echo** action in a Visual Basic for Applications (VBA) module, use the **Echo** method of the **DoCmd** object. 
  
## Examples

 **Set the value of a control by using a macro**
  
The following macro opens the Add Products form from a button on the Suppliers form. It shows the use of the **Echo**, **CloseWindow**, **OpenForm**, **SetValue**, and **GoToControl** actions. The **SetValue** action sets the Supplier ID control on the Products form to the current supplier on the Suppliers form. The **GoToControl** action then moves the focus to the Category ID field, where you can begin to enter data for the new product. This macro should be attached to the Add Products button on the Suppliers form. 
  
|**Action**|**Arguments: Setting**|**Comment**|
|:-----|:-----|:-----|
|**Echo** <br/> |**Echo On**: **No** <br/> |Stop screen updating while the macro is running.  <br/> |
|**CloseWindow** <br/> |**Object Type**: **Form** **Object Name**: Product List **Save**: **No** <br/> |Close the Product List form.  <br/> |
|**OpenForm** <br/> |**Form Name**: Products **View**: **Form** **Data Mode**: **Add** **Window Mode**: **Normal** <br/> |Open the Products form.  <br/> |
|**SetValue** <br/> |**Item**: [Forms]![Products]![SupplierID] **Expression**: SupplierID  <br/> |Set the Supplier ID control to the current supplier on the Suppliers form.  <br/> |
|**GoToControl** <br/> |**Control Name**: CategoryID  <br/> |Go to the Category ID control.  <br/> |
   
 **Synchronize forms by using a macro**
  
The following macro opens the Product List form in the lower-right corner of the Suppliers form, displaying the current supplier's products. It shows the use of the **Echo**, **MessageBox**, **GoToControl**, **StopMacro**, **OpenForm**, and **MoveAndSizeWindow** actions. It also shows the use of a conditional expression with the **MessageBox**, **GoToControl**, and **StopMacro** actions. This macro should be attached to the Review Products button on the Suppliers form. 
  
|**Condition**|**Action**|**Arguments: Setting**|**Comment**|
|:-----|:-----|:-----|:-----|
||**Echo** <br/> |**Echo On**: **No** <br/> |Stop screen updating while the macro is running.  <br/> |
|IsNull([Supplier ID])  <br/> |**MessageBox** <br/> |**Message**: Move to the supplier record whose products you want to see, then click the Review Products button again. **Beep**: **Yes** **Type**: **None** **Title**: Select a Supplier  <br/> |If there is no current supplier on the Suppliers form, display a message.  <br/> |
|...  <br/> |**GoToControl** <br/> |**Control Name**: CompanyName  <br/> |Move focus to the CompanyName control.  <br/> |
|...  <br/> |**StopMacro** <br/> ||Stop the macro.  <br/> |
||**OpenForm** <br/> |**Form Name**: Product List **View**: **Datasheet** **Filter Name**: **Where Condition**: [Supplier ID] = [Forms]![Suppliers]![SupplierID] **Data Mode**: **Read Only** **Window Mode**: **Normal** <br/> |Open the Product List form and show the current supplier's products.  <br/> |
||**MoveAndSizeWindow** <br/> |**Right**: 0.7799" **Down**: 1.8"  <br/> |Position the Product List form in the lower right of the Suppliers form.  <br/> |
   

