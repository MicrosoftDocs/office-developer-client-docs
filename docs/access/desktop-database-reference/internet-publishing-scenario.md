---
title: Internet publishing scenario
TOCTitle: Internet publishing scenario
ms:assetid: 25a3fa8b-86ec-9e72-5e62-bf0d849479b7
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249024(v=office.15)
ms:contentKeyID: 48543790
ms.date: 09/18/2015
mtps_version: v=office.15
localization_priority: Normal
---

# Internet publishing scenario

**Applies to**: Access 2013, Office 2013

This code example demonstrates how to use ADO with the Microsoft OLE DB Provider for Internet Publishing. In this scenario, you will create a Visual Basic application that uses **Recordset**, **Record**, and **Stream** objects to display the contents of resources published with the Internet Publishing Provider.

The following steps are necessary to create this scenario: 

1. Set up the Visual Basic project.
2. Initialize the Main list box.
3. Populate the Fields list box.
4. Populate the Details text box.

## Step 1: Set up the Visual Basic project

In this scenario, it is assumed that you have Microsoft Visual Basic 6.0 or later, ADO 2.5 or later, and the Microsoft OLE DB Provider for Internet Publishing installed on your system.

### Create an ADO project

1.  In Microsoft Visual Basic, create a new Standard EXE project.

2.  From the **Project** menu, choose **References**.

3.  Select **Microsoft ActiveX Data Objects 2.5 Library**, and then click **OK**.

### Insert controls on the main form

1.  Add a ListBox control to Form1. Set its **Name** property to **lstMain**.

2.  Add another ListBox control to Form1. Set its **Name** property to **lstDetails**.

3.  Add a TextBox control to Form1. Set its **Name** property to **txtDetails**.

## Step 2: Initialize the Main list box

### Declare global Record and Recordset objects

- Insert the following code into the (General) (Declarations) for Form1:
    
   ```vb 
     
    Option Explicit 
    Dim grec As Record 
    Dim grs As Recordset 
   ```
    
   This code declares global object references for **Record** and **Recordset** objects that will be used later in this scenario.

### Connect to a URL and populate lstMain

- Insert the following code into the Form Load event handler for Form1:
    
   ```vb 
     
    Private Sub Form_Load() 
        Set grec = New Record 
        Set grs = New Recordset 
        grec.Open "", "URL=https://servername/foldername/", , _ 
            adOpenIfExists Or adCreateCollection 
        Set grs = grec.GetChildren 
        While Not grs.EOF 
            lstMain.AddItem grs(0) 
            grs.MoveNext 
        Wend 
    End Sub 
   ```
    
   This code instantiates the global **Record** and **Recordset** objects. The **Record** `grec` is opened with a URL specified as the **ActiveConnection**. If the URL exists, it is opened; if it does not already exist, it is created. 
   
   Note that you should replace `https://servername/foldername/` with a valid URL from your environment. 
   
   The **Recordset** `grs` is opened on the children of the **Record** `grec`. The lstMain is then populated with the file names of the resources published to the URL.

## Step 3: Populate the Fields list box

- Insert the following code into the Click event handler of lstMain:

   ```vb 
    
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

   This code declares and instantiates local **Record** and **Recordset** objects `rec` and `rs`respectively.

   The row corresponding to the resource selected in lstMain is made the current row of `grs`. The **Details** list box is then cleared and `rec` is opened with the current row of `grs` as the source.

   If the resource is a collection record (as specified by **RecordType**), the local **Recordset** `rs` is opened on the children of `rec`. lstDetails is then filled with the values from the rows of `rs`.

   If the resource is a simple record, `recFields` is called. For more information about `recFields`, see the next step.

   No code is implemented if the resource is a structured document.

## Step 4: Populate the Details text box

- Create a new subroutine named `recFields` and insert the following code:

   ```vb 
    
    Sub recFields(r As Record, l As ListBox, t As TextBox) 
        Dim f As Field 
        Dim s As Stream 
        Set s = New Stream 
        Dim str As String 
        
        For Each f In r.Fields 
            l.AddItem f.Name & ": " & f.Value 
        Next 
        t.Text = "" 
        If r!RESOURCE_CONTENTCLASS = "text/plain" Then 
            s.Open r, adModeRead, adOpenStreamFromRecord 
            str = s.ReadText(1) 
            s.Position = 0 
            If Asc(Mid(str, 1, 1)) = 63 Then '//63 = "?" 
                s.Charset = "ascii" 
                s.Type = adTypeText 
            End If 
            t.Text = s.ReadText(adReadAll) 
        End If 
    End Sub 
   ```

   This code populates lstDetails with the fields and values of the simple record passed to `recFields`. If the resource is a text file, a text **Stream** is opened from the resource record. The code determines if the character set is ASCII, and copies the **Stream** contents into `txtDetails`.

