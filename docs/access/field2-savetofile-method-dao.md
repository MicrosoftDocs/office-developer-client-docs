---
title: "Field2.SaveToFile Method (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- dao360.chm1101191
  
localization_priority: Normal
ms.assetid: 250f9596-1a03-471d-96f9-718cd57dc94f
description: "Saves an attachment to disk."
---

# Field2.SaveToFile Method (DAO)

Saves an attachment to disk.
  
## Version Information

Version Added: Access 2007 
  
## Syntax

 *expression*  . **SaveToFile**( ** *FileName* ** ) 
  
 *expression*  A variable that represents a **Field2** object. 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _FileName_ <br/> |Required  <br/> |**String** <br/> |The fully qualified path of the file to which you want to save the attachment.  <br/> |
   
## Example

The following code snippet illustrates how to use the **SaveToFile** method to save all of the attachments for a specific employee to disk. 
  
```
'  Instantiate the parent recordset.  
   Set rsEmployees = db.OpenRecordset("Employees") 
  
   … Code to move to desired employee 
  
   ' Instantiate the child recordset. 
   Set rsPictures = rsEmployees.Fields("Pictures").Value  
 
   '  Loop through the attachments. 
   While Not rsPictures.EOF 
  
      '  Save current attachment to disk in the "My Documents" folder. 
      rsPictures.Fields("FileData").SaveToFile _ 
                  "C:\Documents and Settings\Username\My Documents" 
      rsPictures.MoveNext 
   Wend 

```

The following example shows how to save the files stored in an attachment field to the specified folder path.
  
 **Sample code provided by:** The [Microsoft Access 2010 Programmer's Reference](http://www.wrox.com/WileyCDA/WroxTitle/Access-2010-Programmer-s-Reference.productCd-0470591668.mdl) | [About the Contributors](#AboutContributors)
  
```
Public Function SaveAttachments(strPath As String, Optional strPattern As String = "*.*") As Long
    Dim dbs As DAO.Database
    Dim rst As DAO.Recordset2
    Dim rsA As DAO.Recordset2
    Dim fld As DAO.Field2
    Dim strFullPath As String
    
    'Get the database, recordset, and attachment field
    Set dbs = CurrentDb
    Set rst = dbs.OpenRecordset("tblAttachments")
    Set fld = rst("Attachments")
    
    'Navigate through the table
    Do While Not rst.EOF
    
        'Get the recordset for the Attachments field
        Set rsA = fld.Value
        
        'Save all attachments in the field
        Do While Not rsA.EOF
            If rsA("FileName") Like strPattern Then
                strFullPath = strPath &amp; "\" &amp; rsA("FileName")
                
                'Make sure the file does not exist and save
                If Dir(strFullPath) = "" Then
                    rsA("FileData").SaveToFile strFullPath
                End If
                
                'Increment the number of files saved
                SaveAttachments = SaveAttachments + 1
            End If
            
            'Next attachment
            rsA.MoveNext
        Loop
        rsA.Close
        
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
  

