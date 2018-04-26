---
title: "GoToControl Macro Action"
 
 
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: caff76dc-7ca8-4f87-8144-89445ed4600d

description: "You can use the GoToControl action to move the focus to the specified field or control in the current record of the open form, form datasheet, table datasheet, or query datasheet. You can use this action when you want a particular field or control to have the focus. This field or control can then be used for comparisons or FindRecord actions. You can also use this action to navigate in a form according to certain conditions. For example, if the user enters No in a Married control on a health insurance form, the focus can automatically skip the Spouse/partner Name control and move to the next control."
---

# GoToControl Macro Action

You can use the **GoToControl** action to move the focus to the specified field or control in the current record of the open form, form datasheet, table datasheet, or query datasheet. You can use this action when you want a particular field or control to have the focus. This field or control can then be used for comparisons or **FindRecord** actions. You can also use this action to navigate in a form according to certain conditions. For example, if the user enters No in a Married control on a health insurance form, the focus can automatically skip the Spouse/partner Name control and move to the next control. 
  
## Setting

> [!NOTE]
>  This action is not available for use with data access pages. 
  
The **GoToControl** action has the following argument. 
  
|**Action argument**|**Description**|
|:-----|:-----|
|**Control Name** <br/> |The name of the field or control where you want the focus. Enter the field or control name in the **Control Name** box in the **Action Arguments** section of the Macro Builder pane. This is a required argument.  <br/> > [!NOTE]> Enter only the name of the field or control in the **Control Name** argument, not the fully qualified identifier, such as Forms!Products![Product ID].           |
   
## Remarks

You cannot use the **GoToControl** action to move the focus to a control on a hidden form. 
  
> [!TIP]
> You can use the **GoToControl** action to move to a subform, which is a type of control. You can then use the **GoToRecord** action to move to a particular record in the subform. You can also move to a control on a subform by using the **GoToControl** action to move first to the subform and then to the control on the subform. 
  
To run the **GoToControl** action in a Visual Basic for Applications (VBA) module, use the **GoToControl** method of the **DoCmd** object. You can also use the **SetFocus** method to move the focus to a control on a form or any of its subforms, or to a field in an open table, query, or form datasheet. 
  
## Examples

 **Set the value of a control by using a macro**
  
The following macro opens the Add Products form from a button on the Suppliers form. It shows the use of the **Echo**, **CloseWindow**, **OpenForm**, **SetValue**, and **GoToControl** actions. The **SetValue** action sets the Supplier ID control on the Products form to the current supplier on the Suppliers form. The **GoToControl** action then moves the focus to the Category ID field, where you can begin to enter data for the new product. This macro should be attached to the Add Products button on the Suppliers form. 
  
|**Action**|**Arguments: Setting**|**Comment**|
|:-----|:-----|:-----|
|**Echo** <br/> |**Echo On**: **No** <br/> |Stop screen updating while the macro is running.  <br/> |
|**CloseWindow** <br/> |**Object Type**: **Form** **Object Name**: Product List **Save**: **No** <br/> |Close Product List form.  <br/> |
|**OpenForm** <br/> |**Form Name**: Products **View**: **Form** **Data Mode**: **Add** **Window Mode**: **Normal** <br/> |Open the Products form.  <br/> |
|**SetValue** <br/> |**Item**: [Forms]![Products]![SupplierID] **Expression**: SupplierID  <br/> |Set the Supplier ID control to the current supplier on the Suppliers form.  <br/> |
|**GoToControl** <br/> |**Control Name**: CategoryID  <br/> |Go to the Category ID control.  <br/> |
   
 **Validate data by using a macro**
  
The following validation macro checks the postal codes entered in a Suppliers form. It shows the use of the **StopMacro**, **MessageBox**, **CancelEvent**, and **GoToControl** actions. A conditional expression checks the country/region and postal code entered in a record on the form. If the postal code is not in the right format for the country/region, the macro displays a message box and cancels saving the record. The macro then returns you to the Postal Code control, where you can correct the error. This macro should be attached to the **BeforeUpdate** property of the Suppliers form. 
  
|**Condition**|**Action**|**Arguments: Setting**|**Comment**|
|:-----|:-----|:-----|:-----|
|IsNull([CountryRegion])  <br/> |**StopMacro** <br/> ||If CountryRegion is **Null**, postal code cannot be validated.  <br/> |
|[CountryRegion] In ("France","Italy","Spain") And Len([Postal Code]) \<\> 5  <br/> |**MessageBox** <br/> |**Message**: The postal code must be 5 characters. **Beep**: **Yes** **Type**: **Information** **Title**: Postal Code Error  <br/> |If the postal code is not 5 characters, display a message.  <br/> |
|...  <br/> |**CancelEvent** <br/> ||Cancel the event.  <br/> |
||**GoToControl** <br/> |**Control Name**: PostalCode  <br/> ||
|[CountryRegion] In ("Australia","Singapore") And Len([Postal Code]) \<\> 4  <br/> |**MessageBox** <br/> |Message: The postal code must be 4 characters. **Beep**: **Yes** **Type**: **Information** **Title**: Postal Code Error  <br/> |If the postal code is not 4 characters, display a message.  <br/> |
|...  <br/> |**CancelEvent** <br/> ||Cancel the event.  <br/> |
||**GoToControl** <br/> |**Control Name**: PostalCode  <br/> ||
|([CountryRegion] = "Canada") And ([Postal Code] Not Like"[A-Z][0-9][A-Z] [0-9][A-Z][0-9]")  <br/> |**MessageBox** <br/> |**Message**: The postal code is not valid. Example of Canadian code: H1J 1C3 **Beep**: **Yes** **Type**: **Information** **Title**: Postal Code Error  <br/> |If the postal code is not correct for Canada, display a message. (Example of Canadian code: H1J 1C3)  <br/> |
|...  <br/> |**CancelEvent** <br/> ||Cancel the event.  <br/> |
   

