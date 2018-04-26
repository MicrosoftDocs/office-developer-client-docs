---
title: "Microsoft OLE DB Provider for Oracle"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 97508e3f-077f-9b85-f4dd-8dd01a201aba
description: "The Microsoft OLE DB Provider for Oracle allows ADO to access Oracle databases."
---

# Microsoft OLE DB Provider for Oracle

The Microsoft OLE DB Provider for Oracle allows ADO to access Oracle databases.
  
## Connection String Parameters

To connect to this provider, set the  *Provider*  argument of the [ConnectionString](connectionstring-property-ado.md) property to: 
  
```
 
MSDAORA 

```

Reading the [Provider](provider-property-ado.md) property will return this string as well. 
  
If a join query with a keyset or dynamic cursor is executed in an Oracle database, an error occurs. Oracle only supports a static read-only cursor.
  
## Typical Connection String

A typical connection string for this provider is:
  
```
 
"Provider=MSDAORA;Data Source=serverName ;User ID=userName ; Password=userPassword ;" 

```

The string consists of these keywords:
  
|**Keyword**|**Description**|
|:-----|:-----|
|**Provider** <br/> |Specifies the OLE DB Provider for Oracle.  <br/> |
|**Data Source** <br/> |Specifies the name of a server.  <br/> |
|**User ID** <br/> |Specifies the user name.  <br/> |
|**Password** <br/> |Specifies the user password.  <br/> |
   
## Provider-Specific Connection Parameters

The provider supports several provider-specific connection parameters in addition to those defined by ADO. As with the ADO connection properties, these provider-specific properties can be set via the [Properties](properties-collection-ado.md) collection of a [Connection](connection-object-ado.md) or as part of the **ConnectionString**. 
  
These parameters are fully described in the OLE DB Programmer's Reference. (The [ADO Dynamic Property Index](ado-dynamic-property-index.md) provides a cross-reference between these parameter names and the corresponding OLE DB properties.) 
  
|**Parameter**|**Description**|
|:-----|:-----|
|**Window Handle** <br/> |Indicates the window handle to use to prompt for additional information.  <br/> |
|**Locale Identifier** <br/> |Indicates a unique 32-bit number (for example, 1033) that specifies preferences related to the user's language. These preferences indicate how dates and times are formatted, items are sorted alphabetically, strings are compared, and so on.  <br/> |
|**OLE DB Services** <br/> |Indicates a bitmask that specifies OLE DB services to enable or disable.  <br/> |
|**Prompt** <br/> |Indicates whether to prompt the user while a connection is being established.  <br/> |
|**Extended Properties** <br/> |A string containing provider-specific, extended connection information. Use this property only for provider-specific connection information that cannot be described through the property mechanism.  <br/> |
   

