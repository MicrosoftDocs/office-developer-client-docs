---
title: "DBEngine.CreateWorkspace Method (DAO)"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
f1_keywords:
- dao360.chm1052966
  
localization_priority: Normal
ms.assetid: a7d73771-9420-0448-99e6-d6c4aa78683a
description: "Creates a new Workspace object."
---

# DBEngine.CreateWorkspace Method (DAO)

Creates a new **[Workspace](workspace-object-dao.md)** object. 
  
## Syntax

 *expression*  . **CreateWorkspace**( ** *Name* **, ** *UserName* **, ** *Password* **, ** *UseType* ** ) 
  
 *expression*  A variable that represents a **DBEngine** object. 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Name_ <br/> |Required  <br/> |**String** <br/> |A **String** that uniquely names the new **Workspace** object. See the **[Name](connection-name-property-dao.md)** property for details on valid **Workspace** names.  <br/> |
| _UserName_ <br/> |Required  <br/> |**String** <br/> |A **String** that identifies the owner of the new **Workspace** object. See the **UserName** property for more information.  <br/> |
| _Password_ <br/> |Required  <br/> |**String** <br/> |A **String** containing the password for the new **Workspace** object. The password can be up to 20 characters long and can include any characters except ASCII character 0 (null).  <br/> > [!NOTE]> Use strong passwords that combine upper- and lowercase letters, numbers, and symbols. Weak passwords don't mix these elements. Strong password: Y6dh!et5. Weak password: House27. Use a strong password that you can remember so that you don't have to write it down.           |
| _UseType_ <br/> |Optional  <br/> |**Variant** <br/> |One of the **[WorkspaceTypeEnum](workspacetypeenum-enumeration-dao.md)** values.  <br/> > [!NOTE]> ODBCDirect workspaces are not supported in Microsoft Access 2013. Setting the type argument to **dbUseODBC** will result in a run-time error. Use ADO if you want to access external data sources without using the Microsoft Access database engine.           |
   
### Return Value

Workspace
  
## Remarks

Once you use the **CreateWorkspace** method to create a new **Workspace** object, a **Workspace** session is started, and you can refer to the **Workspace** object in your application. 
  
 **Workspace** objects aren't permanent, and you can't save them to disk. Once you create a **Workspace** object, you can't alter any of its property settings, except for the **Name** property, which you can modify before appending the **Workspace** object to the **[Workspaces](workspaces-collection-dao.md)** collection. 
  
You don't have to append the new **Workspace** object to a collection before you can use it. You append a newly created **Workspace** object only if you need to refer to it through the **Workspaces** collection. 
  
To remove a **Workspace** object from the **Workspaces** collection, close all open databases and connections and then use the **[Close](connection-close-method-dao.md)** method on the **Workspace** object. 
  
## Example

This example uses the **CreateWorkspace** method to createMicrosoft Access workspace. It then lists the properties of the workspace. 
  
```
Sub CreateWorkspaceX() 
 
   Dim wrkAcc As Workspace 
   Dim wrkLoop As Workspace 
   Dim prpLoop As Property 
 
   DefaultType = dbUseJet 
   ' Create an unnamed Workspace object of the type  
   ' specified by the DefaultType property of DBEngine  
   ' (dbUseJet). 
   Set wrkAcc = CreateWorkspace("", "admin", "") 
 
   ' Enumerate Workspaces collection. 
   Debug.Print "Workspace objects in Workspaces collection:" 
   For Each wrkLoop In Workspaces 
      Debug.Print "  " &amp; wrkLoop.Name 
   Next wrkLoop 
 
   With wrkAcc 
      ' Enumerate Properties collection of Microsoft Access  
      ' workspace. 
      Debug.Print _ 
         "Properties of unnamed Microsoft Access workspace" 
      On Error Resume Next 
      For Each prpLoop In .Properties 
         Debug.Print "  " &amp; prpLoop.Name &amp; " = " &amp; prpLoop 
      Next prpLoop 
      On Error GoTo 0 
   End With 
 
   wrkAcc.Close 
 
End Sub 
 
```

