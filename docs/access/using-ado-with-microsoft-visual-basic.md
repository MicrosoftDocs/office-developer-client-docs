---
title: "Using ADO with Microsoft Visual Basic"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 5e0fb2ec-42aa-e181-386f-099607ac7400
description: "Setting up an ADO project and writing ADO code is similar whether you use Visual Basic or Visual Basic for Applications. This topic addresses using ADO with both Visual Basic and Visual Basic for Applications and notes any differences."
---

# Using ADO with Microsoft Visual Basic

Setting up an ADO project and writing ADO code is similar whether you use Visual Basic or Visual Basic for Applications. This topic addresses using ADO with both Visual Basic and Visual Basic for Applications and notes any differences.
  
## Referencing the ADO Library

The ADO library must be referenced by your project.
  
 **To reference ADO from Microsoft Visual Basic**
  
1. In Visual Basic, from the **Project** menu, select **References...**. 
    
2. Select **Microsoft ActiveX Data Objects x.x Library** from the list. Verify that at least the following libraries are also selected: 
    
  - Visual Basic for Applications
    
  - Visual Basic runtime objects and procedures
    
  - Visual Basic objects and procedures
    
  - OLE Automation
    
3. Click **OK**. 
    
You can use ADO just as easily with Visual Basic for Applications, using Microsoft Access, for example.
  
 **To reference ADO from Microsoft Access**
  
1. In Microsoft Access, select or create a module from the **Modules** tab in the **Database** window. 
    
2. From the **Tools** menu, select **References...**. 
    
3. Select **Microsoft ActiveX Data Objects x.x Library** from the list. Verify that at least the following libraries are also selected: 
    
  - Visual Basic for Applications
    
  - Microsoft Access 11.0 Object Library (or later)
    
4. Click **OK**. 
    
## Creating ADO Objects in Visual Basic

To create an automation variable and an instance of an object for that variable, you can use two methods: **Dim** or **CreateObject**. 
  
## Dim

You can use the **New** keyword with **Dim** to declare and instantiate ADO objects in one step: 
  
```
 
Dim conn As New ADODB.Connection 

```

Alternately, the **Dim** statement declaration and object instantiation can also be two steps: 
  
```
 
Dim conn As ADODB.Connection 
Set conn = New ADODB.Connection 

```

> [!NOTE]
> It is not required to explicitly use the  `ADODB` progid with the **Dim** statement, assuming you have properly referenced the ADO library in your project. However, using it ensures that you won't have naming conflicts with other libraries. 
  
For example, if you include references to both ADO and DAO in the same project, you should include a qualifier to specify which object model to use when instantiating **Recordset** objects, as in the following code: 
  
 `Dim adoRS As ADODB.Recordset`
  
 `Dim daoRS As DAO.Recordset`
  
## CreateObject

With the **CreateObject** method, the declaration and object instantiation must be two discrete steps: 
  
```
 
Dim conn1 
Set conn1 = CreateObject("ADODB.Connection") As Object 

```

Objects instantiated with **CreateObject** are late-bound, which means that they are not strongly typed and command-line completion is disabled. However, it does allow you to skip referencing the ADO library from your project, and enables you to instantiate specific versions of objects. For example: 
  
```
 
Set conn1 = CreateObject("ADODB.Connection.2.0") As Object 

```

You could also accomplish this by specifically creating a reference to the ADO version 2.0 type library and creating the object.
  
Instantiating objects with the **CreateObject** method is typically slower than using the **Dim** statement. 
  
## Handling Events

In order to handle ADO events in Microsoft Visual Basic, you must declare a module-level variable using the **WithEvents** keyword. The variable can be declared only as part of a class module and must be declared at the module level. For a more complete discussion of handling ADO events, see [Chapter 7: Handling ADO Events](chapter-7-handling-ado-events.md).
  
## Visual Basic Examples

Many Visual Basic examples are included with the ADO documentation. For more information, see [ADO Code Examples in Microsoft Visual Basic](ado-code-examples-in-microsoft-visual-basic.md).
  

