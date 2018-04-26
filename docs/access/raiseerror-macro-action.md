---
title: "RaiseError Macro Action"
 
 
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: c8c57685-b373-67d6-cea6-8f2c334547d3
description: "The RaiseError action throws an exception that can be handled by the OnError macro action."
---

# RaiseError Macro Action

The **RaiseError** action throws an exception that can be handled by the **[OnError](onerror-macro-action.md)** macro action. 
  
> [!NOTE]
> The **RaiseError** action is available only in Data Macros. 
  
## Setting

The **RaiseError** action has the following arguments. 
  
|**Argument**|**Required**|**Description**|
|:-----|:-----|:-----|
| _Error Number_ <br/> |Yes  <br/> |A number or an expression that resolves to the **Long** data type.  <br/> |
| _Error Description_ <br/> |No  <br/> |A string expression that describes the error.  <br/> |
   
## Remarks

If the **RaiseError** action is called in a **[Before Change](before-change-macro-event.md)** or **[Before Delete](before-delete-macro-event.md)** macro event, the event is cancelled. 
  
If there is not an active **OnError** statment that is handling errors, then the error thrown by the **RaiseError** action is added to the **USysApplicationLog** system table. When the **RaiseError** action to writes to the **USysApplicationLog** table, the **Category** column is automatically set to **Execution**. 
  
To see the **USysApplicationLog** table, use the following steps: 
  
1. Click the **File** menu, and then click **Options**.
    
2. In the **Access Options** dialog box, click the **Current Database** tab. 
    
3. In the **Navigation** section, click **Navigation Options**.
    
4. In the **Navigation Options** dialog box, click **Show System Objects**, and then click **OK**.
    
5. Click **OK** to dismiss the **Access Options** dialog box. 
    
## Example

The following example shows how to use the **RaiseError** action to cancel the **Before Change** data macro event. When the **AssignedTo** field is updated, a **LookupRecord** data block is used to determine whether the assigned technician is currently assigned to an open service request. If this is true, then the **Before Change** event is cancelled and the record is not updated. 
  
 **Sample code provided by:** The [Microsoft Access 2010 Programmer's Reference](http://www.wrox.com/WileyCDA/WroxTitle/Access-2010-Programmer-s-Reference.productCd-0470591668.mdl)
  
```
/* Get the name of the technician  */
Look Up A Record In tblTechnicians
    Where Condition =[tblTechnicians].[ID]=[tblServiceRequests].[AssignedTo]
SetLocalVar
    Name TechName
    Expression [tblTechnicians].[FirstName] &amp; " " &amp; [tblTechnicians].[LastName]
/* End LookUpRecord  */
If Updated("AssignedTo") Then
    Look Up A Record In tblServiceRequests
        Where Condition SR.[AssignedTo]=tblServiceRequests[AssignedTo] And 
            SR.[ID]<>tblServiceRequests.[ID] And IsNull(SR.[ActualCompletionDate])
        Alias SR
        RaiseError
            Error Number 1234
            Error Description ="Cannot assign a request to the specified technician: " &amp; [TechName]
End If
```

## About the Contributors
<a name="AboutContributors"> </a>

Wrox Press is driven by the Programmer to Programmer philosophy. Wrox books are written by programmers for programmers, and the Wrox brand means authoritative solutions to real-world programming problems. 
  

