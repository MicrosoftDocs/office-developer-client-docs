---
title: "HelloData A Simple ADO Application"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: c271abeb-8865-81f9-db8e-47d3db87ad30
description: "To lay the groundwork for an exploration of the ADO library, consider a simple ADO application calledHelloData.HelloData steps through each of the four major ADO operations (getting, examining, editing, and updating data). In order to focus on the fundamentals of ADO and prevent code clutter, minimal error handling is done in the example."
---

# HelloData: A Simple ADO Application

To lay the groundwork for an exploration of the ADO library, consider a simple ADO application called "HelloData." HelloData steps through each of the four major ADO operations (getting, examining, editing, and updating data). In order to focus on the fundamentals of ADO and prevent code clutter, minimal error handling is done in the example.
  
The application queries the Northwind sample database that is included with Microsoft SQL Server 2000.
  
 **To run HelloData**
  
1. Create a new Standard Executable Visual Basic Project that references the ADO 2.5 library.
    
2. Create four command buttons at the top of the form, setting the **Name** and **Caption** properties to the values shown in the table below. 
    
3. Below the buttons, add a **Microsoft DataGrid Control** (Msdatgrd.ocx). The Msdatgrd.ocx file comes with Visual Basic and is located in your \windows\system32 or \winnt\system32 directory. To add the DataGrid control to your Visual Basic toolbox pane, select **Components...** from the **Project** menu. Then check the box next to "Microsoft DataGrid Control 6.0 (SP3) (OLEDB)" and click **OK**. To add the control to the project, drag the DataGrid control from the Toolbox to the Visual Basic form. 
    
4. Create a **TextBox** on the form below the grid and set its properties as shown in the table. The form should look similar to the following figure when you are finished. 
    
5. Finally, copy the code listed in "[HelloData Code](hellodata-code.md)" and paste it into the code editor window of the form. Press **F5** to run the code. 
    
> [!NOTE]
> In the following example, and throughout the guide, the user id "MyId" with a password of "123aBc" is used to authenticate against the server. You should substitute these values with valid logon credentials for your server. Also, substitute the "MyServer" value with the name of your server. 
  
For a detailed description of the code, see "[HelloData Details](hellodata-details.md)."
  
|**Control Type**|**Property**|**Value**|
|:-----|:-----|:-----|
|Form  <br/> |Name  <br/> |Form1  <br/> |
|
  
 <br/> |Height  <br/> |6500  <br/> |
|
  
 <br/> |Width  <br/> |6500  <br/> |
|MS DataGrid  <br/> |Name  <br/> |grdDisplay1  <br/> |
|TextBox  <br/> |Name  <br/> |txtDisplay1  <br/> |
|
  
 <br/> |Multiline  <br/> |true  <br/> |
|Command Button  <br/> |Name  <br/> |cmdGetData  <br/> |
|
  
 <br/> |Caption  <br/> |Get Data  <br/> |
|Command Button  <br/> |Name  <br/> |cmdExamineData  <br/> |
|
  
 <br/> |Caption  <br/> |Examine Data  <br/> |
|Command Button  <br/> |Name  <br/> |cmdEditData  <br/> |
|
  
 <br/> |Caption  <br/> |Edit Data  <br/> |
|Command Button  <br/> |Name  <br/> |cmdUpdateData  <br/> |
|
  
 <br/> |Caption  <br/> |Update Data  <br/> |
   

