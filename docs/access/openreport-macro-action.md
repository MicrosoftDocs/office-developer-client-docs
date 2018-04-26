---
title: "OpenReport Macro Action"
 
 
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vbaac10.chm188079
  
localization_priority: Normal
ms.assetid: cd35faf2-190d-ac48-cf59-81c1599eb764

description: "You can use the OpenReport action to open a report in Design view or Print Preview, or to send the report directly to the printer. You can also restrict the records that are printed in the report."
---

# OpenReport Macro Action

You can use the **OpenReport** action to open a report in Design view or Print Preview, or to send the report directly to the printer. You can also restrict the records that are printed in the report. 
  
## Setting

The **OpenReport** action has the following arguments. 
  
|**Action argument**|**Description**|
|:-----|:-----|
| _Report Name_ <br/> |The name of the report to open. The **Report Name** box in the **Action Arguments** section of the **Macro Builder** pane shows all reports in the current database. This is a required argument. If you run a macro containing the **OpenReport** action in a library database, Microsoft Access first looks for the report with this name in the library database, and then in the current database.  <br/> |
| _View_ <br/> |The view in which the report will open. Click **Print** (print the report immediately), **Design**, or **Print Preview** in the **View** box. The default is **Print**.  <br/> |
| _Filter Name_ <br/> |A filter that restricts the report's records. You can enter the name of either an existing query or a filter that was saved as a query. However, the query must include all the fields in the report you are opening or have its **OutputAllFields** property set to **Yes**.  <br/> |
| _Where Condition_ <br/> |A valid SQL WHERE clause (without the word WHERE) or expression that Access uses to select records from the report's underlying table or query. If you select a filter with the  _Filter Name_ argument, Access applies this WHERE clause to the results of the filter. To open a report and restrict its records to those specified by the value of a control on a form, use the following expression:           **[** *fieldname* **] = Forms![** *formname* **]![** *controlname on form* **]**          Replace  *fieldname*  with the name of a field in the underlying table or query of the report you want to open. Replace  *formname*  and  *controlname on form*  with the name of the form and the control on the form that contains the value you want records in the report to match.  <br/> > [!NOTE]> The maximum length of the  _Where Condition_ argument is 255 characters. If you need to enter a more complex SQL WHERE clause longer than this, use the **OpenReport** method of the **DoCmd** object in a Visual Basic for Applications (VBA) module instead. You can enter SQL WHERE clause statements of up to 32,768 characters in VBA.           |
| _Window Mode_ <br/> | The mode in which the report will open. Click **Normal**, **Hidden**, **Icon**, or **Dialog** in the **Window Mode** box. The default is **Normal**.  <br/> > [!NOTE]>  Some  _Window Mode_ argument settings do not apply when using tabbed documents. To switch to overlapping windows:            and then click **Options**.  <br/>  In the **Access Options** dialog box, click **Current Database**.  <br/>  In the **Application Options** section, under **Document Window Options**, click **Overlapping Windows**.  <br/>  Click **OK**, then close and reopen the database.  <br/> |
   
## Remarks

The **Print** setting for the **View** argument prints the report immediately by using the current printer settings, without bringing up the **Print** dialog box. You can also use the **OpenReport** action to open and set up a report and then use the **PrintOut** action to print it. For example, you may want to modify the report or use the **PrintOut** action to change the printer settings before you print. 
  
The filter and WHERE condition you apply become the setting of the report's **Filter** property. 
  
The **OpenReport** action is similar to double-clicking the report in the Navigation Pane, or right-clicking the report in the Navigation Pane and selecting a view or the **Print** command. 
  
 **Tips**
  
- To print similar reports for different sets of data, use a filter or a WHERE clause to restrict the records printed in the report. Then edit the macro to apply a different filter or change the  _Where Condition_ argument. 
    
- You can drag a report from the Navigation Pane to a macro action row. This automatically creates an **OpenReport** action that opens the report in Report view. 
    
## Example

The following example shows how to use the **OpenReport** action to pass a parameter that filters a report as it is opened. The **rptChapters** report displays the records for the specified author by passing the item selected in the **cboAuthors** combo box to the  _SelectedAuthor_ parameter. 
  
 **Sample code provided by:** The [Microsoft Access 2010 Programmer's Reference](http://www.wrox.com/WileyCDA/WroxTitle/Access-2010-Programmer-s-Reference.productCd-0470591668.mdl)
  
```
OpenReport
    Report Name rptChapters
    View Report
    Filter Name
    Where Condition
    Window Mode Normal
Parameters
    SelectedAuthor =[cboAuthor]
```

## About the Contributors
<a name="AboutContributors"> </a>

Wrox Press is driven by the Programmer to Programmer philosophy. Wrox books are written by programmers for programmers, and the Wrox brand means authoritative solutions to real-world programming problems. 
  

