---
title: "Customization File Connect Section"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 037abfb4-798d-4b09-6133-356969aee95c
description: "The default behavior of the handler is to deny all connections. The connect section specifies exceptions to that behavior. For example, if all the connect sections were absent or empty, then by default no connections could be made."
---

# Customization File Connect Section

The default behavior of the handler is to deny all connections. The **connect** section specifies exceptions to that behavior. For example, if all the **connect** sections were absent or empty, then by default no connections could be made. 
  
The **connect** section can contain: 
  
- A default access entry that specifies the default read and write operations allowed on this connection. If there is no default access entry in the section, the section will be ignored.
    
- A new connection string that replaces the client connection string.
    
## Syntax

A default access entry is of the form:
  
```
Access=accessRight
```

A replacement connection string entry is of the form:
  
```
Connect=connectionString
```

|**Part**|**Description**|
|:-----|:-----|
|**Connect** <br/> |A literal string that indicates this is a connection string entry.  <br/> |
|***connectionString* ** <br/> |A string that replaces the whole client connection string.  <br/> |
|**Access** <br/> |A literal string that indicates this is an access entry.  <br/> |
|***accessRight* ** <br/> | One of the following access rights:  <br/> **NoAccess** — User cannot access the data source.  <br/> **ReadOnly** — User can read the data source.  <br/> **ReadWrite** — User can read or write to the data source.  <br/> |
   
If you want to allow any connection (in effect, disabling the default handler behavior), set the access entry in the **connect default** section to , and delete or comment out any other **connect** *identifier*  section. 
  

