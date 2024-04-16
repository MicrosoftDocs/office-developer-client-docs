---
title: Address Book Data-Binding object
TOCTitle: Address Book Data-Binding object
ms:assetid: cf43f645-1ee1-8655-eb70-86d601e9f3f7
ms:mtpsurl: https://msdn.microsoft.com/library/JJ250030(v=office.15)
ms:contentKeyID: 48547807
ms.date: 09/18/2015
mtps_version: v=office.15
ms.localizationpriority: medium
---

# Address Book Data-Binding object

**Applies to**: Access 2013, Office 2013

The Address Book application uses the [RDS.DataControl](datacontrol-object-rds.md) object to bind data from the SQL Server database to a visual object (in this case, a DHTML table) in the application's client HTML page. The event-driven VBScript program logic uses the [RDS.DataControl](datacontrol-object-rds.md) to:

  - Query the database, send updates to the database, and refresh the data grid.

  - Allow users to move to the first, next, previous, or last record in the data grid.

The following code defines the **RDS.DataControl** component:

```vb 
 
<OBJECT classid="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33" 
   ID=DC1 Width=1 Height=1> 
   <PARAM NAME="SERVER" VALUE="https://<%=Request.ServerVariables("SERVER_NAME")%>"> 
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
|:------------|:--------------|
|**_CLASSID_**|A unique, 128-bit number that identifies the type of embedded object to the system. This identifier is maintained in the local computer's system registry. (For the class IDs of the **RDS.DataControl** object, see [RDS.DataControl Object](/office/client-developer/access/desktop-database-reference/datacontrol-object-rds). |
|**_ID_**     |Defines a document-wide identifier for the embedded object that is used to identify it in code.  |

## RDS.DataControl Tag Parameters

The following table describes the parameters specific to the **RDS.DataControl** object. (For a complete list of the **RDS.DataControl** object parameters, and when to implement them, see [RDS.DataControl object](datacontrol-object-rds.md).)

|**Parameter**|**Description**|
|:------------|:--------------|
|[SERVER](/office/client-developer/access/desktop-database-reference/server-property-rds)| If you are using HTTP, the value is the name of the server computer preceded by https:// </br>|
|[CONNECT](/office/client-developer/access/desktop-database-reference/connect-property-rds)| Provides the necessary connection information for the <strong>RDS.DataControl</strong> to connect to SQL Server. </br>|
|[SQL](/office/vba/access/concepts/miscellaneous/sql-property-ado)| Sets or returns the query string used to retrieve the [Recordset](/office/client-developer/access/desktop-database-reference/recordset-object-ado)|
