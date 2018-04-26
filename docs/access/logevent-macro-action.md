---
title: "LogEvent Macro Action"
 
 
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 3578c725-64b9-385e-ef73-a15cdf751c33
description: "The LogEvent action writes information to the USysApplicationLog system table."
---

# LogEvent Macro Action

The **LogEvent** action writes information to the **USysApplicationLog** system table. 
  
> [!NOTE]
> The **LogEvent** action is available only in Data Macros. 
  
## Setting

The **LogEvent** action has the following arguments. 
  
|**Argument**|**Required**|**Description**|
|:-----|:-----|:-----|
|**Description** <br/> |No  <br/> |A string expression that describes the condition that you want to log. The description cannot exceed 255 characters.  <br/> |
   
## Remarks

The **LogEvent** action can be used to write status information to the **USysApplicationLog** system table that does not merit using the **[RaiseError](raiseerror-macro-action.md)** action to throw an error. For example, you could log changes to a specific field, or use the items written to the **USysApplicationLog** to assist you in debugging your macro. 
  
When you use the **LogEvent** action to write to the **USysApplicationLog** table, the **Category** column is automatically set to **User**. 
  
 To see the **USysApplicationLog** table, use the following steps: 
  
1. Click the **File** menu,and then click **Options**.
    
2. In the **Access Options** dialog box, click the **Current Database** tab. 
    
3. In the **Navigation** section, click **Navigation Options**.
    
4. In the **Navigation Options** dialog box, click **Show System Objects**, and then click **OK**.
    
5. Click **OK** to dismiss the **Access Options** dialog box. 
    

