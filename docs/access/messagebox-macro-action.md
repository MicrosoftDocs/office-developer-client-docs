---
title: "MessageBox Macro Action"
 
 
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 326a0e68-38fb-4f81-b319-5a70caa5aec4

---

# MessageBox Macro Action

## 

You can use the **MessageBox** action to display a message box containing a warning or an informational message. For example, you can use the **MessageBox** action with validation macros. When a control or record fails a validation condition in the macro, a message box can display an error message and provide instructions about the kind of data that should be entered. 
  
## Setting

The **MessageBox** action has the following arguments. 
  
|**Action argument**|**Description**|
|:-----|:-----|
|**Message** <br/> |The text in the message box. Enter the message text in the **Message** box in the **Action Arguments** section of the Macro Builder pane. You can type up to 255 characters or enter an expression (preceded by an equal sign).  <br/> |
|**Beep** <br/> |Specifies whether your computer's speaker sounds a beep tone when the message displays. Click **Yes** (sound the beep tone) or **No** (don't sound the beep tone). The default is **Yes**.  <br/> |
|**Type** <br/> |The type of message box. Each type has a different icon. Click **None**, **Critical**, **Warning?**, **Warning!**, or **Information**. The default is **None**.  <br/> |
|**Title** <br/> |The text displayed in the message box title bar. For example, you can have the title bar display "Customer ID Validation". If you leave this argument blank, "Microsoft Access" is displayed.  <br/> |
   
## Remarks

You can use the **MessageBox** action to create a formatted error message similar to built-in error messages displayed by Microsoft Access. The **MessageBox** action permits you to supply a message in three sections for the Message argument. You separate the sections with the "@" character. 
  
The following example displays a formatted message box with a sectioned message. The first section of text in the message is displayed as a bold heading. The second section is displayed as plain text beneath that heading. The third section is displayed as plain text beneath the second section, with a blank line between them.
  
Type the following string in the **Message** argument: 
  
 **Wrong button!@This button doesn't work.@Try another.**
  
You can't run the **MessageBox** action in a Visual Basic for Applications (VBA) module. Use the **MsgBox** function instead. 
  
## Examples

 **Synchronize forms by using a macro**
  
The following macro opens a Product List form in the lower-right corner of the Suppliers form, displaying the current supplier's products. It shows the use of the **Echo**, **MessageBox**, **GoToControl**, **StopMacro**, **OpenForm**, and **MoveAndSizeWindow** actions. It also shows the use of a conditional expression with the **MessageBox**, **GoToControl**, and **StopMacro** actions. This macro should be attached to the Review Products button on the Suppliers form. 
  
|**Condition**|**Action**|**Arguments: Setting**|**Comment**|
|:-----|:-----|:-----|:-----|
||**Echo** <br/> |**Echo On**: **No** <br/> |Stop screen updating while the macro is running.  <br/> |
|IsNull([SupplierID])  <br/> |**MessageBox** <br/> |**Message**: Move to the supplier record whose products you want to see, then click the Review Products button again. **Beep**: **Yes** **Type**: **None** **Title**: Select a Supplier  <br/> |If there is no current supplier on the Suppliers form, display a message.  <br/> |
|...  <br/> |**GoToControl** <br/> |**Control Name**: CompanyName  <br/> |Move focus to the CompanyName control.  <br/> |
|...  <br/> |**StopMacro** <br/> ||Stop the macro.  <br/> |
||**OpenForm** <br/> |**Form Name**: Product List **View**: **Datasheet** **Filter Name**: **Where Condition**: [SupplierID] = [Forms]![Suppliers]![SupplierID] **Data Mode**: **Read Only** **Window Mode**: **Normal** <br/> |Open the Product List form and show the current supplier's products.  <br/> |
||**MoveAndSizeWindow** <br/> |**Right**: 0.7799" **Down**: 1.8"  <br/> |Position the Product List form in the lower right of the Suppliers form.  <br/> |
   
 **Validate data by using a macro**
  
The following validation macro checks the postal codes entered in a Suppliers form. It shows the use of the **StopMacro**, **MessageBox**, **CancelEvent**, and **GoToControl** actions. A conditional expression checks the country/region and postal code entered in a record on the form. If the postal code isn't in the right format for the country/region, the macro displays a message box and cancels saving the record. It then returns you to the PostalCode control, where you can correct the error. This macro should be attached to the **BeforeUpdate** property of the Suppliers form. 
  
|**Condition**|**Action**|**Arguments: Setting**|**Comment**|
|:-----|:-----|:-----|:-----|
|IsNull([CountryRegion])  <br/> |**StopMacro** <br/> ||If CountryRegion is **Null**, the postal code can't be validated.  <br/> |
|[CountryRegion] In ("France","Italy","Spain") And Len([PostalCode]) \<\> 5  <br/> |**MessageBox** <br/> |**Message**: The postal code must be 5 characters. **Beep**: **Yes** **Type**: **Information** **Title**: Postal Code Error  <br/> |If the postal code isn't 5 characters, display a message.  <br/> |
|...  <br/> |**CancelEvent** <br/> ||Cancel the event.  <br/> |
||**GoToControl** <br/> |**Control Name**: PostalCode  <br/> ||
|[CountryRegion] In ("Australia","Singapore") And Len([PostalCode]) \<\> 4  <br/> |**MessageBox** <br/> |**Message**: The postal code must be 4 characters. **Beep**: **Yes** **Type**: **Information** **Title**: Postal Code Error  <br/> |If the postal code isn't 4 characters, display a message.  <br/> |
|...  <br/> |**CancelEvent** <br/> ||Cancel the event.  <br/> |
||**GoToControl** <br/> |**Control Name**: PostalCode  <br/> ||
|([CountryRegion] = "Canada") And ([PostalCode] Not Like"[A-Z][0-9][A-Z] [0-9][A-Z][0-9]")  <br/> |**MessageBox** <br/> |**Message**: The postal code is not valid. Example of Canadian code: H1J 1C3 **Beep**: **Yes** **Type**: **Information** **Title**: Postal Code Error  <br/> |If the postal code isn't correct for Canada, display a message. (Example of Canadian code: H1J 1C3)  <br/> |
|...  <br/> |**CancelEvent** <br/> ||Cancel the event.  <br/> |
   

