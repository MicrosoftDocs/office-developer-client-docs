﻿---
title: Address Book Navigation Buttons
TOCTitle: Address Book Navigation Buttons
ms:assetid: 4ec32c08-5b35-8dce-23ec-0daa4db551cf
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249253(v=office.15)
ms:contentKeyID: 48544765
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Address Book Navigation Buttons


**Applies to**: Access 2013 | Office 2013

The Address Book application displays the navigation buttons at the bottom of the Web page. You can use the navigation buttons to navigate through the data in the HTML grid display by selecting either the first or last row of data, or rows adjacent to the current selection.

## Navigation Sub Procedures

The Address Book application contains several procedures that allow users to click the **First**, **Next**, **Previous**, and **Last** buttons to move around the data.

For example, clicking the **First** button activates the VBScript First\_OnClick Sub procedure. The procedure executes a [MoveFirst](movefirst-movelast-movenext-and-moveprevious-methods-rds.md) method, which makes the first row of data the current selection. Clicking the **Last** button activates the Last\_OnClick Sub procedure, which invokes the [MoveLast](movefirst-movelast-movenext-and-moveprevious-methods-rds.md) method, making the last row of data the current selection. The remaining navigation buttons work in a similar fashion.

``` 
 
' Move to the first record in the bound Recordset. 
Sub First_OnClick 
 DC1.Recordset.MoveFirst 
End Sub 
 
' Move to the next record from the current position 
' in the bound Recordset. 
Sub Next_OnClick 
 If Not DC1.Recordset.EOF Then ' Cannot move beyond bottom record. 
 DC1.Recordset.MoveNext 
 Exit Sub 
 End If 
End Sub 
 
' Move to the previous record from the current position in the bound 
' Recordset. 
Sub Prev_OnClick 
 If Not DC1.Recordset.BOF Then ' Cannot move beyond top record. 
 DC1.Recordset.MovePrevious 
 Exit Sub 
 End If 
End Sub 
 
' Move to the last record in the bound Recordset. 
Sub Last_OnClick 
 DC1.Recordset.MoveLast 
End Sub 
```

