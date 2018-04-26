---
title: "Parameter Members (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 38e19de8-5318-6077-13b1-10653069aaeb
description: "A Parameter object represents a value supplied to a query. The parameter is associated with a QueryDef object created from a parameter query."
---

# Parameter Members (DAO)

A **Parameter** object represents a value supplied to a query. The parameter is associated with a **QueryDef** object created from a parameter query. 
  
## Properties

|**Name**|**Description**|
|:-----|:-----|
|**[Direction](parameter-direction-property-dao.md)** <br/> |
> [!NOTE]
> ODBCDirect workspaces are not supported in Microsoft Access 2013. Use ADO if you want to access external data sources without using the Microsoft Access database engine. 
  
Sets or returns a value that indicates whether a **[Parameter](parameter-object-dao.md)** object represents an input parameter, an output parameter, both, or the return value from the procedure (ODBCDirect workspaces only).  <br/> |
|**[Name](parameter-name-property-dao.md)** <br/> |Returns the name of the specified object. Read-only **String**.  <br/> |
|**[Properties](parameter-properties-property-dao.md)** <br/> |Returns the **[Properties](properties-collection-dao.md)** collection of the specified object. Read-only.  <br/> |
|**[Type](parameter-type-property-dao.md)** <br/> |Sets or returns a value that indicates the operational type or data type of an object. Read/write **Integer**.  <br/> |
|**[Value](parameter-value-property-dao.md)** <br/> |Sets or returns the value of an object. Read/write **Variant**.  <br/> |
   

