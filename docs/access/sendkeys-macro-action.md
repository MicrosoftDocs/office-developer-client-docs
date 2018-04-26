---
title: "SendKeys Macro Action"
 
 
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vbaac10.chm183441
  
localization_priority: Normal
ms.assetid: 3b06fcfc-ea64-c780-b5fc-6fc72853f524
description: "Security Note Avoid using the SendKeys statement or an AutoKeys macro with sensitive or confidential information. A malicious user could intercept the keystrokes and compromise the security of your computer and data."
---

# SendKeys Macro Action

> [!SECURITY NOTE]

You can use the **SendKeys** action to send keystrokes directly to Microsoft Access or to an active Windows-based application. 
  
> [!NOTE]
> This action will not be allowed if the database is not trusted. For more information about enabling macros, see the links in the **See Also** section of this article. 
  
## Setting

The **SendKeys** action has the following arguments. 
  
|**Action argument**|**Description**|
|:-----|:-----|
|**Keystrokes** <br/> |The keystrokes you want Access or the application to process. Enter the keystrokes in the **Keystrokes** box in the **Action Arguments** section of the Macro Builder pane. You can type up to 255 characters. This is a required argument.  <br/> |
|**Wait** <br/> |Specifies whether the macro should pause until the keystrokes have been processed. Click **Yes** (to pause) or **No** (to not pause). The default is **No**.  <br/> |
   
## Remarks

Access processes the keystrokes it receives through the **SendKeys** action exactly as if you had typed them directly in an Access window. 
  
To specify the keystrokes, use the same syntax as you would for the **SendKeys** statement. 
  
> [!NOTE]
> An error can occur if the **Keystrokes** argument contains incorrect syntax, misspelled text, or other values that aren't appropriate for the window the keystrokes are sent to. 
  
You can use this action to enter information in a dialog box, particularly if you don't want to interrupt the macro to respond manually to the dialog box. Some Access actions, such as **PrintOut** and **FindRecord**, automatically select the options in certain frequently used dialog boxes. You can use the **SendKeys** action to select the options in less commonly used dialog boxes. 
  
> [!NOTE]
>  Because the dialog box suspends the macro, you must put the **SendKeys** action before the action that causes the dialog box to open and set the **Wait** argument to **No**. >  The timing of the keystrokes reaching Access or another application can be tricky. As a result, it's recommended that if there's some other method (such as the **FindRecord** action) you can use to achieve a desired task, use that method rather than using the **SendKeys** action to fill in the options in a dialog box. 
  
If you want to send more than 255 characters to Access or another Windows-based application, you can use several **SendKeys** actions in succession in a macro. 
  
Using the **SendKeys** action to send keystrokes triggers the appropriate **KeyDown**, **KeyUp**, and **KeyPress** events. Sending non-ANSI keystrokes (such as a function key) doesn't trigger the **KeyPress** event. 
  
This action isn't available from a Visual Basic for Applications (VBA) module. Use the **SendKeys** statement instead. 
  

