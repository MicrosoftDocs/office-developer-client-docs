---
title: "Recordset.Type Property (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: d841b088-50bf-16d9-33e0-2140050e1ac6

description: "Sets or returns a value that indicates the operational type or data type of an object. Read-only Integer ."
---

# Recordset.Type Property (DAO)

Sets or returns a value that indicates the operational type or data type of an object. Read-only **Integer**. 
  
## Syntax

 *expression*  . **Type**
  
 *expression*  A variable that represents a **Recordset** object. 
  
## Remarks

For a **Recordset** object, the possible settings and return values are as follows. 
  
|**Constant**|**Recordset type**|
|:-----|:-----|
|**dbOpenTable** <br/> |Table (Microsoft Access workspaces only)  <br/> |
|**dbOpenDynamic** <br/> |Dynamic (ODBCDirect workspaces only)  <br/> > [!NOTE]> ODBCDirect workspaces are not supported in Microsoft Access 2013. Use ADO if you want to access external data sources without using the Microsoft Access database engine.           |
|**dbOpenDynaset** <br/> |Dynaset  <br/> |
|**dbOpenSnapshot** <br/> |Snapshot  <br/> |
|**dbOpenForwardOnly** <br/> |Forward-only  <br/> |
   

