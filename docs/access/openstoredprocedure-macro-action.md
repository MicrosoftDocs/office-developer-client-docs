---
title: "OpenStoredProcedure Macro Action"
 
 
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vbaac10.chm187628
  
localization_priority: Normal
ms.assetid: b14dbb82-7c8a-0ace-e251-46599551a490
description: "In an Access project, you can use the OpenStoredProcedure action to open a stored procedure in Datasheet view, stored procedure Design view, or Print Preview. This action runs the named stored procedure when opened in Datasheet view. You can select the data entry mode for the stored procedure and restrict the records that the stored procedure displays."
---

# OpenStoredProcedure Macro Action

In an Access project, you can use the **OpenStoredProcedure** action to open a stored procedure in Datasheet view, stored procedure Design view, or Print Preview. This action runs the named stored procedure when opened in Datasheet view. You can select the data entry mode for the stored procedure and restrict the records that the stored procedure displays. 
  
> [!NOTE]
> This action will not be allowed if the database is not trusted. For more information about enabling macros, see the links in the **See Also** section of this article. 
  
## Setting

The **OpenStoredProcedure** action has the following arguments. 
  
|**Action argument**|**Description**|
|:-----|:-----|
|**Procedure Name** <br/> |The name of the stored procedure to open. The **Procedure Name box** box in the **Action Arguments** section of the Macro Builder pane shows all stored procedures in the current database. This is a required argument. If you run a macro containing the **OpenStoredProcedure** action in a library database, Microsoft Access first looks for the stored procedure with this name first in the library database, and then in the current database.  <br/> |
|**View** <br/> |The view in which the stored procedure will open. Click **Datasheet**, **Design**, **Print Preview**, **PivotTable**, or **PivotChart** in the **View** box. The default is **Datasheet**.  <br/> |
|**Data Mode** <br/> |The data entry mode for the stored procedure. This applies only to stored procedures opened in Datasheet view. Click **Add** (the user can add new records but can't view or edit existing records), **Edit** (the user can view or edit existing records and add new records), or **Read Only** (the user can only view records). The default is **Edit**.  <br/> |
   
## Remarks

This action is similar to double-clicking the stored procedure in the Navigation Pane, or right-clicking the stored procedure in the Navigation Pane and selecting the command you want.
  
Switching to Design view while the stored procedure is open removes the **Data Mode** argument setting for the stored procedure. This setting is not in effect, even if the user returns to Datasheet view. 
  
> [!TIP]
> >  You can drag a stored procedure from the Navigation Pane to a macro action row. This automatically creates an **OpenStoredProcedure** action that opens the stored procedure in Datasheet view. >  If you do not want to display the system messages that normally appear when a stored procedure is run (indicating it is a stored procedure and showing how many records will be affected), you can use the **SetWarning** action to suppress the display of these messages. > 
  
To run the **OpenStoredProcedure** action in a Visual Basic for Applications (VBA) module, use the **OpenStoredProcedure** method of the **DoCmd** object. 
  

