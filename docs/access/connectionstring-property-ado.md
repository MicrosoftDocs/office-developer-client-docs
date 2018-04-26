---
title: "ConnectionString Property (ADO)"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: c67a7daf-258f-d99d-6475-a4aa98d1e99d
---

# ConnectionString Property (ADO)

Indicates the information used to establish a connection to a data source.
  
## Settings and Return Values

Sets or returns a **String** value. 
  
## Remarks

Use the **ConnectionString** property to specify a data source by passing a detailed connection string containing a series of  *argument*  *= value*  statements separated by semicolons. 
  
ADO supports five arguments for the **ConnectionString** property; any other arguments pass directly to the provider without any processing by ADO. The arguments ADO supports are as follows. 
  
|**Argument**|**Description**|
|:-----|:-----|
| *Provider=*  <br/> |Specifies the name of a provider to use for the connection.  <br/> |
| *File Name=*  <br/> |Specifies the name of a provider-specific file (for example, a persisted data source object) containing preset connection information.  <br/> |
| *Remote Provider=*  <br/> |Specifies the name of a provider to use when opening a client-side connection. (Remote Data Service only.)  <br/> |
| *Remote Server=*  <br/> |Specifies the path name of the server to use when opening a client-side connection. (Remote Data Service only.)  <br/> |
| *URL=*  <br/> |Specifies the connection string as an absolute URL identifying a resource, such as a file or directory.  <br/> |
   
After you set the **ConnectionString** property and open the [Connection](connection-object-ado.md) object, the provider may alter the contents of the property, for example, by mapping the ADO-defined argument names to their provider equivalents. 
  
The **ConnectionString** property automatically inherits the value used for the  *ConnectionString*  argument of the [Open](open-method-ado-connection.md) method, so you can override the current **ConnectionString** property during the **Open** method call. 
  
Because the  *File Name*  argument causes ADO to load the associated provider, you cannot pass both the  *Provider*  and  *File Name*  arguments. 
  
The **ConnectionString** property is read/write when the connection is closed and read-only when it is open. 
  
Duplicates of an argument in the **ConnectionString** property are ignored. The last instance of any argument is used. 
  
 **Remote Data Service Usage** When used on a client-side **Connection** object, the **ConnectionString** property can include only the  *Remote Provider*  and  *Remote Server*  parameters. 
  

