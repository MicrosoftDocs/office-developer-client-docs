---
title: "Recordset.Seek Method (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- dao360.chm1053061
  
localization_priority: Normal
ms.assetid: ef83d909-c962-b016-7d33-36eacdc25c2c
description: "Locates the record in an indexed table-type Recordset object that satisfies the specified criteria for the current index and makes that record the current record (Microsoft Access workspaces only)."
---

# Recordset.Seek Method (DAO)

Locates the record in an indexed table-type **Recordset** object that satisfies the specified criteria for the current index and makes that record the current record (Microsoft Access workspaces only). 
  
## Syntax

 *expression*  . **Seek**( ** *Comparison* **, ** *Key1* **, ** *Key2* **, ** *Key3* **, ** *Key4* **, ** *Key5* **, ** *Key6* **, ** *Key7* **, ** *Key8* **, ** *Key9* **, ** *Key10* **, ** *Key11* **, ** *Key12* **, ** *Key13* ** ) 
  
 *expression*  A variable that represents a **Recordset** object. 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Comparison_ <br/> |Required  <br/> |**String** <br/> |One of the following string expressions: \<, \<=, =, \>=, or \>.  <br/> |
| _Key1, Key2...Key13_ <br/> |Required  <br/> |**Variant** <br/> |One or more values corresponding to fields in the **Recordset** object's current index, as specified by its **Index** property setting. You can use up to 13  _key_ arguments.  <br/> |
   
## Remarks

You must set the current index with the **Index** property before you use **Seek**. If the index identifies a nonunique key field, **Seek** locates the first record that satisfies the criteria. 
  
The **Seek** method searches through the specified key fields and locates the first record that satisfies the criteria specified by  _comparison_ and  _key1_. Once found, it makes that record current and sets the **NoMatch** property to **False**. If the **Seek** method fails to locate a match, the **NoMatch** property is set to **True**, and the current record is undefined. 
  
If  _comparison_ is equal (=), greater than or equal (>=), or greater than (>), **Seek** starts at the beginning of the index and searches forward. 
  
If comparison is less than (<) or less than or equal (<=), **Seek** starts at the end of the index and searches backward. However, if there are duplicate index entries at the end of the index, **Seek** starts at an arbitrary entry among the duplicates and then searches backward. 
  
You must specify values for all fields defined in the index. If you use **Seek** with a multiple-column index, and you don't specify a comparison value for every field in the index, then you cannot use the equal (=) operator in the comparison. That's because some of the criteria fields (  _key2_,  _key3_, and so on) will default to **Null**, which will probably not match. Therefore, the equal operator will work correctly only if you have a record which is all **null** except the key you're looking for. It's recommended that you use the greater than or equal (>=) operator instead. 
  
The  _key1_ argument must be of the same field data type as the corresponding field in the current index. For example, if the current index refers to a number field (such as Employee ID),  _key1_ must be numeric. Similarly, if the current index refers to a Text field (such as Last Name),  _key1_ must be a string. 
  
There doesn't have to be a current record when you use **Seek**. 
  
You can use the **[Indexes](indexes-collection-dao.md)** collection to enumerate the existing indexes. 
  
To locate a record in a dynaset- or snapshot-type **Recordset** that satisfies a specific condition that is not covered by existing indexes, use the **[Find](recordset-findfirst-method-dao.md)** methods. To include all records, not just those that satisfy a specific condition, use the **[Move](recordset-movefirst-method-dao.md)** methods to move from record to record. 
  
You can't use the **Seek** method on a linked table because you can't open linked tables as table-type **Recordset** objects. However, if you use the **[OpenDatabase](dbengine-opendatabase-method-dao.md)** method to directly open an installable ISAM (non-ODBC) database, you can use **Seek** on tables in that database. 
  
## Example

This example demonstrates the **Seek** method by allowing the user to search for a product based on an ID number. 
  
```
Sub SeekX() 
 
   Dim dbsNorthwind As Database 
   Dim rstProducts As Recordset 
   Dim intFirst As Integer 
   Dim intLast As Integer 
   Dim strMessage As String 
   Dim strSeek As String 
   Dim varBookmark As Variant 
 
   Set dbsNorthwind = OpenDatabase("Northwind.mdb") 
   ' You must open a table-type Recordset to use an index,  
   ' and hence the Seek method. 
   Set rstProducts = _ 
      dbsNorthwind.OpenRecordset("Products", dbOpenTable) 
 
   With rstProducts 
      ' Set the index. 
      .Index = "PrimaryKey" 
 
      ' Get the lowest and highest product IDs. 
      .MoveLast 
      intLast = !ProductID 
      .MoveFirst 
      intFirst = !ProductID 
 
      Do While True 
         ' Display current record information and ask user  
         ' for ID number. 
         strMessage = "Product ID: " &amp; !ProductID &amp; vbCr &amp; _ 
            "Name: " &amp; !ProductName &amp; vbCr &amp; vbCr &amp; _ 
            "Enter a product ID between " &amp; intFirst &amp; _ 
            " and " &amp; intLast &amp; "." 
         strSeek = InputBox(strMessage) 
 
         If strSeek = "" Then Exit Do 
 
         ' Store current bookmark in case the Seek fails. 
         varBookmark = .Bookmark 
 
         .Seek "=", Val(strSeek) 
 
         ' Return to the current record if the Seek fails. 
         If .NoMatch Then 
            MsgBox "ID not found!" 
            .Bookmark = varBookmark 
         End If 
      Loop 
 
      .Close 
   End With 
 
   dbsNorthwind.Close 
 
End Sub 

```

This example uses the **NoMatch** property to determine whether a **Seek** and a **FindFirst** were successful, and if not, to give appropriate feedback. The **SeekMatch** and **FindMatch** procedures are required for this procedure to run. 
  
```
Sub NoMatchX() 
 
   Dim dbsNorthwind As Database 
   Dim rstProducts As Recordset 
   Dim rstCustomers As Recordset 
   Dim strMessage As String 
   Dim strSeek As String 
   Dim strCountry As String 
   Dim varBookmark As Variant 
 
   Set dbsNorthwind = OpenDatabase("Northwind.mdb") 
   ' Default is dbOpenTable; required if Index property will  
   ' be used. 
   Set rstProducts = dbsNorthwind.OpenRecordset("Products") 
 
   With rstProducts 
      .Index = "PrimaryKey" 
 
      Do While True 
         ' Show current record information; ask user for  
         ' input. 
         strMessage = "NoMatch with Seek method" &amp; vbCr &amp; _ 
            "Product ID: " &amp; !ProductID &amp; vbCr &amp; _ 
            "Product Name: " &amp; !ProductName &amp; vbCr &amp; _ 
            "NoMatch = " &amp; .NoMatch &amp; vbCr &amp; vbCr &amp; _ 
            "Enter a product ID." 
         strSeek = InputBox(strMessage) 
         If strSeek = "" Then Exit Do 
 
         ' Call procedure that seeks for a record based on  
         ' the ID number supplied by the user. 
         SeekMatch rstProducts, Val(strSeek) 
      Loop 
 
      .Close 
   End With 
 
   Set rstCustomers = dbsNorthwind.OpenRecordset( _ 
      "SELECT CompanyName, Country FROM Customers " &amp; _ 
      "ORDER BY CompanyName", dbOpenSnapshot) 
 
   With rstCustomers 
 
      Do While True 
         ' Show current record information; ask user for  
         ' input. 
         strMessage = "NoMatch with FindFirst method" &amp; _ 
            vbCr &amp; "Customer Name: " &amp; !CompanyName &amp; _ 
            vbCr &amp; "Country: " &amp; !Country &amp; vbCr &amp; _ 
            "NoMatch = " &amp; .NoMatch &amp; vbCr &amp; vbCr &amp; _ 
            "Enter country on which to search." 
         strCountry = Trim(InputBox(strMessage)) 
         If strCountry = "" Then Exit Do 
 
         ' Call procedure that finds a record based on  
         ' the country name supplied by the user. 
         FindMatch rstCustomers, _ 
            "Country = '" &amp; strCountry &amp; "'" 
      Loop 
 
      .Close 
   End With 
 
   dbsNorthwind.Close 
 
End Sub 
 
Sub SeekMatch(rstTemp As Recordset, _ 
   intSeek As Integer) 
 
   Dim varBookmark As Variant 
   Dim strMessage As String 
 
   With rstTemp 
      ' Store current record location. 
      varBookmark = .Bookmark 
      .Seek "=", intSeek 
 
      ' If Seek method fails, notify user and return to the  
      ' last current record. 
      If .NoMatch Then 
         strMessage = _ 
            "Not found! Returning to current record." &amp; _ 
            vbCr &amp; vbCr &amp; "NoMatch = " &amp; .NoMatch 
         MsgBox strMessage 
         .Bookmark = varBookmark 
      End If 
 
   End With 
 
End Sub 
 
Sub FindMatch(rstTemp As Recordset, _ 
   strFind As String) 
 
   Dim varBookmark As Variant 
   Dim strMessage As String 
 
   With rstTemp 
      ' Store current record location. 
      varBookmark = .Bookmark 
      .FindFirst strFind 
 
      ' If Find method fails, notify user and return to the  
      ' last current record. 
      If .NoMatch Then 
         strMessage = _ 
            "Not found! Returning to current record." &amp; _ 
            vbCr &amp; vbCr &amp; "NoMatch = " &amp; .NoMatch 
         MsgBox strMessage 
         .Bookmark = varBookmark 
      End If 
 
   End With 
 
End Sub 

```

The following example shows how to use the **Seek** method to find a record in a linked table. 
  
 **Sample code provided by:** The [Microsoft Access 2010 Programmer's Reference](http://www.wrox.com/WileyCDA/WroxTitle/Access-2010-Programmer-s-Reference.productCd-0470591668.mdl) | [About the Contributors](#AboutContributors)
  
```
Sub TestSeek()
    ' Get the path to the external database that contains
    ' the tblCustomers table we're going to search.
    Dim strMyExternalDatabase
    Dim dbs    As DAO.Database
    Dim dbsExt As DAO.Database
    Dim rst    As DAO.Recordset
    Dim tdf    As DAO.TableDef
    
    Set dbs = CurrentDb()
    Set tdf = dbs.TableDefs("tblCustomers")
    strMyExternalDatabase = Mid(tdf.Connect, 11)
    
    'Open the database that contains the table that is linked
    Set dbsExt = OpenDatabase(strMyExternalDatabase)
    
    'Open a table-type recordset against the external table
    Set rst = dbsExt.OpenRecordset("tblCustomers", dbOpenTable)
    
    'Specify which index to search on
    rst.Index = "PrimaryKey"
    
    'Specify the criteria
    rst.Seek "=", 123
    
    'Check the result
    If rst.NoMatch Then
        MsgBox "Record not found."
    Else
        MsgBox "Customer name: " &amp; rst!CustName
    End If
    
    rst.Close
    dbs.Close
    dbsExt.Close
    Set rst = Nothing
    Set tdf = Nothing
    Set dbs = Nothing
    
End Sub
```

## About the Contributors
<a name="AboutContributors"> </a>

Wrox Press is driven by the Programmer to Programmer philosophy. Wrox books are written by programmers for programmers, and the Wrox brand means authoritative solutions to real-world programming problems. 
  

