---
title: "BrowseTo Macro Action"
  
  
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
 
f1_keywords:
- vbaac10.chm35083
  
localization_priority: Normal
ms.assetid: b25e1cc6-c4ed-abd6-0285-94fc7dae0bdf
description: "You can use the BrowseTo action to navigate between objects in place. You can also change the source object of a subform control by specifying the Path to Subform Control argument. Use BrowseTo to navigate from form1 to form2 without opening up a new window."
---

# BrowseTo Macro Action

You can use the **BrowseTo** action to navigate between objects in place. You can also change the source object of a subform control by specifying the **Path to Subform Control** argument. Use **BrowseTo** to navigate from form1 to form2 without opening up a new window. 
  
## Setting

The **BrowseTo** action has the following argument. 
  
|**Action argument**|**Description**|
|:-----|:-----|
| _Object Type_ <br/> |The object type to which to browse.  <br/> |
| _Object Name_ <br/> |The object that loads inside the subform control referenced by the  _Path to Subform Control_ argument.  <br/> |
| _Path to Subform Control_ <br/> |If specified, the path from the main form of the application to the target subform control that loads the object specified by the  _Object Name_ argument.  <br/> |
| _Where Condition_ <br/> |If specified, replaces the Where condition of the object record source.  <br/> |
| _Page_ <br/> |If specified, sets the page of the continuous form that will be made the current page. This argument is Web only.  <br/> |
| _Data Mode_ <br/> |If specified, the data entry mode of the form.  <br/> |
   
## Remarks

The  _PathToSubFormControl_ argument must be specified using the syntax in the following code example: 
  
```
Main Form.SubForm Ctrl 1>Form 2.SubForm Ctrl 2>Form 3.SubFormCtrl3
```

In this example, the Main Form is the top level form in the Access client application. The  _Path to Sub Form Control_ argument must alternately specify form and subform control names leading from the main form to the subform control that is the container of the object specified by the  _Object Name_ argument. Each subform control specified must be a control on the form that precedes it. The path must end with a subform control. 
  
## Example

The following example shows how to use the **BrowseTo** action to open a report in a subform control or within a navigation control. 
  
 **Sample code provided by:** The [Microsoft Access 2010 Programmer's Reference](http://www.wrox.com/WileyCDA/WroxTitle/Access-2010-Programmer-s-Reference.productCd-0470591668.mdl)
  
```
OnError
    Go to Next
    Macro Name
/* Try to load the report in the host form (frmAuthorsParameter)    */
BrowseTo
    Object Type Report
    Object Name rptChapters
    Path to Subform Control frmAuthorsParameter.sfrmChild
    Where Condition
    Page
    Data Mode Edit
Parameters
    SelectedAuthor =[cboAuthor]
/* if this fails, try to load it in the navigation subform     */
BrowseTo
    Object Type Report
    Object Name rptChapters
    Path to Subform Control frmMain.NavigationSubform>frmAuthorsParameter.sfrmChild
    Where Condition
    Page
    Data Mode Edit
Parameters
    SelectedAuthor =[cboAuthor]
```

## About the Contributors
<a name="AboutContributors"> </a>

Wrox Press is driven by the Programmer to Programmer philosophy. Wrox books are written by programmers for programmers, and the Wrox brand means authoritative solutions to real-world programming problems. 
  

