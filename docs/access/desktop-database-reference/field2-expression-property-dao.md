---
title: Field2.Expression property (DAO)
TOCTitle: Expression Property
ms:assetid: 8ae9db2c-7460-5bfc-0dc4-3f87e5ab30ff
ms:mtpsurl: https://msdn.microsoft.com/library/Ff197109(v=office.15)
ms:contentKeyID: 48546205
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- dao360.chm1053562
ms.localizationpriority: medium
---

# Field2.Expression property (DAO)

**Applies to**: Access 2013, Office 2013

Gets or sets an expression that represents the formula for a calculated field. Read/write **String**.

## Version information

Version added: Access 2010

## Syntax

*expression* .Expression

*expression* A variable that represents a **Field2** object.

## Remarks

In Access 2013, you can create table fields that calculate values. The calculations can include values from fields in the same table as well as built-in Access functions.

The calculation cannot include fields from other tables or queries.

The results of the calculation are read-only.

## Example

The following example shows how to create a calculated field. The CreateField method creates a field named **FullName**. The Expression property is then set to the expression that calculates the value of the field.

**Sample code provided by** the [Microsoft Access 2010 Programmer’s Reference](https://www.amazon.com/Microsoft-Access-2010-Programmers-Reference/dp/8126528125).

```vb
    Sub CreateCalculatedField()
        Dim dbs As DAO.Database
        Dim tdf As DAO.TableDef
        Dim fld As DAO.Field2
        
        ' get the database
        Set dbs = CurrentDb()
        
        ' create the table
        Set tdf = dbs.CreateTableDef("tblContactsCalcField")
        
        ' create the fields: first name, last name
        tdf.Fields.Append tdf.CreateField("FirstName", dbText, 20)
        tdf.Fields.Append tdf.CreateField("LastName", dbText, 20)
        
        ' create the calculated field: full name
        Set fld = tdf.CreateField("FullName", dbText, 50)
        fld.Expression = "[FirstName] & "" "" & [LastName]"
        tdf.Fields.Append fld
        
        ' append the table and cleanup
        dbs.TableDefs.Append tdf
        
    Cleanup:
        Set fld = Nothing
        Set tdf = Nothing
        Set dbs = Nothing
    End Sub
```

