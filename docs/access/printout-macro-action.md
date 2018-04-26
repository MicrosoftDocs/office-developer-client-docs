---
title: "PrintOut Macro Action"
 
 
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vbaac10.chm1697
  
localization_priority: Normal
ms.assetid: 13688158-1cf1-4b2e-d90a-271c8890e413
description: "You can use the PrintOut action to print the active object in the open database. You can print datasheets, reports, forms, data access pages, and modules."
---

# PrintOut Macro Action

You can use the **PrintOut** action to print the active object in the open database. You can print datasheets, reports, forms, data access pages, and modules. 
  
> [!NOTE]
> This action will not be allowed if the database is not trusted. For more information about enabling macros, see the links in the **See Also** section of this article. 
  
## Setting

The **PrintOut** action has the following arguments. 
  
|**Action argument**|**Description**|
|:-----|:-----|
|**Print Range** <br/> |The range to print. Click **All** (the user can print all of the object), **Selection** (the user can print the part of the object that's selected), or **Pages** (the user can specify a range of pages in the **Page From** and **Page To** arguments) in the **Print Range** box in the **Action Arguments** section of the Macro Builder pane. The default is **All**.  <br/> |
|**Page From** <br/> |The first page to print. Printing starts at the top of this page. This argument is required if you select **Pages** in the **Print Range** box.  <br/> |
|**Page To** <br/> |The last page to print. Printing stops at the bottom of this page. This argument is required if you select **Pages** in the **Print Range** box.  <br/> |
|**Print Quality** <br/> |The print quality. Click **High**, **Medium**, **Low**, or **Draft**. The lower the quality, the faster the object prints. The default is **High**.  <br/> |
|**Copies** <br/> |The number of copies to print. The default is 1.  <br/> |
|**Collate Copies** <br/> |Click **Yes** (collate the printed copies) or **No** (do not collate copies). The object may print faster if this argument is set to **No**. The default is **Yes**.  <br/> |
   
## Remarks

This action is similar to selecting an object, clicking the **File** tab and then clicking **Print**. With this action, however, no **Print** dialog box appears. 
  
> [!TIP]
> If you have particular print settings you use frequently, create a macro containing a **PrintOut** action with these settings in its arguments. 
  
The arguments for this action correspond to options in the **Print** dialog box. However, unlike the **FindRecord** action and **Find and Replace** dialog box, the argument settings aren't shared with the **Print** dialog box options. 
  
To run the **PrintOut** action in a Visual Basic for Applications (VBA) module, use the **PrintOut** method of the **DoCmd** object. 
  

