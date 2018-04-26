---
title: "DisplayHourglassPointer Macro Action"
  
  
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
 
f1_keywords:
- vbaac10.chm117200
  
localization_priority: Normal
ms.assetid: 2c93039a-f75c-abeb-1dfa-e632a5bdf6f2
description: "You can use the DisplayHourglassPointer action to change the mouse pointer to an image of an hourglass (or another icon you've chosen) while a macro is running. This action can provide a visual indication that the macro is running. This is especially useful when a macro action or the macro itself takes a long time to run."
---

# DisplayHourglassPointer Macro Action

You can use the **DisplayHourglassPointer** action to change the mouse pointer to an image of an hourglass (or another icon you've chosen) while a macro is running. This action can provide a visual indication that the macro is running. This is especially useful when a macro action or the macro itself takes a long time to run. 
  
## Setting

The **DisplayHourglassPointer** action has the following argument. 
  
|**Action argument**|**Description**|
|:-----|:-----|
|**Hourglass On** <br/> |Click **Yes** (display the icon) or **No** (display the normal mouse pointer) in the **Hourglass On** box in the **Action Arguments** section of the Macro Builder pane. The default is **Yes**.  <br/> |
   
## Remarks

You often use this action if you have turned echo off by using the **Echo** action. When echo is off, Access suspends screen updates until the macro is finished. 
  
Access automatically resets the **Hourglass On** argument to **No** when the macro finishes running. 
  
> [!NOTE]
>  In Microsoft Windows, this is the icon you set for **Busy** in the **Mouse Properties** dialog box of Windows Control Panel. The default for all Windows operating systems is an animated hourglass icon. >  You can choose another icon if you want. 
  
To run the **DisplayHourglassPointer** action in a Visual Basic for Applications (VBA) module, use the **Hourglass** method of the **DoCmd** object. 
  

