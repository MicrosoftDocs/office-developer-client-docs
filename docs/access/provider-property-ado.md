---
title: "Provider Property (ADO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 1b795f51-93d7-431c-b1fe-0db95f69a56a

---

# Provider Property (ADO)

Indicates the name of the provider for a [Connection](connection-object-ado.md) object. 
  
## Settings and Return Values

Sets or returns a **String** value that indicates the provider name. 
  
## Remarks

Use the **Provider** property to set or return the name of the provider for a connection. This property can also be set by the contents of the [ConnectionString](connectionstring-property-ado.md) property or the  *ConnectionString*  argument of the [Open](open-method-ado-connection.md) method; however, specifying a provider in more than one place while calling the **Open** method can have unpredictable results. If no provider is specified, the property will default to MSDASQL ( [Microsoft OLE DB Provider for ODBC](microsoft-ole-db-provider-for-odbc.md)).
  
The **Provider** property is read/write when the connection is closed and read-only when it is open. The setting does not take effect until you either open the **Connection** object or access the [Properties](properties-collection-ado.md) collection of the **Connection** object. If the setting is not valid, an error occurs. 
  

