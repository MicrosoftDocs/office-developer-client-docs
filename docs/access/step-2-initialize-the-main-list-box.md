---
title: "Step 2 Initialize the Main List Box"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 81e4dcfd-6ee0-b5f9-9ea3-026c38c26bf0

---

# Step 2: Initialize the Main List Box

## Step 2: Initialize the Main List Box

 **To declare global Record and Recordset objects**
  
- Insert the following code into the (General) (Declarations) for Form1:
    
  ```
   
  Option Explicit 
  Dim grec As Record 
  Dim grs As Recordset 
  
  ```

     This code declares global object references for **Record** and **Recordset** objects that will be used later in this scenario. 
    
 **To connect to a URL and populate lstMain**
  
- Insert the following code into the Form Load event handler for Form1:
    
  ```
   
  Private Sub Form_Load() 
      Set grec = New Record 
      Set grs = New Recordset 
      grec.Open "", "URL=http://servername/foldername/", , _ 
          adOpenIfExists Or adCreateCollection 
      Set grs = grec.GetChildren 
      While Not grs.EOF 
          lstMain.AddItem grs(0) 
          grs.MoveNext 
      Wend 
  End Sub 
  
  ```

     This code instantiates the global **Record** and **Recordset** objects. The **Record**,  `grec`, is opened with a URL specified as the **ActiveConnection**. If the URL exists, it is opened; if it does not already exist, it is created. Note that you should replace "http://servername/foldername/" with a valid URL from your environment. The **Recordset**,  `grs`, is opened on the children of the **Record**,  `grec`. Then lstMain is populated with the file names of the resources published to the URL.
    

