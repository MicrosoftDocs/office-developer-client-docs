---
title: "Step 3 Populate the Fields List Box"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: b304d3a1-2237-d6f5-6e32-c6e5b9946e10

---

# Step 3: Populate the Fields List Box

## Step 3: Populate the Fields List Box

 **To populate the Fields list box**
  
Insert the following code into the Click event handler of lstMain:
  
```
 
Private Sub lstMain_Click() 
    Dim rec As Record 
    Dim rs As Recordset 
    Set rec = New Record 
    Set rs = New Recordset 
    grs.MoveFirst 
    grs.Move lstMain.ListIndex 
    lstDetails.Clear 
    rec.Open grs 
    Select Case rec.RecordType 
        Case adCollectionRecord: 
            Set rs = rec.GetChildren 
            While Not rs.EOF 
                lstDetails.AddItem rs(0) 
                rs.MoveNext 
            Wend 
        Case adSimpleRecord: 
            recFields rec, lstDetails, txtDetails 
             
        Case adStructDoc: 
    End Select 
     
End Sub 

```

This code declares and instantiates local **Record** and **Recordset** objects,  `rec` and and  `rs`, respectively.
  
The row corresponding to the resource selected in lstMain is made the current row of  `grs`. Then the **Details** list box is cleared and  `rec` is opened with the current row of . Then the **Details** list box is cleared and  `rec` is opened with the current row of  `grs` as the source. 
  
If the resource is a collection record (as specified by **RecordType** ), the local **Recordset**,  `rs,` is opened on the children of  `rec`. Then lstDetails is filled with the values from the rows of is opened on the children of  `rec`. Then lstDetails is filled with the values from the rows of  `rs`.
  
If the resource is a simple record, recFields is called. For more information about recFields, see the next step.
  
No code is implemented if the resource is a structured document.
  

