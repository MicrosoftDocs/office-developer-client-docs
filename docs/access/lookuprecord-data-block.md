---
title: "LookupRecord Data Block"
 
 
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 750dc8ca-3bab-c3d1-c91d-2196f9c0604d

description: "A LookupRecord data block performs a set of actions on a specific record."
---

# LookupRecord Data Block

A **LookupRecord** data block performs a set of actions on a specific record. 
  
> [!NOTE]
> The **LookupRecord** data block is available only in Data Macros. 
  
## Setting

The **SetField** action has the following arguments. 
  
|**Argument**|**Required**|**Description**|
|:-----|:-----|:-----|
| _In_ <br/> |Yes  <br/> |A string that identifies the record to operate on. The  *In*  argument can contain the name of the table, a select query, or a SQL statement.  <br/> > [!NOTE]> The specified record cannot include data stored in a linked table or ODBC data source.           |
| _Where Condition_ <br/> |No  <br/> |A string expression used to restrict the range of data on which the **LookupRecord** data block is performed. For example, criteria are often equivalent to the WHERE clause in an SQL expression, without the word WHERE. If criteria are omitted, the **LookupRecord** data block operates on the entire domain specified by the  *In*  argument. Any field that is included in criteria must also be a field in  *In*  .  <br/> |
| _Alias_ <br/> |No  <br/> |A string that provides an alternative name for the record specified by the  *In*  argument. Often used to shorten the table name for subsequent references to prevent possible ambiguous references. If  *Alias*  is not specified, the table or query name will be used as the alias.  <br/> |
   
## Remarks

If the criteria specified by the  *In*  and  *Where Condition*  arguments specifies more than one record, the **LookupRecord** data block will operate only on the first record. 
  
## Example

The following example shows how to use the **SetReturnVar** action to return a value from a named data macro. A **ReturnVar** named **CurrentServiceRequest** is returned to the macro or Visual Basic for Applications (VBA) subroutine that called the named data macro. 
  
 **Sample code provided by:** The [Microsoft Access 2010 Programmer's Reference](http://www.wrox.com/WileyCDA/WroxTitle/Access-2010-Programmer-s-Reference.productCd-0470591668.mdl)
  
```
RunDataMacro
    Macro Name tblServiceRequests.dmGetCurrentServiceRequest
Parameters
    prmAssignedTo =[ID]
SetProperty
    Control Name txtCurrentSR
    Property Value
    Value =[ReturnVars]![CurrentServiceRequest]
```

The following example shows how to use the **RaiseError** action to cancel the **Before Change** data macro event. When the **AssignedTo** field is updated, a **LookupRecord** data block is used to determine whether the assigned technician is currently assigned to an open service request. If this is true, the **Before Change** event is cancelled and the record is not updated. 
  
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
  

