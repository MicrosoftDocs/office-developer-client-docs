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

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Parameter</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong><em>CLASSID</em></strong></p></td>
<td><p>A unique, 128-bit number that identifies the type of embedded object to the system. This identifier is maintained in the local computer's system registry. (For the class IDs of the <strong>RDS.DataControl</strong> object, see <a href="datacontrol-object-rds.md">RDS.DataControl Object</a>.)</p></td>
</tr>
<tr class="even">
<td><p><strong><em>ID</em></strong></p></td>
<td><p>Defines a document-wide identifier for the embedded object that is used to identify it in code.</p></td>
</tr>
</tbody>
</table>


## RDS.DataControl Tag Parameters

The following table describes the parameters specific to the **RDS.DataControl** object. (For a complete list of the **RDS.DataControl** object parameters, and when to implement them, see [RDS.DataControl object](datacontrol-object-rds.md).)

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Parameter</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="server-property-rds.md">SERVER</a></p></td>
<td><p>If you are using HTTP, the value is the name of the server computer preceded by https:// .</p></td>
</tr>
<tr class="even">
<td><p><a href="connect-property-rds.md">CONNECT</a></p></td>
<td><p>Provides the necessary connection information for the <strong>RDS.DataControl</strong> to connect to SQL Server.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://docs.microsoft.com/office/vba/access/concepts/miscellaneous/sql-property-ado">SQL</a></p></td>
<td><p>Sets or returns the query string used to retrieve the <a href="recordset-object-ado.md">Recordset</a>.</p></td>
</tr>
</tbody>
</table>

