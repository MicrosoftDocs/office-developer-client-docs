---
title: "Provider Support for ADOX"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 32ea3236-d69f-df94-1685-d8791aeb9e0f
description: "Certain features of ADOX are unsupported, depending upon your OLE DB data provider. ADOX is fully supported with the OLE DB Provider for Microsoft Jet. The unsupported features with the Microsoft OLE DB Provider for SQL Server, the Microsoft OLE DB Provider for ODBC, or the Microsoft OLE DB Provider for Oracle are listed below. ADOX is not supported by any other Microsoft OLE DB providers."
---

# Provider Support for ADOX

Certain features of ADOX are unsupported, depending upon your OLE DB data provider. ADOX is fully supported with the [OLE DB Provider for Microsoft Jet](microsoft-ole-db-provider-for-microsoft-jet.md). The unsupported features with the [Microsoft OLE DB Provider for SQL Server](microsoft-ole-db-provider-for-sql-server.md), the [Microsoft OLE DB Provider for ODBC](microsoft-ole-db-provider-for-odbc.md), or the [Microsoft OLE DB Provider for Oracle](microsoft-ole-db-provider-for-oracle.md) are listed below. ADOX is not supported by any other Microsoft OLE DB providers. 
  
## Microsoft OLE DB Provider for SQL Server

|**Object or Collection**|**Usage Restriction**|
|:-----|:-----|
|**Catalog** object  <br/> |The **Create** method is not supported.  <br/> |
|**Tables** collection  <br/> |Properties are read/write prior to object creation, and read-only when referencing an existing object.  <br/> |
|**Views** collection  <br/> |**Views** is not supported.  <br/> |
|**Procedures** collection  <br/> |The **Append** and **Delete** methods are not supported.  <br/> |
|**Procedure** object  <br/> |The **Command** property is not supported.  <br/> |
|**Keys** collection  <br/> |The **Append** and **Delete** methods are not supported.  <br/> |
|**Users** collection  <br/> |**Users** is not supported.  <br/> |
|**Groups** collection  <br/> |**Groups** is not supported.  <br/> |
   
## Microsoft OLE DB Provider for ODBC

|**Object or Collection**|**Usage Restriction**|
|:-----|:-----|
|**Catalog** object  <br/> |The **Create** method is not supported.  <br/> |
|**Tables** collection  <br/> |The **Append** and **Delete** methods are not supported. Properties are read/write prior to object creation, and read-only when referencing an existing object.  <br/> |
|**Procedures** collection  <br/> |The **Append** and **Delete** methods are not supported.  <br/> |
|**Procedure** object  <br/> |The **Command** property is not supported.  <br/> |
|**Indexes** collection  <br/> |The **Append** and **Delete** methods are not supported.  <br/> |
|**Keys** collection  <br/> |The **Append** and **Delete** methods are not supported.  <br/> |
|**Users** collection  <br/> |**Users** is not supported.  <br/> |
|**Groups** collection  <br/> |**Groups** is not supported.  <br/> |
   
## Microsoft OLE DB Provider for Oracle

|**Object or Collection**|**Usage Restriction**|
|:-----|:-----|
|**Catalog** object  <br/> |The **Create** method is not supported.  <br/> |
|**Tables** collection  <br/> |The **Append** and **Delete** methods are not supported. Properties are read/write prior to object creation, and read-only when referencing an existing object.  <br/> |
|**Views** collection  <br/> |The **Append** and **Delete** methods are not supported.  <br/> |
|**View** object  <br/> |The **Command** property is not supported.  <br/> |
|**Procedures** object  <br/> |The **Append** and **Delete** methods are not supported.  <br/> |
|**Procedure** object  <br/> |The **Command** property is not supported.  <br/> |
|**Indexes** collection  <br/> |The **Append** and **Delete** methods are not supported.  <br/> |
|**Keys** collection  <br/> |The **Append** and **Delete** methods are not supported.  <br/> |
|**Users** collection  <br/> |**Users** is not supported.  <br/> |
|**Groups** collection  <br/> |**Groups** is not supported.  <br/> |
   

