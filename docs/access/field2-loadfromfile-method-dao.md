---
title: "Field2.LoadFromFile Method (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- dao360.chm1101190
  
localization_priority: Normal
ms.assetid: 8ffe4636-d4da-0579-f4b5-14f423647562
description: "Loads the specified file from disk."
---

# Field2.LoadFromFile Method (DAO)

Loads the specified file from disk.
  
## Version Information

Version Added: Access 2007 
  
## Syntax

 *expression*  . **LoadFromFile**( ** *FileName* ** ) 
  
 *expression*  A variable that represents a **Field2** object. 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _FileName_ <br/> |Required  <br/> |**String** <br/> |The fully qualified path of the file to that you want to load.  <br/> |
   
## Example

The following code snippet uses the **LoadFromFile** method to load an employee's picture from disk. 
  
```
   '  Instantiate the parent recordset.  
   Set rsEmployees = db.OpenRecordset("Employees") 
  
   … Code to move to desired employee 
  
   ' Activate edit mode. 
   rsEmployees.Edit 
  
   ' Instantiate the child recordset. 
   Set rsPictures = rsEmployees.Fields("Pictures").Value  
  
   ' Add a new attachment. 
   rsPictures.AddNew 
   rsPictures.Fields("FileData").LoadFromFile "EmpPhoto39392.jpg" 
   rsPictures.Update 
  
   ' Update the parent record 
   rsEmployees.Update 

```

The following example shows how to add files from a specified folder path to an attachment field.
  
 **Sample code provided by:** The [Microsoft Access 2010 Programmer's Reference](http://www.wrox.com/WileyCDA/WroxTitle/Access-2010-Programmer-s-Reference.productCd-0470591668.mdl) | [About the Contributors](#AboutContributors)
  
```
Public Function LoadAttachments(strPath As String, Optional strPattern As String = "*.*") As Long
    Dim dbs As DAO.Database
    Dim rst As DAO.Recordset2
    Dim rsA As DAO.Recordset2
    Dim fld  As DAO.Field2
    Dim strFile As String
    
    'Get the database, recordset, and attachment field
    Set dbs = CurrentDb
    Set rst = dbs.OpenRecordset("tblAttachments")
    Set fld = rst("Attachments")
    
    'Navigate through the table
    Do While Not rst.EOF
    
        'Get the recordset for the Attachments field
        Set rsA = fld.Value
        
        'Load all attachments in the specified directory
        strFile = Dir(strPath &amp; "\*.*")
        
        rst.Edit
        Do While Len(strFile) > 0
            'Add a new attachment that matches the pattern.
            'Pass "" to match all files.
            If strFile Like strPattern Then
                rsA.AddNew
                rsA("FileData").LoadFromFile strPath &amp; "\" &amp; strFile
                rsA.Update
                
                'Increment the number of files added
                LoadAttachments = LoadAttachments + 1
            End If
            strFile = Dir
        Loop
        rsA.Close
        
        rst.Update
        'Next record
        rst.MoveNext
    Loop
    
    rst.Close
    dbs.Close
    
    Set fld = Nothing
    Set rsA = Nothing
    Set rst = Nothing
    Set dbs = Nothing
End Function
```

## About the Contributors
<a name="AboutContributors"> </a>

Wrox Press is driven by the Programmer to Programmer philosophy. Wrox books are written by programmers for programmers, and the Wrox brand means authoritative solutions to real-world programming problems. 
  

