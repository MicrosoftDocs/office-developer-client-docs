---
title: "Create Method (ADOX)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: d4072ee7-a0b9-7780-7be0-1d64b42b437c
---

# Create Method (ADOX)

Creates a new catalog.
  
## Syntax

 *Catalog*  . **Create** *ConnectString* 
  
## Parameters

-  *ConnectString* 
    
- A **String** value used to connect to the data source. 
    
## Remarks

The **Create** method creates and opens a new ADO [Connection](connection-object-ado.md) to the data source specified in  *ConnectString*  . If successful, the new **Connection** object is assigned to the [ActiveConnection](activeconnection-property-adox.md) property. 
  
An error will occur if the provider does not support creating new catalogs.
  

