---
title: "OpenForm Macro Action"
 
 
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: c519a9d7-99d4-4765-ad96-59c3fe1be9e3

description: "You can use the OpenForm action to open a form in Form view, Design view, Print Preview, or Datasheet view. You can select data entry and window modes for the form and restrict the records that the form displays."
---

# OpenForm Macro Action

You can use the **OpenForm** action to open a form in Form view, Design view, Print Preview, or Datasheet view. You can select data entry and window modes for the form and restrict the records that the form displays. 
  
## Setting

The **OpenForm** action has the following arguments. 
  
|**Action argument**|**Description**|
|:-----|:-----|
|**Form Name** <br/> |The name of the form to open. The **Form Name** box in the **Action Arguments** section of the Macro Builder pane shows all forms in the current database. This is a required argument. If you run a macro containing the **OpenForm** action in a library database, Microsoft Access first looks for the form with this name in the library database, and then in the current database.  <br/> |
|**View** <br/> |The view in which the form will open. Click **Form**, **Design**, **Print Preview**, **Datasheet**, **PivotTable**, or **PivotChart** in the **View** box. The default is **Form**.  <br/> > [!NOTE]> The **View** argument setting overrides the settings of the form's **DefaultView** and **ViewsAllowed** properties. For example, if a form's **ViewsAllowed** property is set to **Datasheet**, you can still use the **OpenForm** action to open the form in Form view.           |
|**Filter Name** <br/> |A filter that restricts or sorts the form's records. You can enter the name of either an existing query or a filter that was saved as a query. However, the query must include all the fields in the form you are opening or have its **OutputAllFields** property set to **Yes**.  <br/> |
|**Where Condition** <br/> |A valid SQL WHERE clause (without the word WHERE) or expression that Access uses to select records from the form's underlying table or query. If you select a filter with the **Filter Name** argument, Access applies this WHERE clause to the results of the filter. To open a form and restrict its records to those specified by the value of a control on another form, use the following expression: **[** *fieldname* **] = Forms![** *formname* **]![** *controlname on other form* **]** Replace  *fieldname*  with the name of a field in the underlying table or query of the form you want to open. Replace  *formname*  and  *controlname on other form*  with the name of the other form and the control on the other form that contains the value you want records in the first form to match.  <br/> > [!NOTE]> The maximum length of the **Where Condition** argument is 255 characters. If you need to enter a more complex SQL WHERE clause longer than this, use the **OpenForm** method of the **DoCmd** object in a Visual Basic for Applications (VBA) module instead. You can enter SQL WHERE clause statements of up to 32,768 characters in VBA.           |
|**Data Mode** <br/> | The data entry mode for the form. This applies only to forms opened in Form view or Datasheet view. Click **Add** (the user can add new records but can't edit existing records), **Edit** (the user can edit existing records and add new records), or **Read Only** (the user can only view records). The default is **Edit**. **Notes** <br/>  The **Data Mode** argument setting overrides the settings of the form's **AllowEdits**, **AllowDeletions**, **AllowAdditions**, and **DataEntry** properties. For example, if a form's **AllowEdits** property is set to **No**, you can still use the **OpenForm** action to open the form in Edit mode.  <br/>  If you leave this argument blank, Access opens the form in the data entry mode set by the form's **AllowEdits**, **AllowDeletions**, **AllowAdditions**, and **DataEntry** properties.  <br/> |
|**Window Mode** <br/> |The window mode in which the form opens. Click **Normal** (the form opens in the mode set by its properties), **Hidden** (the form is hidden), **Icon** (the form opens minimized as a small title bar at the bottom of the screen), or **Dialog** (the form's **Modal** and **PopUp** properties are set to **Yes**). The default is **Normal**.  <br/> > [!NOTE]> Some **Window Mode** argument settings do not apply when using tabbed documents. To switch to overlapping windows:           Click the File tab  and then click Options. In the  Access Options dialog box, click Current Database. In the Application Optionssection, under Document Window Options, click Overlapping Windows. Click OK, then close and reopen the database. |
   
## Remarks

This action is similar to double-clicking a form in the Navigation Pane, or right-clicking the form in the Navigation Pane and then selecting a view.
  
A form can be modal (it must be closed or hidden before the user can perform any other action) or modeless (the user can move to other windows while the form is open). It can also be a pop-up form (a form used to collect or display information that remains on top of all other Access windows). You set the **Modal** and **PopUp** properties when you design the form. If you use **Normal** for the **Window Mode** argument, the form opens in the mode specified by these property settings. If you use **Dialog** for the **Window Mode** argument, these properties are both set to **Yes**. A form opened as hidden or as an icon returns to the mode specified by its property settings when you show or restore it. 
  
When you open a form with the **Window Mode** argument set to **Dialog**, Access suspends the macro until the form is closed or hidden. You can hide a form by setting its **Visible** property to **No** by using the **SetValue** action. 
  
> [!TIP]
> You can select a form in the Navigation Pane and drag it to a macro action row. This automatically creates an **OpenForm** action that opens the form in Form view. 
  
The filter and WHERE condition you apply become the setting of the form's **Filter** property. 
  
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
   
The following macro opens a Product List form in the lower-right corner of the Suppliers form, displaying the current supplier's products. It shows the use of the **Echo**, **MessageBox**, **GoToControl**, **StopMacro**, **OpenForm**, and **MoveAndSizeWindow** actions. It also shows the use of a conditional expression with the **MessageBox**, **GoToControl**, and **StopMacro** actions. This macro should be attached to the Review Products button on the Suppliers form. 
  
 **Synchronize forms by using a macro**
  
|**Condition**|**Action**|**Arguments: Setting**|**Comment**|
|:-----|:-----|:-----|:-----|
||**Echo** <br/> |**Echo On**: **No** <br/> |Stop screen updating while the macro is running.  <br/> |
|IsNull([SupplierID])  <br/> |**MessageBox** <br/> |**Message**: Move to the supplier record whose products you want to see, then click the Review Products button again. **Beep**: **Yes** **Type**: **None** **Title**: Select a Supplier  <br/> |If there is no current supplier on the Suppliers form, display a message.  <br/> |
|...  <br/> |**GoToControl** <br/> |**Control Name**: CompanyName  <br/> |Move focus to the CompanyName control.  <br/> |
|...  <br/> |**StopMacro** <br/> ||Stop the macro.  <br/> |
||**OpenForm** <br/> |**Form Name**: Product List **View**: **Datasheet** **Filter Name**: **Where Condition**: [SupplierID] = [Forms]![Suppliers]![SupplierID] **Data Mode**: **Read Only** **Window Mode**: **Normal** <br/> |Open the Product List form and show the current supplier's products.  <br/> |
||**MoveAndSizeWindow** <br/> |**Right**: 0.7799" **Down**: 1.8"  <br/> |Position the Product List form in the lower right of the Suppliers form.  <br/> |
   

