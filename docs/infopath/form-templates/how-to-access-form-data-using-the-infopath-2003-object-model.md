---
title: "Access Form Data Using the InfoPath 2003 Object Model"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
 
keywords:
- xdocument interface [infopath 2007],InfoPath 2003-compatible form templates, accessing form data,XDocumentsCollection interface [InfoPath 2007]
 
localization_priority: Normal
ms.assetid: e0731014-f454-4417-9f90-19f3387f5776
description: "When you want to extend the functionality of an InfoPath form, it is often necessary to programmatically access information about the form's underlying XML document, access the data that the XML document contains, or perform some action on the XML document. The InfoPath object model supports accessing and manipulating a form's underlying XML document through the use of the XDocument interface in association with the XDocumentsCollection interface."
---

# Access Form Data Using the InfoPath 2003 Object Model

When you want to extend the functionality of an InfoPath form, it is often necessary to programmatically access information about the form's underlying XML document, access the data that the XML document contains, or perform some action on the XML document. The InfoPath object model supports accessing and manipulating a form's underlying XML document through the use of the [XDocument](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.XDocument.aspx) interface in association with the [XDocumentsCollection](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.XDocumentsCollection.aspx) interface. 
  
The **XDocument** interface is one of the most useful types within the InfoPath object model because it provides a variety of properties, methods, and events that not only interact with a form's underlying XML document, but also perform many of the actions that are available in the InfoPath user interface. In a managed-code project created using the InfoPath 2003-compatible object model, a variable of type **XDocument** that is named  `thisXDocument` is automatically defined in the  `_StartUp` method of the class that contains event handlers in your project's form code. You can use the  `thisXDocument` variable in your form's code to access the **XDocument** interface and its members. 
  
## Overview of the XDocumentsCollection Interface

The **XDocumentsCollection** interface provides the following methods and properties that form developers can use to manage the **XDocument** objects that the collection contains. 
  
|**Name**|**Description**|
|:-----|:-----|
|[Close](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.XDocuments2.Close.aspx) method  <br/> |Closes the specified form.  <br/> |
|[New](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.XDocuments2.New.aspx) method  <br/> |Creates a new form based on an existing form.  <br/> |
|[NewFromSolution](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.XDocuments2.NewFromSolution.aspx) method  <br/> |Creates a new form based on an existing form template.  <br/> |
|[NewFromSolutionWithData](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.XDocuments2.NewFromSolutionWithData.aspx) method  <br/> |Creates a new InfoPath form using the specified XML data and form template.  <br/> |
|[Open](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.XDocuments2.Open.aspx) method  <br/> |Opens the specified form.  <br/> |
|[Count](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.XDocuments2.Count.aspx) property  <br/> |Returns a count of the number of **XDocument** objects contained in the collection.  <br/> |
|[Item](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.XDocuments2.Item.aspx) property  <br/> |Returns a reference to the specified **XDocument** object.  <br/> |
   
## Overview of the XDocument Interface

The **XDocument** interface provides the following methods and properties, which form developers can use to interact with and perform actions on a form's underlying XML document. 
  
|**Name**|**Description**|
|:-----|:-----|
|[GetDataVariable](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._XDocument2.GetDataVariable.aspx) method  <br/> |Returns the string value of a specified data variable.  <br/> |
|[GetDOM](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._XDocument2.GetDOM.aspx) method  <br/> |Returns a reference to the XML Document Object Model (DOM) associated with the specified **DataObject** object.  <br/> |
|[ImportFile](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._XDocument2.ImportFile.aspx) method  <br/> |Imports (or merges) the specified form with the currently open form.  <br/> |
|[PrintOut](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._XDocument2.PrintOut.aspx) method  <br/> |Prints the current view of a form.  <br/> |
|[Query](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._XDocument2.Query.aspx) method  <br/> |Retrieves data from a form's associated data adapter.  <br/> |
|[Save](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._XDocument2.Save.aspx) method  <br/> |Saves the currently open form.  <br/> |
|[SaveAs](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._XDocument2.SaveAs.aspx) method  <br/> |Saves the currently open form with the specified name.  <br/> |
|[SetDataVariable](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._XDocument2.SetDataVariable.aspx) method  <br/> |Sets the value of a specified data variable.  <br/> |
|[Submit](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._XDocument2.Submit.aspx) method  <br/> |Submits a form according to the submit operation established in design mode.  <br/> |
|[DataObjects](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._XDocument2.DataObjects.aspx) property  <br/> |Returns a reference to the **DataObjects** collection.  <br/> |
|[DOM](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._XDocument2.DOM.aspx) property  <br/> |Returns a reference to the XML DOM that is populated with the source XML data of a form.  <br/> |
|[Errors](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._XDocument2.Errors.aspx) property  <br/> |Returns a reference to the **Errors** collection.  <br/> |
|[Extension](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._XDocument2.Extension.aspx) property  <br/> |Returns a reference to an object representing all of the functions and variables contained in a form code file.  <br/> |
|[IsDirty](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._XDocument2.IsDirty.aspx) property  <br/> |Returns a **Boolean** value indicating whether the data in the form has been changed.  <br/> |
|[IsDOMReadOnly](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._XDocument2.IsDOMReadOnly.aspx) property  <br/> |Returns a **Boolean** value indicating whether the XML DOM is set as read-only.  <br/> |
|[IsNew](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._XDocument2.IsNew.aspx) property  <br/> |Returns a **Boolean** value indicating whether the form was saved after it was created.  <br/> |
|[IsReadOnly](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._XDocument2.IsReadOnly.aspx) property  <br/> |Returns a **Boolean** value indicating whether the form is in read-only mode.  <br/> |
|[IsSigned](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._XDocument2.IsSigned.aspx) property  <br/> |Returns a **Boolean** value indicating whether the form is digitally signed.  <br/> |
|[Language](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._XDocument2.Language.aspx) property  <br/> |Specifies or returns the string value of the language used for the form.  <br/> |
|[QueryAdapter](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._XDocument2.QueryAdapter.aspx) property  <br/> |Returns a reference to the data adapter object.  <br/> |
|[Solution](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._XDocument2.Solution.aspx) property  <br/> |Returns a reference to the **Solution** object.  <br/> |
|[UI](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._XDocument2.UI.aspx) property  <br/> |Returns a reference to the **UI** object.  <br/> |
|[URI](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._XDocument2.URI.aspx) property  <br/> |Returns a string value containing the Uniform Resource Identifier (URI) of the form.  <br/> |
|[View](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._XDocument2.View.aspx) property  <br/> |Returns a reference to the **View** object.  <br/> |
|[ViewInfos](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._XDocument2.ViewInfos.aspx) property  <br/> |Returns a reference to the **ViewInfos** collection.  <br/> |
   
## Using the XDocuments Collection and the XDocument Interfaces

The **XDocumentsCollection** interface is accessed through the [XDocuments](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._Application2.XDocuments.aspx) property of the [Application](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.Application.aspx) interface. In a managed-code project created using the InfoPath 2003-compatible object model, you can access the **XDocumentsCollection** interface by using the  `thisApplication` variable that is instantiated in the  `_StartUp` method of your project's form code. The following lines of code create a variable that references the **XDocumentsCollection** interface of the current project. 
  
```cs
XDocumentsCollection xdocs;
xdocs = thisApplication.XDocuments;
// Write code here to work with the XDocumentsCollection.
```

```vb
Dim xdocs As XDocumentsCollection
xdocs = thisApplication.XDocuments
' Write code here to work with the XDocumentsCollection.
```

In a managed-code project created using the InfoPath 2003-compatible object model, you can access the **XDocument** interface by using the  `thisXDocument` variable that is instantiated in the  `StartUp` method of your project's form code. The following line of code uses the  `thisXDocument` variable to access the **XDocument** interface of the current project to display the URI of the currently open form in an alert message. 
  
```cs
thisXDocument.UI.Alert(thisXDocument.URI);
```

```vb
thisXDocument.UI.Alert(thisXDocument.URI)
```

> [!NOTE]
> When you use the **XDocument** interface to access a form's underlying XML document, you are accessing the XML document that is associated with the currently open form. 
  
A key property of the **XDocument** interface is the **DOM** property. This property returns a reference to the XML DOM that is populated with the source XML data of a form. When using the **DOM** property, you can use any of the properties and methods that are supported by the XML DOM. For example, the following code uses the **xml** property of the XML DOM to return and display all of the contents of a form's underlying XML document. 
  
```cs
string xmldoc;
xmldoc = thisXDocument.DOM.xml;
// Display xml.
thisXDocument.UI.Alert(xmldoc);
```

```vb
Dim xmldoc As String
xmldoc = thisXDocument.DOM.xml
' Display xml.
thisXDocument.UI.Alert(xmldoc)
```

> [!NOTE]
> To learn more about the XML DOM and all of the properties and methods that it supports, see the MSXML SDK on MSDN. 
  

