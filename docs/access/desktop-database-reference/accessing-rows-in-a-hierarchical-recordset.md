---
title: Accessing Rows in a Hierarchical Recordset
TOCTitle: Accessing Rows in a Hierarchical Recordset
ms:assetid: db59b152-b780-539c-17ef-462e8adfb26e
ms:mtpsurl: https://msdn.microsoft.com/library/JJ250106(v=office.15)
ms:contentKeyID: 48548104
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Accessing Rows in a Hierarchical Recordset


**Applies to**: Access 2013 | Office 2013

The following example shows the steps necessary to access rows in a hierarchical [Recordset](recordset-object-ado.md):

1.  **Recordset** objects from the authors and titleauthor tables are related by author ID.

2.  The outer loop displays each author's first and last name, state, and identification.

3.  The appended **Recordset** for each row is retrieved from the **Fields** collection and assigned to *rstTitleAuthor*.

4.  The inner loop displays four fields from each row in the appended **Recordset**.

(The [StayInSync](stayinsync-property-ado.md) property is set to FALSE for purposes of illustration — so you can see the chapter change explicitly in each iteration of the outer loop. However, the example will be more efficient if the assignment in step 3 is moved before the first line in step 2, so that the assignment is performed only once. Then set the **StayInSync** property to TRUE, so that *rstTitleAuthor* will implicitly and automatically change to the corresponding chapter whenever *rst* moves to a new row.)

**Example**

```vb 
 
Sub datashape() 
 Dim cnn As New ADODB.Connection 
 Dim rst As New ADODB.Recordset 
 Dim rstTitleAuthor As New ADODB.Recordset 
 
 cnn.Provider = "MSDataShape" 
 cnn.Open "Data Provider=MSDASQL;" & _ 
 "Data Source=SRV;" & _ 
 "User Id=MyUserName;Password=MyPassword;Database=Pubs" 
' STEP 1 
 rst.StayInSync = FALSE 
 rst.Open "SHAPE {select * from authors} " & _ 
 "APPEND ({select * from titleauthor} " & _ 
 "RELATE au_id TO au_id) AS chapTitleAuthor", _ 
 cnn 
' STEP 2 
 While Not rst.EOF 
 Debug.Print rst("au_fname"), rst("au_lname"), _ 
 rst("state"), rst("au_id") 
' STEP 3 
 Set rstTitleAuthor = rst("chapTitleAuthor").Value 
' STEP 4 
 While Not rstTitleAuthor.EOF 
 Debug.Print rstTitleAuthor(0), rstTitleAuthor(1), _ 
 rstTitleAuthor(2), rstTitleAuthor(3) 
 rstTitleAuthor.MoveNext 
 Wend 
 rst.MoveNext 
 Wend 
End Sub 
```

