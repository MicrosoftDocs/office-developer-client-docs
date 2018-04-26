---
title: "MoveAndSizeWindow Macro Action"
 
 
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 86bcf45f-90ce-4ca2-a7fb-efbe5347d137
description: "If you have set your document window options to use overlapping windows instead of tabbed documents, you can use the MoveAndSizeWindow action to move or resize the active window. For information on how to set document window options, see the Remarks section."
---

# MoveAndSizeWindow Macro Action

If you have set your document window options to use overlapping windows instead of tabbed documents, you can use the **MoveAndSizeWindow** action to move or resize the active window. For information on how to set document window options, see the Remarks section. 
  
## Setting

The **MoveAndSizeWindow** action has the following arguments. 
  
|**Action argument**|**Description**|
|:-----|:-----|
|**Right** <br/> |The new horizontal position of the window's upper-left corner, measured from the left edge of its containing window. Enter the position in the **Right** box in the **Action Arguments** section of the Macro Builder pane.  <br/> |
|**Down** <br/> |The new vertical position of the window's upper-left corner, measured from the top edge of its containing window.  <br/> |
|**Width** <br/> |The window's new width.  <br/> |
|**Height** <br/> |The window's new height.  <br/> |
   
If you leave an argument blank, Microsoft Access uses the window's current setting.
  
You must enter a value for at least one argument.
  
> [!NOTE]
> Each measurement is in inches or centimeters, depending on the regional settings in Windows Control Panel. 
  
## Remarks

To set up an application to use overlapping windows instead of tabbed documents, use the following procedure:
  
1.  and then click **Options**
    
2. Click **Current Database**.
    
3. In the **Application Options** section, under **Document Window Options**, click **Overlapping Windows**.
    
4. Click **OK**, and then close and reopen the database.
    
This action is similar to clicking **Move** or **Size** on the window's **Control** menu. With the menu commands, you use the keyboard's arrow keys to move or resize the window. With the **MoveAndSizeWindow** action, you enter the position and size measurements directly. You can also use the mouse to move and size windows. 
  
You can use this action on any window, in any view.
  
 **Tips**
  
- To move a window without resizing it, enter values for the **Right** and **Down** arguments but leave the **Width** and **Height** arguments blank. 
    
- To resize a window without moving it, enter values for the **Width** and **Height** arguments but leave the **Right** and **Down** arguments blank. 
    
To run the **MoveAndSizeWindow** action in a Visual Basic for Applications (VBA) module, use the **MoveSize** method of the **DoCmd** object. 
  
## Example

 **Synchronize forms by using a macro**
  
The following macro opens a Product List form in the lower-right corner of the Suppliers form, displaying the current supplier's products. It shows the use of the **Echo**, **MessageBox**, **GoToControl**, **StopMacro**, **OpenForm**, and **MoveAndSizeWindow** actions. It also shows the use of a conditional expression with the **MessageBox**, **GoToControl**, and **StopMacro** actions. This macro should be attached to the Review Products button on the Suppliers form. 
  
|**Condition**|**Action**|**Arguments: Setting**|**Comment**|
|:-----|:-----|:-----|:-----|
||**Echo** <br/> |**Echo On**: **No** <br/> |Stop screen updating while the macro is running.  <br/> |
|IsNull([Supplier ID])  <br/> |**MessageBox** <br/> |**Message**: Move to the supplier record whose products you want to see, then click the Review Products button again. **Beep**: **Yes** **Type**: **None** **Title**: Select a Supplier  <br/> |If there is no current supplier on the Suppliers form, display a message.  <br/> |
||**GoToControl** <br/> |**Control Name**: CompanyName  <br/> |Move focus to the CompanyName control.  <br/> |
|...  <br/> |**StopMacro** <br/> ||Stop the macro.  <br/> |
||**OpenForm** <br/> |**Form Name**: Product List **View**: **Datasheet** **Filter Name**: **Where Condition**: [Supplier ID] = [Forms]![Suppliers]![SupplierID] **Data Mode**: **Read Only** **Window Mode**: **Normal** <br/> |Open the Product List form and show the current supplier's products.  <br/> |
||**MoveAndSizeWindow** <br/> |**Right**: 0.7799" **Down**: 1.8"  <br/> |Position the Product List form in the lower right of the Suppliers form.  <br/> |
   

