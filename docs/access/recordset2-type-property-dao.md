---
title: "Recordset2.Type Property (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- dao360.chm1052880
  
localization_priority: Normal
ms.assetid: 9bec543e-7f59-ea59-dc79-41d0e08b5ab6

description: "Sets or returns a value that indicates the operational type or data type of an object. Read-only Integer ."
---

# Recordset2.Type Property (DAO)

Sets or returns a value that indicates the operational type or data type of an object. Read-only **Integer**. 
  
## Syntax

 *expression*  . **Type**
  
 *expression*  A variable that represents a **Recordset2** object. 
  
## Remarks

For a **Recordset** object, the possible settings and return values are as follows. 
  
|**Constant**|**Recordset type**|
|:-----|:-----|
|**dbOpenTable** <br/> |Table (Microsoft Access workspaces only)  <br/> |
|**dbOpenDynamic** <br/> |Dynamic (ODBCDirect workspaces only)  <br/> > [!NOTE]> ODBCDirect workspaces are not supported in Microsoft Access 2013. Use ADO if you want to access external data sources without using the Microsoft Access database engine.           |
|**dbOpenDynaset** <br/> |Dynaset  <br/> |
|**dbOpenSnapshot** <br/> |Snapshot  <br/> |
|**dbOpenForwardOnly** <br/> |Forward-only  <br/> |
   

