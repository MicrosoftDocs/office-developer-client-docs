---
title: Dealing with failed updates
TOCTitle: Dealing with failed updates
ms:assetid: f6f4914d-59b3-f3f2-b986-218e07ce5a1d
ms:mtpsurl: https://msdn.microsoft.com/library/JJ250258(v=office.15)
ms:contentKeyID: 48548752
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Dealing with failed updates

**Applies to**: Access 2013, Office 2013

## Dealing with Failed Updates

When an update concludes with errors, how you resolve the errors depends on the nature and severity of the errors and the logic of your application. However, if the database is shared with other users, a typical error is that someone else modifies the field before you do. This type of error is called a *conflict.* ADO detects this situation and reports an error.

If there are update errors, they will be trapped in an error-handling routine. Filter the **Recordset** with the **adFilterConflictingRecords** constant so that only the conflicting rows are visible. In this example, the error-resolution strategy is merely to print the author's first and last names (**au\_fname** and **au\_lname**).

The code to alert the user to the update conflict looks like this:

```vb 
 
objRs.Filter = adFilterConflictingRecords 
objRs.MoveFirst 
Do While Not objRst.EOF 
   Debug.Print "Conflict: Name =  "; objRs!au_fname; " "; objRs!au_lname 
   objRs.MoveNext 
Loop 
```

