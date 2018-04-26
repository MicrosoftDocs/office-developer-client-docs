---
title: "DataFactory Customization"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 43cd7416-1f05-87ee-22f0-6cf0d2d1b39f
description: "Remote Data Service (RDS) provides a way to easily perform data access in a three-tier client/server system. A client data control specifies connection and command string parameters to perform a query on a remote data source, or connection string and Recordset object parameters to perform an update."
---

# DataFactory Customization

Remote Data Service (RDS) provides a way to easily perform data access in a three-tier client/server system. A client data control specifies connection and command string parameters to perform a query on a remote data source, or connection string and [Recordset](recordset-object-ado.md) object parameters to perform an update. 
  
The parameters are passed to a server program, which performs the data-access operation on the remote data source. RDS provides a default server program called the [RDSServer.DataFactory](datafactory-object-rdsserver.md) object. The **RDSServer.DataFactory** object returns any **Recordset** object produced by a query to the client. 
  
However, the **RDSServer.DataFactory** is limited to performing queries and updates. It cannot perform any validation or processing on the connection or command strings. 
  
With ADO, you can specify that the **DataFactory** work in conjunction with another type of server program called a  *handler*  . The handler can modify client connection and command strings before they are used to access the data source. In addition, the handler can enforce access rights, which govern the ability of the client to read and write data to the data source. 
  
The parameters the handler uses to modify client parameters and access rights are specified in sections of a customization file.
  
See the following topics for more information about customizing the **DataFactory** object: 
  
- [Understanding the Customization File](understanding-the-customization-file.md)
    
- [Customization File Connect Section](customization-file-connect-section.md)
    
- [Customization File SQL Section](customization-file-sql-section.md)
    
- [Customization File UserList Section](customization-file-userlist-section.md)
    
- [Customization File Logs Section](customization-file-logs-section.md)
    
- [Required Client Settings](http://msdn.microsoft.com/library/edd196b2-cfd7-ff82-b23b-6334910518e4%28Office.15%29.aspx)
    
- [Writing Your Own Customized Handler](http://msdn.microsoft.com/library/67186df9-26b9-428d-2987-cd0bc165f231%28Office.15%29.aspx)
    

