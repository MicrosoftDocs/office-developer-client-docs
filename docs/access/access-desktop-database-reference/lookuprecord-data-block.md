---
title: LookupRecord Data Block
TOCTitle: LookupRecord Data Block
ms:assetid: 750dc8ca-3bab-c3d1-c91d-2196f9c0604d
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff195882(v=office.15)
ms:contentKeyID: 48545671
ms.date: 09/18/2015
mtps_version: v=office.15
---

# LookupRecord Data Block


_**Applies to:** Access 2013 | Office 2013_

**In this article**  
Setting  
Remarks  
Example  
About the Contributors  

A **LookupRecord** data block performs a set of actions on a specific record.


> [!NOTE]
> <P>The <STRONG>LookupRecord</STRONG> data block is available only in Data Macros.</P>



## Setting

The **SetField** action has the following arguments.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Argument</p></th>
<th><p>Required</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>In</p></td>
<td><p>Yes</p></td>
<td><p>A string that identifies the record to operate on. The <em>In</em> argument can contain the name of the table, a select query, or a SQL statement.</p>

> [!NOTE]
> <P>The specified record cannot include data stored in a linked table or ODBC data source.</P>


<p></p></td>
</tr>
<tr class="even">
<td><p>Where Condition</p></td>
<td><p>No</p></td>
<td><p>A string expression used to restrict the range of data on which the <strong>LookupRecord</strong> data block is performed. For example, criteria are often equivalent to the WHERE clause in an SQL expression, without the word WHERE. If criteria are omitted, the <strong>LookupRecord</strong> data block operates on the entire domain specified by the <em>In</em> argument. Any field that is included in criteria must also be a field in <em>In</em>.</p></td>
</tr>
<tr class="odd">
<td><p>Alias</p></td>
<td><p>No</p></td>
<td><p>A string that provides an alternative name for the record specified by the <em>In</em> argument. Often used to shorten the table name for subsequent references to prevent possible ambiguous references. If <em>Alias</em> is not specified, the table or query name will be used as the alias.</p></td>
</tr>
</tbody>
</table>


## Remarks

If the criteria specified by the *In* and *Where Condition* arguments specifies more than one record, the **LookupRecord** data block will operate only on the first record.

## Example

The following example shows how to use the SetReturnVar action to return a value from a named data macro. A ReturnVar named **CurrentServiceRequest** is returned to the macro or Visual Basic for Applications (VBA) subroutine that called the named data macro.

**Sample code provided by:** The [Microsoft Access 2010 Programmer’s Reference](http://www.wrox.com/wileycda/wroxtitle/access-2010-programmer-s-reference.productcd-0470591668.html)

    RunDataMacro
        Macro Name tblServiceRequests.dmGetCurrentServiceRequest
    
    Parameters
        prmAssignedTo =[ID]
    
    SetProperty
        Control Name txtCurrentSR
        Property Value
        Value =[ReturnVars]![CurrentServiceRequest]

The following example shows how to use the RaiseError action to cancel the Before Change data macro event. When the AssignedTo field is updated, a LookupRecord data block is used to determine whether the assigned technician is currently assigned to an open service request. If this is true, the Before Change event is cancelled and the record is not updated.

    /* Get the name of the technician  */
    Look Up A Record In tblTechnicians
        Where Condition =[tblTechnicians].[ID]=[tblServiceRequests].[AssignedTo]
    SetLocalVar
        Name TechName
        Expression [tblTechnicians].[FirstName] & " " & [tblTechnicians].[LastName]
    /* End LookUpRecord  */
    
    If Updated("AssignedTo") Then
        Look Up A Record In tblServiceRequests
            Where Condition SR.[AssignedTo]=tblServiceRequests[AssignedTo] And 
                SR.[ID]<>tblServiceRequests.[ID] And IsNull(SR.[ActualCompletionDate])
            Alias SR
            RaiseError
                Error Number 1234
                Error Description ="Cannot assign a request to the specified technician: " & [TechName]
    
    End If

## About the Contributors

Wrox Press is driven by the Programmer to Programmer philosophy. Wrox books are written by programmers for programmers, and the Wrox brand means authoritative solutions to real-world programming problems.

