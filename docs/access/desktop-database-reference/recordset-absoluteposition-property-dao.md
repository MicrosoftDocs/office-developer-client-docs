---
title: Recordset.AbsolutePosition Property (DAO)
TOCTitle: AbsolutePosition Property
ms:assetid: c35c0c07-f789-524b-0a3d-dfd18fa6eebc
ms:mtpsurl: https://msdn.microsoft.com/library/Ff823038(v=office.15)
ms:contentKeyID: 48547569
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Recordset.AbsolutePosition Property (DAO)

**Applies to**: Access 2013 | Office 2013

Sets or returns the relative record number of a **Recordset** object's current record.

## Syntax

*expression* .AbsolutePosition

*expression* A variable that represents a **Recordset** object.

## Remarks

You can use the **AbsolutePosition** property to position the current record pointer to a specific record based on its ordinal position in a dynaset- or snapshot-type **Recordset** object. You can also determine the current record number by checking the **AbsolutePosition** property setting.

Because the **AbsolutePosition** property value is zero-based (that is, a setting of 0 refers to the first record in the **Recordset** object), you cannot set it to a value greater than or equal to the number of populated records; doing so causes a trappable error. You can determine the number of populated records in the **Recordset** object by checking the **RecordCount** property setting. The maximum allowable setting for the **AbsolutePosition** property is the value of the **RecordCount** property minus 1.

If there is no current record, as when there are no records in the **Recordset** object, **AbsolutePosition** returns –1. If the current record is deleted, the **AbsolutePosition** property value isn't defined, and a trappable error occurs if it's referenced. New records are added to the end of the sequence.

You shouldn't use this property as a surrogate record number. Bookmarks are still the recommended way of retaining and returning to a given position and are the only way to position the current record across all types of **Recordset** objects. In particular, the position of a record changes when one or more records preceding it are deleted. There is also no assurance that a record will have the same absolute position if the **Recordset** object is re-created again because the order of individual records within a **Recordset** object isn't guaranteed unless it's created with an SQL statement by using an ORDER BY clause.

> [!NOTE]
> - Setting the **AbsolutePosition** property to a value greater than zero on a newly opened but unpopulated **Recordset** object causes a trappable error. Populate the **Recordset** object first with the **MoveLast** method.
> - The **AbsolutePosition** property isn't available on forward–only–type **Recordset** objects, or on **Recordset** objects opened from pass-through queries against Microsoft Access database engine-connected ODBC databases.

## Example

This example uses the **AbsolutePosition** property to track the progress of a loop that enumerates all the records of a **Recordset**.

```vb
    Sub AbsolutePositionX() 
     
       Dim dbsNorthwind As Database 
       Dim rstEmployees As Recordset 
       Dim strMessage As String 
     
       Set dbsNorthwind = OpenDatabase("Northwind.mdb") 
       ' AbsolutePosition only works with dynasets or snapshots. 
       Set rstEmployees = _ 
          dbsNorthwind.OpenRecordset("Employees", _ 
          dbOpenSnapshot) 
     
       With rstEmployees 
          ' Populate Recordset. 
          .MoveLast 
          .MoveFirst 
     
          ' Enumerate Recordset. 
          Do While Not .EOF 
             ' Display current record information. Add 1 to  
             ' AbsolutePosition value because it is zero-based. 
             strMessage = "Employee: " & !LastName & vbCr & _ 
                "(record " & (.AbsolutePosition + 1) & _ 
                " of " & .RecordCount & ")" 
             If MsgBox(strMessage, vbOKCancel) = vbCancel _ 
                Then Exit Do 
             .MoveNext 
          Loop 
     
          .Close 
       End With 
     
       dbsNorthwind.Close 
     
    End Sub
```
