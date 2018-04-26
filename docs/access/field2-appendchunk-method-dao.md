---
title: "Field2.AppendChunk Method (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- dao360.chm1052867
  
localization_priority: Normal
ms.assetid: 540cd02d-1fc6-81d1-ac08-1e3df72a7208
description: "Appends data from a string expression to a Memo or Long Binary Field2 object in a Recordset ."
---

# Field2.AppendChunk Method (DAO)

Appends data from a string expression to a Memo or Long Binary **Field2** object in a **[Recordset](recordset-object-dao.md)**. 
  
## Syntax

 *expression*  . **AppendChunk**( ** *Val* ** ) 
  
 *expression*  A variable that represents a **Field2** object. 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Val_ <br/> |Required  <br/> |**Variant** <br/> |A Variant (String subtype) expression or variable containing the data you want to append to the **Field2** object.  <br/> |
   
## Remarks

You can use the **AppendChunk** and **GetChunk** methods to access subsets of data in a Memo or Long Binary field. 
  
You can also use these methods to conserve string space when you work with Memo and Long Binary fields. Certain operations (copying, for example) involve temporary strings. If string space is limited, you may need to work with chunks of a field instead of the entire field.
  
If there is no current record when you use **AppendChunk**, an error occurs. 
  
> [!NOTE]
> The initial **AppendChunk** operation (after an **[Edit](recordset-edit-method-dao.md)** or **[AddNew](recordset-addnew-method-dao.md)** call) will simply place the data in the field, overwriting any existing data. Subsequent **AppendChunk** calls within the same **Edit** or **AddNew** session will then add to the existing data. 
  
## Example

This example uses the **AppendChunk** and **GetChunk** methods to fill an OLE object field with data from another record, 32K at a time. In a real application, one might use a procedure like this to copy an employee record (including the employee's photo) from one table to another. In this example, the record is simply being copied back to same table. Note that all the chunk manipulation takes place within a single AddNew-Update sequence. 
  
```
Sub AppendChunkX() 
 
   Dim dbsNorthwind As Database 
   Dim rstEmployees As Recordset 
   Dim rstEmployees2 As Recordset 
 
   Set dbsNorthwind = OpenDatabase("Northwind.mdb") 
 
   ' Open two recordsets from the Employees table. 
   Set rstEmployees = _ 
      dbsNorthwind.OpenRecordset("Employees", _ 
      dbOpenDynaset) 
   Set rstEmployees2 = rstEmployees.Clone 
 
   ' Add a new record to the first Recordset and copy the  
   ' data from a record in the second Recordset. 
   With rstEmployees 
      .AddNew 
      !FirstName = rstEmployees2!FirstName 
      !LastName = rstEmployees2!LastName 
      CopyLargeField rstEmployees2!Photo, !Photo 
      .Update 
 
      ' Delete new record because this is a demonstration. 
      .Bookmark = .LastModified 
      .Delete 
      .Close 
   End With 
 
   rstEmployees2.Close 
   dbsNorthwind.Close 
 
End Sub 
 
Function CopyLargeField(fldSource As Field2, _ 
   fldDestination As Field2) 
 
   ' Set size of chunk in bytes. 
   Const conChunkSize = 32768 
 
   Dim lngOffset As Long 
   Dim lngTotalSize As Long 
   Dim strChunk As String 
 
   ' Copy the photo from one Recordset to the other in 32K  
   ' chunks until the entire field is copied. 
   lngTotalSize = fldSource.FieldSize 
   Do While lngOffset < lngTotalSize 
      strChunk = fldSource.GetChunk(lngOffset, conChunkSize) 
      fldDestination.AppendChunk strChunk 
      lngOffset = lngOffset + conChunkSize 
   Loop 
 
End Function 

```


