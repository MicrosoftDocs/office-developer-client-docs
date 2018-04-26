---
title: "Customization File UserList Section"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: b60ba3b0-37d4-bb59-d3cd-2ab44d178b8a
description: "The userlist section pertains to the connect section with the same section identifier parameter."
---

# Customization File UserList Section

The **userlist** section pertains to the **connect** section with the same section  *identifier*  parameter. 
  
This section can contain a  *user access entry*  , which specifies access rights for the specified user and overrides the  *default*  *access entry*  in the matching **connect** section. 
  
## Syntax

A user access entry is of the form:
  
 *userName* **= *accessRights* **
  
|**Part**|**Description**|
|:-----|:-----|
| *userName*  <br/> |The  *user name*  of the person employing this connection. Valid user names are established with the IIS **Service Manager** dialog.  <br/> |
|***accessRights* ** <br/> | One of the following access rights:            <br/> **NoAccess** — User cannot access the data source.  <br/> **ReadOnly** — User can read the data source.  <br/> **ReadWrite** — User can read or write to the data source.  <br/> |
   

