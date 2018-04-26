---
title: "Index.IgnoreNulls Property (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- dao360.chm1052931
  
localization_priority: Normal
ms.assetid: f49f17b8-d7c1-18ab-07a8-e1be61488519
description: "Sets or returns a value that indicates whether records that have Null values in their index fields have index entries (Microsoft Access workspaces only)."
---

# Index.IgnoreNulls Property (DAO)

Sets or returns a value that indicates whether records that have Null values in their index fields have index entries (Microsoft Access workspaces only).
  
## Syntax

 *expression*  . **IgnoreNulls**
  
 *expression*  A variable that represents an **Index** object. 
  
## Remarks

 This property is read/write for a new **[Index](index-object-dao.md)** object not yet appended to a collection and read-only for an existing **Index** object in an **[Indexes](indexes-collection-dao.md)** collection. 
  
To speed up the process of searching for records, you can define an index for a field. If you allow **null** entries in an indexed field and expect many of the entries to be **null**, you can set the **IgnoreNulls** property for the **Index** object to **True** to reduce the amount of storage space that the index uses. 
  
The **IgnoreNulls** property setting and the **[Required](field-required-property-dao.md)** property setting together determine whether a record with a **null** index value has an index entry. 
  
|**If IgnoreNulls is**|**And Required is**|**Then**|
|:-----|:-----|:-----|
|True  <br/> |False  <br/> |A null value is allowed in the index field; no index entry added.  <br/> |
|False  <br/> |False  <br/> |A null value is allowed in the index field; index entry added.  <br/> |
|True or False  <br/> |True  <br/> |A null value isn't allowed in the index field; no index entry added.  <br/> |
   
## Example

This example sets the **IgnoreNulls** property of a new **Index** to **True** or **False** based on user input, and then demonstrates the effect on a **Recordset** with a record whose key field contains a **Null** value. 
  
```
Sub IgnoreNullsX() 
 
 Dim dbsNorthwind As Database 
 Dim tdfEmployees As TableDef 
 Dim idxNew As Index 
 Dim rstEmployees As Recordset 
 
 Set dbsNorthwind = OpenDatabase("Northwind.mdb") 
 Set tdfEmployees = dbsNorthwind!Employees 
 
 With tdfEmployees 
 ' Create a new Index object. 
 Set idxNew = .CreateIndex("NewIndex") 
 idxNew.Fields.Append idxNew.CreateField("Country") 
 
 ' Set the IgnoreNulls property of the new Index object 
 ' based on the user's input. 
 Select Case MsgBox("Set IgnoreNulls to True?", _ 
 vbYesNoCancel) 
 Case vbYes 
 idxNew.IgnoreNulls = True 
 Case vbNo 
 idxNew.IgnoreNulls = False 
 Case Else 
 dbsNorthwind.Close 
 End 
 End Select 
 
 ' Append the new Index object to the Indexes 
 ' collection of the Employees table. 
 .Indexes.Append idxNew 
 .Indexes.Refresh 
 End With 
 
 Set rstEmployees = _ 
 dbsNorthwind.OpenRecordset("Employees") 
 
 With rstEmployees 
 ' Add a new record to the Employees table. 
 .AddNew 
 !FirstName = "Gary" 
 !LastName = "Haarsager" 
 .Update 
 
 ' Use the new index to set the order of the records. 
 .Index = idxNew.Name 
 .MoveFirst 
 
 Debug.Print "Index = " &amp; .Index &amp; _ 
 ", IgnoreNulls = " &amp; idxNew.IgnoreNulls 
 Debug.Print " Country - Name" 
 
 ' Enumerate the Recordset. The value of the 
 ' IgnoreNulls property will determine if the newly 
 ' added record appears in the output. 
 Do While Not .EOF 
 Debug.Print " " &amp; _ 
 IIf(IsNull(!Country), "[Null]", !Country) &amp; _ 
 " - " &amp; !FirstName &amp; " " &amp; !LastName 
 .MoveNext 
 Loop 
 
 ' Delete new record because this is a demonstration. 
 .Index = "" 
 .Bookmark = .LastModified 
 .Delete 
 .Close 
 End With 
 
 ' Delete new Index because this is a demonstration. 
 tdfEmployees.Indexes.Delete idxNew.Name 
 dbsNorthwind.Close 
 
End Sub 

```


