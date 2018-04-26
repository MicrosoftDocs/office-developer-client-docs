---
title: "Document Members (DAO)"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 8de770e6-e4d1-372a-3ef8-8539c921b41f
description: "A Document object includes information about one instance of an object. The object can be a database, saved table, query, or relationship (Microsoft Access database engine databases only)."
---

# Document Members (DAO)

A **Document** object includes information about one instance of an object. The object can be a database, saved table, query, or relationship (Microsoft Access database engine databases only). 
  
## Methods

|**Name**|**Description**|
|:-----|:-----|
|**[CreateProperty](document-createproperty-method-dao.md)** <br/> |Creates a new user-defined **[Property](property-object-dao.md)** object (Microsoft Access workspaces only).  <br/> |
   
## Properties

|**Name**|**Description**|
|:-----|:-----|
|**[Container](document-container-property-dao.md)** <br/> |Returns the name of the **[Container](container-object-dao.md)** object to which a **Document** object belongs (Microsoft Access workspaces only). .  <br/> |
|**[DateCreated](document-datecreated-property-dao.md)** <br/> | Returns the date and time that an object was created. Read-only **Variant**.  <br/> |
|**[LastUpdated](document-lastupdated-property-dao.md)** <br/> |Returns the date and time of the most recent change made to an object. Read-only **Variant**.  <br/> |
|**[Name](document-name-property-dao.md)** <br/> |Returns the name of the specified object. Read-only **String**.  <br/> |
|**[Properties](document-properties-property-dao.md)** <br/> |Returns the **[Properties](properties-collection-dao.md)** collection of the specified object. Read-only.  <br/> |
   

