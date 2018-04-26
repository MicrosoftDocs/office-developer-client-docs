---
title: "Address Book Data-Binding Object"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: cf43f645-1ee1-8655-eb70-86d601e9f3f7
description: "The Address Book application uses the RDS.DataControl object to bind data from the SQL Server database to a visual object (in this case, a DHTML table) in the application's client HTML page. The event-driven VBScript program logic uses the RDS.DataControl to:"
---

# Address Book Data-Binding Object

The Address Book application uses the [RDS.DataControl](datacontrol-object-rds.md) object to bind data from the SQL Server database to a visual object (in this case, a DHTML table) in the application's client HTML page. The event-driven VBScript program logic uses the [RDS.DataControl](datacontrol-object-rds.md) to: 
  
- Query the database, send updates to the database, and refresh the data grid.
    
- Allow users to move to the first, next, previous, or last record in the data grid.
    
The following code defines the **RDS.DataControl** component: 
  
```
 
<OBJECT classid="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33" 
   ID=DC1 Width=1 Height=1> 
   <PARAM NAME="SERVER" VALUE="http://<%=Request.ServerVariables("SERVER_NAME")%>"> 
   <PARAM NAME="CONNECT" VALUE="Provider=sqloledb; 
Initial Catalog=AddrBookDb;Integrated Security=SSPI;"> 
</OBJECT> 

```

The OBJECT tag defines the **RDS.DataControl** component in the program. The tag includes two types of parameters: 
  
- Those associated with the generic OBJECT tag.
    
- Those specific to the **RDS.DataControl** object. 
    
## Generic OBJECT Tag Parameters

The following table describes the parameters associated with the OBJECT tag.
  
|**Parameter**|**Description**|
|:-----|:-----|
|***CLASSID* ** <br/> |A unique, 128-bit number that identifies the type of embedded object to the system. This identifier is maintained in the local computer's system registry. (For the class IDs of the **RDS.DataControl** object, see [RDS.DataControl Object](datacontrol-object-rds.md).)  <br/> |
|***ID* ** <br/> |Defines a document-wide identifier for the embedded object that is used to identify it in code.  <br/> |
   
## RDS.DataControl Tag Parameters

The following table describes the parameters specific to the **RDS.DataControl** object. (For a complete list of the **RDS.DataControl** object parameters, and when to implement them, see [RDS.DataControl object](datacontrol-object-rds.md).)
  
|**Parameter**|**Description**|
|:-----|:-----|
|[SERVER](server-property-rds.md) <br/> |If you are using HTTP, the value is the name of the server computer preceded by  `http://` .  <br/> |
|[CONNECT](connect-property-rds.md) <br/> |Provides the necessary connection information for the **RDS.DataControl** to connect to SQL Server.  <br/> |
|[SQL](http://msdn.microsoft.com/library/210adcbb-5c89-150b-4c61-6a52dea9af56%28Office.15%29.aspx) <br/> |Sets or returns the query string used to retrieve the [Recordset](recordset-object-ado.md).  <br/> |
   

