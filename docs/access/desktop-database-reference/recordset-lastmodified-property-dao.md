---
title: Recordset.LastModified property (DAO)
TOCTitle: LastModified Property
ms:assetid: 7386f25b-bde1-a446-e980-640696a3bfec
ms:mtpsurl: https://msdn.microsoft.com/library/Ff195859(v=office.15)
ms:contentKeyID: 48545640
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- dao360.chm1052898
f1_categories:
- Office.Version=v15
ms.localizationpriority: medium
---

# Recordset.LastModified property (DAO)


**Applies to**: Access 2013, Office 2013 

Returns a bookmark indicating the most recently added or modified record.

## Syntax

*expression* .LastModified

*expression* A variable that represents a **Recordset** object.

## Remarks

You can use the **LastModified** property to move to the most recently added or updated record. Use the **LastModified** property with table- and dynaset-type **[Recordset](recordset-object-dao.md)** objects. A record must be added or modified in the **Recordset** object itself in order for the **LastModified** property to have a value.

## Example

This example uses the **LastModified** property to move the current record pointer to both a record that has been modified and a newly created record.

```vb
Public Sub LastModifiedDemo() 
    
    Dim Northwind           As DAO.Database 
    Dim Employees           As DAO.Recordset 
    Dim CurrentFirstName    As String 
    Dim CurrentLastName     As String 
    
    Set Northwind = OpenDatabase("Northwind.mdb") 
    Set Employees = Northwind.OpenRecordset("Employees", dbOpenDynaset) 
    
    With Employees 
        ' Store current data. 
        CurrentFirstName = !FirstName 
        CurrentLastName = !LastName 

        ' Modify the data in the current record. 
        .Edit 
            !FirstName = "Julie" 
            !LastName = "Warren" 
        .Update 
        ' Move the current record pointer to the most recently 
        ' modified or added record. 
        .Bookmark = .LastModified 
        Debug.Print _ 
            "Data in LastModified record after Edit: " & _ 
            !FirstName & " " & !LastName 
        
        ' Restore the original data because this is a demonstration. 
        .Edit 
            !FirstName = CurrentFirstName 
            !LastName = CurrentLastName 
        .Update 
        
        ' Add new record. 
        .AddNew 
            !FirstName = "Roger" 
            !LastName = "Harui" 
        .Update 
        ' Move the current record pointer to the most recently 
        ' modified or added record. 
        .Bookmark = .LastModified 
        Debug.Print _ 
            "Data in LastModified record after AddNew: " & _ 
            !FirstName & " " & !LastName 
        
        ' Delete the new record because this is a demonstration. 
        .Delete 
        .Close 
    End With 
    Set Employees = Nothing

    Northwind.Close 
    Set Northwind = Nothing
 
End Sub 
```


This example uses the **AddNew** method to create a new record with the specified name. The AddName sub is required for this procedure to run.

```vb
Public Sub AddNewDemo() 
 
    Dim Northwind       As DAO.Database 
    Dim Employees       As DAO.Recordset 
    Dim FirstName       As String 
    Dim LastName        As String 
    
    Set Northwind = OpenDatabase("Northwind.mdb") 
    Set Employees = Northwind.OpenRecordset("Employees", dbOpenDynaset) 
    
    ' Get data from the user. 
    FirstName = Trim(InputBox("Enter first name:")) 
    LastName = Trim(InputBox("Enter last name:")) 
    
    ' Proceed only if the user actually entered something 
    ' for both the first and last names. 
    If FirstName <> "" And LastName <> "" Then        
        ' Call the sub that adds the record. 
        AddName Employees, FirstName, LastName 
        
        ' Show the newly added data. 
        With Employees 
            Debug.Print _ 
                "New record: " & !FirstName & " " & !LastName 
            ' Delete the new record because this is a demonstration. 
            .Delete 
        End With             
    Else 
        MsgBox _ 
            "You must input values for both first and last name.", _
            vbInformation + vbOKOnly, _
            "Add new name" 
    End If 
    
    Employees.Close 
    Set Employees = Nothing

    Northwind.Close 
    Set Northwind = Nothing
 
End Sub 

 
Public Sub AddName( _ 
    ByRef Records As DAO.Recordset, _ 
    ByVal FirstName As String, _ 
    ByVal LastName As String) 
    
    ' Adds a new record to a Recordset using the data 
    ' passed by the calling procedure. 
    ' The new record is then made the current record. 
    With Records 
        .AddNew 
            !FirstName = FirstName 
            !LastName = LastName 
        .Update 
        .Bookmark = .LastModified 
    End With 
 
End Function
```
