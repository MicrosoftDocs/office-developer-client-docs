---
title: "Access External Data Sources Using the InfoPath 2003 Object Model"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
 
keywords:
- data sources [infopath 2007], accessing with infopath 2003 object model,InfoPath 2003-compatible form templates, accessing external data
 
ms.localizationpriority: medium
ms.assetid: 9fd9ca47-abf1-48dd-8668-dfee27161793
description: "When working with an InfoPath form template that uses the InfoPath 2003 compatible object model, you can write code to access the form's secondary data sources and manipulate the data that they contain."
---

# Access External Data Sources Using the InfoPath 2003 Object Model

When working with an InfoPath form template that uses the InfoPath 2003 compatible object model, you can write code to access the form's secondary data sources and manipulate the data that they contain.
  
Each secondary data source is represented by an object instantiated using the [DataSourceObject](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.DataSourceObject.aspx) interface, and corresponds to stored data, obtained from some external source of data, such as a database or a Web Service query. These data sources are referred to as secondary because when the user saves an InfoPath form, the user is saving the data only in the main data source, not the data in the secondary data sources. The connection to a data source is represented by an object instantiated using one of the "data adapter" interfaces, such as the [WebServiceAdapterObject](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.WebServiceAdapterObject.aspx) interface, which represents a data connection to an XML Web Service. 
  
The instantiated [DataSourceObject](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.DataSourceObject.aspx) object represents the storage of XML data returned by a data connection (to a database or Web Service query), and the data adapter represents the data connection itself. 
  
The InfoPath object model supports access to a form's secondary data sources through the use of the [DataSourceObject](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.DataSourceObject.aspx) interface in association with the [DataObjectsCollection](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.DataObjectsCollection.aspx) interface. 
  
The InfoPath object model also provides a set of data adapter objects, containing information about the data connections used by the form. 
  
There are two kinds of data adapters: Query adapters and Submit adapters. Query adapters are used to obtain the data that is then stored in a secondary data source whereas Submit adapters are used to submit data, to a database or Web service, for example. The submitted data is copied from the main or secondary data sources. 
  
## Overview of the DataObjectsCollection Interface

The [DataObjectsCollection](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.DataObjectsCollection.aspx) interface provides the following properties and methods, which form developers can use to manage the [DataSourceObject](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.DataSourceObject.aspx) instances that the form contains. 
  
|**Name**|**Description**|
|:-----|:-----|
|[Count](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.DataObjects.Count.aspx) property  <br/> |Returns a count of the number of **DataSourceObject** instances contained in the collection. |
|[GetEnumerator](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.DataObjects.GetEnumerator.aspx) method  <br/> |Returns an **IEnumerator** that can be used to iterate through the collection. |
|[Item](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.DataObjects.Item.aspx) property  <br/> |Returns a reference to the specified **DataSourceObject** instance. |
   
## Overview of the DataSourceObject Interface

The [DataSourceObject](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.DataSourceObject.aspx) interface provides the following method and properties, which form developers can use to interact with an InfoPath secondary data source. 
  
|**Name**|**Description**|
|:-----|:-----|
|[Query](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.DataObject.Query.aspx) method  <br/> |Executes the query on the data adapter and inserts the returned data as XML into the XML Document Object Model (DOM) associated with the **DataSourceObject**. |
|[DOM](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.DataObject.DOM.aspx) property  <br/> |Returns a reference to the XML DOM used to store and manipulate data using the **DataSourceObject**. |
|[Name](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.DataObject.Name.aspx) property  <br/> |Returns a string value indicating the name of the **DataSourceObject**. |
|[QueryAdapter](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.DataObject.QueryAdapter.aspx) property  <br/> |Returns a reference to the associated data adapter object. |
   
## Overview of the Data Adapter Interfaces

The interfaces for accessing data adapters provide different properties and methods that retrieve and submit data through connections to external data sources; the data adapter that is associated with a [DataSourceObject](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.DataSourceObject.aspx) object is dependent on the type of external data connection. InfoPath implements the following interfaces for accessing data adapters. 
  
|**Name**|**Description**|
|:-----|:-----|
|[ADOAdapterObject](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.ADOAdapterObject.aspx) interface  <br/> |Connects to ADO/OLEDB data sources; limited to Microsoft Access and Microsoft SQL Server™. |
|[SharepointListAdapterObject](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.SharepointListAdapterObject.aspx) interface  <br/> |Connects to a SharePoint list or document library. |
|[WebServiceAdapterObject](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.WebServiceAdapterObject.aspx) interface  <br/> |Connects to XML Web services. |
|[XMLFileAdapterObject](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.XMLFileAdapterObject.aspx) object  <br/> |Connects to an XML file. |
   
## Using the DataSourceObjects and the DataSourceObject Interfaces

The **DataSourceObjects** collection is accessed through the [DataObjects](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._XDocument2.DataObjects.aspx) property of the [XDocument](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.XDocument.aspx) interface. For example, if you create a secondary data source named Employees that retrieves data from the Employees table in the Northwind Traders Microsoft Access database, you can use the **DataSourceObjects** collection to set a reference to a **DataObject** object that represents the retrieved data. 
  
In the following code sample, the name of the secondary data source is passed to the accessor property of the **DataObjectsCollection** interface, which returns a reference to the **DataSourceObject** object. The data from the secondary data source is displayed in a message box by using the **DOM** property of the **DataSourceObject** interface to access the **xml** property of the XML DOM. 
  
```cs
public void CTRL1_5_OnClick(DocActionEvent e)
{
   // Instantiate a variable to access the specified data object
   // from the DataObjectsCollection of the form.
   // You must explicitly cast to the DataSourceObject type 
   // before you can access the data object.
   DataSourceObject myDataObject = 
      thisXDocument.DataObjects["Employees"] as DataSourceObject;
   // Display the data from the secondary data source using the 
   // XML DOM.
   thisXDocument.UI.Alert("Data Adapter: " + myDataObject.DOM.xml);
}
```

```vb
Public Sub CTRL1_5_OnClick(ByVal e As DocActionEvent)
   ' Instantiate a variable to access the specified data object
   ' from the DataObjectsCollection of the form.
   Dim myDataObject As DataSourceObject = _
      thisXDocument.DataObjects("Employees")
   ' Display the data from the secondary data source using the 
   ' XML DOM.
   thisXDocument.UI.Alert("Data Adapter: " + myDataObject.DOM.xml)
End Sub
```

To manipulate the data that is contained in a secondary data source, use the **DOM** property of the **DataSourceObject** interface to return a reference to the XML DOM containing the data. When you have the reference to the XML DOM, you can use any of its properties or methods to manipulate the data that it contains. 
  
## Using the DataAdaptersCollection and the DataAdapterObject Interfaces

The [DataAdaptersCollection](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.DataAdaptersCollection.aspx) interface is accessed through the [DataAdapters](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._XDocument2.DataAdapters.aspx) property of the **XDocument** interface. For example, if you create a secondary data source named Employees that retrieves data from the Employees table in the Northwind Traders Microsoft Access database, you can use the **DataAdapterObjects** collection to set a reference to the **DataAdapterObject** that represents the connection to the database. 
  
In the following code sample, the name of the secondary data source is passed to the accessor property of the **DataAdaptersCollection**, which, in this case, returns a reference to an instance of the **ADOAdapterObject** that represents the connection to the Northwind Microsoft Access database. For this to work properly, you must explicitly cast the object being returned as an **ADOAdapterObject**. The [Connection](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.ADOAdapter2.Connection.aspx) property of the **ADOAdapterObject** interface is used to display the ADO connection string in a message box. 
  
```cs
public void CTRL1_5_OnClick(DocActionEvent e)
{
   // Instantiate a variable to access the specified data object
   // from the DataAdaptersCollection of the form. 
   // You must explicitly cast to the specific adapter type
   // (ADOAdapterObject) before you can access the data adapter.
   ADOAdapterObject myADOAdapter = 
      thisXDocument.DataAdapters["Employees"] as ADOAdapterObject;
   // Display the connection information for the data adapter.
   thisXDocument.UI.Alert("Data Adapter: " + myADOAdapter.Connection);
}
```

```vb
Public Sub CTRL1_5_OnClick(ByVal e As DocActionEvent)
   ' Instantiate a variable to access the specified data object. 
   ' You must explicitly cast to the specific adapter type
   ' (ADOAdapterObject) before you can access the data adapter.
   Dim myADOAdapter As ADOAdapterObject = _
      thisXDocument.DataAdapters("Employees")
   ' Display the connection information for the data adapter.
   thisXDocument.UI.Alert("Data Adapter: " + myADOAdapter.Connection)
End Sub
```


