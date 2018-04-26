---
title: "Field2.IsComplex Property (DAO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: ffc90e6e-e3ee-4f9b-ca6b-615199300d45
description: "Returns Boolean that indicates whether the specified field is a multi-valued data type. Read-only."
---

# Field2.IsComplex Property (DAO)

Returns **Boolean** that indicates whether the specified field is a multi-valued data type. Read-only. 
  
## Version Information

Version Added: Access 2007 
  
## Syntax

 *expression*  . **IsComplex**
  
 *expression*  A variable that represents a **Field2** object. 
  
## Example

The following example shows how to navigate a **Recordset** that contains a multi-value field. 
  
 **Sample code provided by:** The [Microsoft Access 2010 Programmer's Reference](http://www.wrox.com/WileyCDA/WroxTitle/Access-2010-Programmer-s-Reference.productCd-0470591668.mdl) | [About the Contributors](#AboutContributors)
  
```
Sub PrintStudentsAndClasses()
    Dim dbs As DAO.Database
    Dim rsStudents As DAO.Recordset2  'Recordset for students
    Dim rsClasses As DAO.Recordset2  'Recordset for classes
    Dim fld As DAO.Field2
    'open the database
    Set dbs = CurrentDb()
    'get the table of students
    Set rsStudents = dbs.OpenRecordset("tblStudents")
    'loop through the students
    Do While Not rsStudents.EOF
        
        'get the classes field
        Set fld = rsStudents("Classes")
        'get the classes Recordset
        'make sure the field is a multi-valued field before
        'getting a Recordset object
        If fld.IsComplex Then
            Set rsClasses = fld.Value
        End If
        'access all records in the Recordset
        If Not (rsClasses.BOF And rsClasses.EOF) Then
            rsClasses.MoveLast
            rsClasses.MoveFirst
        End If
        'print the student and number of classes
        Debug.Print rsStudents("FirstName") &amp; " " &amp; rsStudents("LastName"), _
            "Number of classes: " &amp; rsClasses.RecordCount
        'print the classes for this student
        Do While Not rsClasses.EOF
            Debug.Print , rsClasses("Value")
            rsClasses.MoveNext
        Loop
        'close the Classes Recordset
        rsClasses.Close
        'get the next student
        rsStudents.MoveNext
    Loop
    
    'cleanup
    rsStudents.Close
    Set fld = Nothing
    Set rsStudents = Nothing
    Set dbs = Nothing
End Sub
```

## About the Contributors
<a name="AboutContributors"> </a>

Wrox Press is driven by the Programmer to Programmer philosophy. Wrox books are written by programmers for programmers, and the Wrox brand means authoritative solutions to real-world programming problems. 
  

