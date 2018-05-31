---
title: "Access External Data Sources"
 
 
manager: soliver
ms.date: 12/07/2015
ms.audience: Developer
 
keywords:
- data connection classes [infopath 2007],secondary data sources [InfoPath 2007],data [InfoPath 2007], secondary,DataSource class [InfoPath 2007],accessing external data sources [InfoPath 2007],DataSourceCollection class [InfoPath 2007],DataConnectionCollection class [InfoPath 2007],DataConnection class [InfoPath 2007],InfoPath 2007, accessing external data,data [InfoPath 2007], external sources
 
localization_priority: Normal
ms.assetid: db7c2521-a1ad-4802-b398-79575d3d310a
description: "When working with an InfoPath form template, you can write code to access the form's secondary data sources and manipulate the data that they contain."
---

# Access External Data Sources

When working with an InfoPath form template, you can write code to access the form's secondary data sources and manipulate the data that they contain. 
  
Each secondary data source is represented by an object instantiated using the [DataSource](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.DataSource.aspx) class, and corresponds to stored data, obtained from some external source of data, such as a database or a Web Service query. These data sources are referred to as secondary because when the user saves an InfoPath form, the user is saving the data only in the main (or primary) data source, not the data in the secondary data sources. The connection to a data source is represented by an object instantiated using one of the "data connection" classes, such as the [WebServiceConnection](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.WebServiceConnection.aspx) class, which represents a data connection to an XML Web Service. 
  
The instantiated [DataSource](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.DataSource.aspx) object represents the storage of XML data returned by a data connection (from a database or Web Service query), and the "data connection" class represents the data connection itself (as defined and named using the **Data Connections** command on the **Data** tab). 
  
The InfoPath object model supports access to a form's secondary data sources through the use of the [DataSource](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.DataSource.aspx) class in association with the [DataSourceCollection](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.DataSourceCollection.aspx) class. 
  
The InfoPath object model also provides a set of data connection classes, containing information about the data connections used by the form.
  
> [!NOTE]
> In Microsoft InfoPath 2003, a data connection is referred to as a data adapter. 
  
Data connections are of two kinds: Query connections are used to obtain the data that is then stored in a secondary data source. Submit connections are used to submit data, to a database or Web service, for example. The submitted data is copied from the main or secondary data sources. 
  
## Overview of the DataSourceCollection Class

The [DataSourceCollection](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.DataSourceCollection.aspx) class provides the following properties and methods, which form developers can use to manage the [DataSourceCollection](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.DataSourceCollection.aspx) object instances that the form contains. 
  
|**Name**|**Description**|
|:-----|:-----|
|[Count](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.DataSourceCollection.Count.aspx) property  <br/> |Returns a count of the number of **DataSource** object instances contained in the collection.  <br/> |
|[GetEnumerator](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.DataSourceCollection.GetEnumerator.aspx) method  <br/> |Returns an **IEnumerator** that can be used to iterate through the collection.  <br/> |
|[Item[Int32]](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.DataSourceCollection.Item.aspx) property  <br/> |Returns a reference to the specified **DataSource** object by index value.  <br/> |
|[Item[String]](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.DataSourceCollection.Item.aspx) property  <br/> |Returns a reference to the specified **DataSource** object by name.  <br/> |
   
## Overview of the DataSource Class

The [DataSourceCollection](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.DataSourceCollection.aspx) class provides the following method and properties, which form developers can use to interact with an InfoPath secondary data source. 
  
|**Name**|**Description**|
|:-----|:-----|
|[CreateNavigator](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.DataSource.CreateNavigator.aspx) method  <br/> |Returns an [XPathNavigator](https://msdn.microsoft.com/library/system.xml.xpath.xpathnavigator%28v=vs.110%29.aspx) object for accessing and editing the data source  <br/> |
|[QueryConnection](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.DataSource.QueryConnection.aspx) property  <br/> |Gets a reference to the associated data connection object.  <br/> To execute the query on the data connection and insert the returned data as XML into the XML node associated with the **DataSource** object, use the [Execute](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.DataConnection.Execute.aspx) method of the associated data connection object.  <br/> |
|[Name](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.DataSource.Name.aspx) property  <br/> |Gets the name of the **DataSource** object.  <br/> |
|[ReadOnly](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.DataSource.ReadOnly.aspx) property  <br/> |Gets a value that indicates whether the data source is in a read-only state  <br/> |
|[GetNamedNodeProperty](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.DataSource.GetNamedNodeProperty.aspx) method  <br/> |Gets the value of a named property for the specified XML node, which must be a **nonattribute** node in the main data source.  <br/> |
|[SetNamedNodeProperty](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.DataSource.SetNamedNodeProperty.aspx) method  <br/> |Sets the value of a named property for the specified XML node, which must be a **nonattribute** node in the main data source.  <br/> |
   
## Overview of the Data Connection Classes

The classes for accessing data connections provide different properties and methods that retrieve and submit data through connections to external data sources; the data connection that is associated with a **DataSource** object is dependent on the type of external data connection. InfoPath implements the following classes for accessing data connections. 
  
|**Name**|**Description**|
|:-----|:-----|
|[AdoQueryConnection](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.AdoQueryConnection.aspx) class  <br/> |Queries an ADO/OLEDB data source; limited to Microsoft Access and Microsoft SQL Server.  <br/> |
|[AdoSubmitConnection](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.AdoSubmitConnection.aspx) class  <br/> |Submits to an ADO/OLEDB data source; limited to Microsoft Access and Microsoft SQL Server.  <br/> |
|[SharePointListRWQueryConnection](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.SharePointListRWQueryConnection.aspx) class  <br/> |Queries a SharePoint list or document library.  <br/> |
|[SharePointListRWSubmitConnection](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.SharePointListRWSubmitConnection.aspx) <br/> |Submits to a SharePoint list or document library.  <br/> |
|[WebServiceConnection](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.WebServiceConnection.aspx) class  <br/> |Connects to an XML Web service.  <br/> |
|[FileQueryConnection](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.FileQueryConnection.aspx) class  <br/> |Queries an XML file.  <br/> |
|[FileSubmitConnection](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.FileSubmitConnection.aspx) class  <br/> |Submits to an XML file.  <br/> |
|[EmailSubmitConnection](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.EmailSubmitConnection.aspx) class  <br/> |Submits a form as an attachment in email.  <br/> |
|[BdcQueryConnection](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.BdcQueryConnection.aspx) class  <br/> |Queries an external list on a server running SharePoint Foundation 2010 or SharePoint Server 2010.  <br/> |
|[BdcSubmitConnection](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.BdcSubmitConnection.aspx) class  <br/> |Submits to an external list on a server running SharePoint Foundation 2010 or SharePoint Server 2010.  <br/> |
   
## Using the DataSourceCollection and the DataSource Classes

The **DataSourceCollection** object that represents the collection of data sources associated with a form template is accessed through the [DataSources](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.DataSources.aspx) property of the [XmlForm](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.aspx) class. For example, if you create a secondary data source named Employees that retrieves data from the Employees table in the Northwind database, you can use the **DataSourceCollection** object to set a reference to a **DataSource** object that represents the retrieved data. 
  
In the following code sample, the name of the secondary data source is passed to the accessor property of the **DataSourceCollection** class, which returns a reference to the **DataSource** object that represents the retrieved Employees table data. The XML node that stores the retrieved data from the secondary data source is displayed in a message box using the **CreateNavigator** method of the **DataSource** class to access the **InnerXml** property of the **XPathNavigator** class. 
  
```cs
// Instantiate a variable to access the specified data source
// from the DataSourceCollection of the form.
DataSource myDataSource = 
   this.DataSources["Employees"];
// Display the XML data from the secondary data source.
MessageBox.Show("Data source data: " +
   myDataSource.CreateNavigator().InnerXml.ToString());
```

```vb
' Instantiate a variable to access the specified data source
' from the DataSourceCollection of the form.
Dim myDataSource As DataSource = _
   Me.DataSources("Employees")
' Display the XML data from the secondary data source.
MessageBox.Show("Data source data: " &amp; _
   myDataSource.CreateNavigator().InnerXml.ToString())
```

To manipulate the data that is contained in a secondary data source, use the **CreateNavigator** method of the **DataSource** class to return a reference to an **XPathNavigator** object positioned at the node where the secondary data is stored. You can use the properties or methods of the **XPathNavigator** class to manipulate the data. For more information, see [Work with the XPathNavigator and XPathNodeIterator Classes](how-to-work-with-the-xpathnavigator-and-xpathnodeiterator-classes.md).
  
## Using the DataConnectionCollection and the DataConnection Classes

The [DataConnectionCollection](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.DataConnectionCollection.aspx) object that represents the collection of data connections associated with a form template is accessed through the [DataConnections](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.DataConnections.aspx) property of the **XmlForm** class. For example, if you create a secondary data source named Employees that retrieves data from the Employees table in the Northwind database, you can use the **DataConnectionCollection** object associated with the form template to set a reference to the **DataConnection** that represents the connection to the database. 
  
In the following code sample, the name of the secondary data source is passed to the accessor property of the **DataConnectionCollection** class, which, in this case, returns a reference to the **ADOQueryConnection** object that represents the connection to the Northwind database. For this to work properly, you must explicitly cast the object being returned to the **ADOQueryConnection** type. The [Connection](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.AdoQueryConnection.Connection.aspx) property of the **ADOAdapterObject** interface is used to display the ADO connection string in a message box. 
  
```cs
// Instantiate a variable to access the specified data connection
// from the DataConnectionCollection of the form. 
// You must cast to the specific data connection type
// (ADOQueryConnection) before you can access the data connection.
ADOQueryConnection myADOConnection = 
   (ADOQueryConnection)this.DataConnections["Employees"];
// Display the connection information for the data connection.
MessageBox.Show("Connection string: " + myADOConnection.Connection);
```

```vb
' Instantiate a variable to access the specified data connection
' from the DataConnectionCollection of the form. 
' You must cast to the specific data connection type
' (ADOQueryConnection) before you can access the data connection.
Dim myADOConnection As ADOQueryConnection = _
   DirectCast(Me.DataConnections("Employees"), ADOQueryConnection)
' Display the connection information for the data connection.
MessageBox.Show("Connection string: " &amp; myADOConnection.Connection)
```

## See also



[Creating InfoPath Form Templates That Work With InfoPath Forms Services](creating-infopath-form-templates-that-work-with-infopath-forms-services.md)

