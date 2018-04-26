---
title: "SetValue Macro Action"
 
 
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: a08be0c1-a053-45f9-b4ae-709fedc58e8b

description: "You can use the SetValue action to set the value of a Microsoft Access field, control, or property on a form, a form datasheet, or a report."
---

# SetValue Macro Action

You can use the **SetValue** action to set the value of a Microsoft Access field, control, or property on a form, a form datasheet, or a report. 
  
> [!NOTE]
> You cannot use the **SetValue** action to set the value of an Access property that returns an object. 
  
> [!NOTE]
> This action will not be allowed if the database is not trusted. For more information about enabling macros, see the links in the **See Also** section of this article. 
  
## Setting

The **SetValue** action has the following arguments. 
  
|**Action argument**|**Description**|
|:-----|:-----|
|**Item** <br/> |The name of the field, control, or property whose value you want to set. Enter the field, control, or property name in the **Item** box in the **Action Arguments** section of the Macro Builder pane. You must use the full syntax to refer to this item, such as  *controlname*  (for a control on the form or report from which the macro was called) or **Forms**! *formname*  !  *controlname*  . This is a required argument.  <br/> |
|**Expression** <br/> |The expression Access uses to set the value for this item. You must always use the full syntax to refer to any objects in the expression. For example, to increase the value in a Salary control on an Employees form by 10 percent, use  `Forms!Employees!Salary*1.1.` This is a required argument.  <br/> > [!NOTE]> You shouldn't use an equal sign ( **=** ) before the expression in this argument. If you do, Access evaluates the expression and then uses this value as the expression in this argument. This can produce unexpected results if the expression is a string.            For example, if you type **="String1"** for this argument, Access first evaluates the expression as String1. Then it uses String1 as the expression in this argument, expecting to find a control or property named String1 on the form or report that called the macro.  <br/> |
   
> [!NOTE]
> In an Access database (.mdb or .accdb), click the **Build** button to use the Expression Builder to create an expression for either of these arguments. 
  
## Remarks

You can use this action to set a value for a field or control on a form, a form datasheet, or a report. You can also set the value for almost all control, form, and report properties in any view. To find out whether a particular property can be set by using a macro and which views it can be set in, see the Help topic for that property in the Visual Basic Editor.
  
You can also set the value for a field in a form's underlying table even if the form doesn't contain a control bound to the field. Use the syntax **Forms**! *formname*  !  *fieldname*  in the **Item** box to set the value for such a field. You can also refer to a field in a report's underlying table by using the syntax **Reports**! *reportname*  !  *fieldname*  , but there must be a control on the report bound to this field, or the field must be referred to in a calculated control on the report. 
  
If you set the value of a control on a form, the **SetValue** action doesn't trigger the control's form-level validation rules, but it does trigger the underlying field's table-level validation rules if the control is a bound control. The **SetValue** action also triggers recalculation, but the recalculation may not happen immediately. To trigger immediate repainting and force the recalculation to completion, use the **RepaintObject** action. The value you set in a control by using the **SetValue** action is also not affected by an input mask set in the control's or underlying field's **InputMask** property. 
  
To change the value of a control, you can use the **SetValue** action in a macro specified by the control's **AfterUpdate** event property. However, you can't use the **SetValue** action in a macro specified by a control's **BeforeUpdate** event property to change the value of the control (although you can use the **SetValue** action to change the value of other controls). You can also use the **SetValue** action in a macro specified by the **BeforeUpdate** or **AfterUpdate** property of a form to change the value of any controls in the current record. 
  
> [!NOTE]
>  You can't use the **SetValue** action to set the value of the following controls: >  Bound controls and calculated controls on reports. >  Calculated controls on forms. 
  
> [!TIP]
> You can use the **SetValue** action to hide or show a form in Form view. Enter **Forms**! *formname* **.Visible** in the **Item** box and **No** or **Yes** in the **Expression** box. Setting a modal form's **Visible** property to **No** hides the form and makes it modeless. Setting the property to **Yes** displays the form and makes it modal again. 
  
Changing the value of or adding new data in a control by using the **SetValue** action in a macro doesn't trigger events such as **BeforeUpdate**, **BeforeInsert**, or **Change** that occur when you change or enter data in these controls in the user interface. These events also don't occur if you set the value of the control by using a Visual Basic for Applications (VBA) module. 
  
This action isn't available in a VBA module. Set the value directly in VBA.
  
## Example

 **Set the value of a control by using a macro**
  
The following macro opens the Add Products form from a button on the Suppliers form. It shows the use of the **Echo**, **CloseWindow**, **OpenForm**, **SetValue**, and **GoToControl** actions. The **SetValue** action sets the SupplierID control on the Products form to the current supplier on the Suppliers form. The **GoToControl** action then moves the focus to the CategoryID field, where you can begin to enter data for the new product. This macro should be attached to the Add Products button on the Suppliers form. 
  
|**Action**|**Arguments: Setting**|**Comment**|
|:-----|:-----|:-----|
|**Echo** <br/> |**Echo On**: **No** <br/> |Stop screen updating while the macro is running.  <br/> |
|**CloseWindow** <br/> |**Object Type**: **Form** **Object Name**: Product List **Save**: **No** <br/> |Close the Product List form.  <br/> |
|**OpenForm** <br/> |**Form Name**: Products **View**: **Form** **Data Mode**: **Add** **Window Mode**: **Normal** <br/> |Open the Products form.  <br/> |
|**SetValue** <br/> |**Item**: [Forms]![Products]![SupplierID] **Expression**: SupplierID  <br/> |Set the SupplierID control to the current supplier on the Suppliers form.  <br/> |
|**GoToControl** <br/> |**Control Name**: CategoryID  <br/> |Go to the CategoryID control.  <br/> |
   

