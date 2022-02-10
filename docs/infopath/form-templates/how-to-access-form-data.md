---
title: "Access Form Data"
manager: soliver
ms.date: 12/07/2015
ms.audience: Developer
keywords:
- form data [infopath 2007],forms [InfoPath 2007], accessing properties,form templates [InfoPath 2007], accessing properties,opening forms [InfoPath 2007],printing forms [InfoPath 2007],forms [InfoPath 2007], printing,closing forms [InfoPath 2007],InfoPath 2007, accessing form data,forms [InfoPath 2007], accessing data source,forms [InfoPath 2007], closing,forms [InfoPath 2007], opening,printing [InfoPath 2007], forms,forms [InfoPath 2007], creating
ms.localizationpriority: medium
ms.assetid: fd7374d3-a268-4e30-9872-7579cd681bd0
description: "When you want to extend the functionality of an InfoPath form, it is often necessary to programmatically access information about the form's underlying XML document, access the data that the XML document contains, or perform some action on the XML document. The InfoPath object model supports accessing and manipulating a form's underlying XML document through the use of the XmlForm class in association with the XmlFormCollection class."
---

# Access Form Data

When you want to extend the functionality of an InfoPath form, it is often necessary to programmatically access information about the form's underlying XML document, access the data that the XML document contains, or perform some action on the XML document. The InfoPath object model supports accessing and manipulating a form's underlying XML document through the use of the [XmlForm](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.aspx) class in association with the [XmlFormCollection](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlFormCollection.aspx) class. 
  
The [XmlForm](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.aspx) class is one of the most useful types in the InfoPath object model because it provides a variety of properties and methods that not only interact with a form's underlying XML document, but also perform many of the actions that are available in the InfoPath user interface. 
  
## Overview of the XmlFormCollection Class

The [XmlFormCollection](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlFormCollection.aspx) class provides the following methods and properties that form developers can use to manage the [XmlForm](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.aspx) objects that the collection contains. 
  
|**Name**|**Description**|
|:-----|:-----|
|[New(String)](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlFormCollection.New.aspx) method  <br/> |Creates a new form based on the specified form. |
|[New(String, XmlFormOpenMode)](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlFormCollection.New.aspx) method (overload 1)  <br/> |Creates a new form based on the specified form using the specified open mode behavior. |
|[NewFromFormTemplate(String)](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlFormCollection.NewFromFormTemplate.aspx) method  <br/> |Creates a new form based on the specified form template. |
|[NewFromFormTemplate(String, String)](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlFormCollection.NewFromFormTemplate.aspx) method (overload 1)  <br/> |Creates a new form based on the specified form template and XML data. |
|[NewFromFormTemplate(String, String, XmlFormOpenMode)](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlFormCollection.NewFromFormTemplate.aspx) method (overload 2)  <br/> |Creates a new form based on the specified form template with data specified by an [XPathNavigator](https://msdn.microsoft.com/library/system.xml.xpath.xpathnavigator%28v=vs.110%29.aspx) object. |
|[NewFromFormTemplate(String, XPathNavigator)](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlFormCollection.NewFromFormTemplate.aspx) method (overload 3)  <br/> |Creates a new form based on the specified form template with data specified by an **XPathNavigator** object using the specified open mode behavior. |
|[Open(String)](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlFormCollection.Open.aspx) method  <br/> |Opens the specified form. |
|[Open(String, XmlFormOpenMode)](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlFormCollection.Open.aspx) method (overload 1)  <br/> |Opens the specified form using the specified open mode behavior. |
|[Count](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlFormCollection.Count.aspx) property  <br/> |Gets a count of the number of **XmlForm** objects contained in the collection. |
|[Item](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlFormCollection.Item.aspx) property  <br/> |Gets a reference to the specified **XmlForm** object from the collection by index value. |
   
## Overview of the XmlForm Class

The [XmlForm](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.aspx) class provides the following methods and properties, which form developers can use to interact with and perform actions on a form's underlying XML document. 
  
|**Name**|**Description**|
|:-----|:-----|
|[Close](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.Close.aspx) method  <br/> |Closes the form. |
|[GetWorkflowTasks](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.GetWorkflowTasks.aspx) method  <br/> |Gets a reference to a **Microsoft.Office.Core.WorkflowTasks** collection for the current form. |
|[GetWorkflowTemplates](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.GetWorkflowTemplates.aspx) method  <br/> |Gets a reference to a **Microsoft.Office.Core.WorkflowTemplates** collection for the current form. |
|[MergeForm(String)](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.MergeForm.aspx) method  <br/> |Merges the current form with the form specified by path or URL. |
|[MergeForm(XPathNavigator)](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.MergeForm.aspx) method (overload 1)  <br/> |Merges the current form with the target form specified in the node returned by the **XPathNavigator** passed to the method. |
|[NotifyHost](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.NotifyHost.aspx) method  <br/> |Provides a custom value to the hosting application or ASPX page. |
|[Print()](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.Print.aspx) method  <br/> |Prints the form content as it is rendered in the form's active view. |
|[Print(Boolean)](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.Print.aspx) method (overload 1)  <br/> |Prints the form content as it is rendered in the form's active view by displaying the **Print** dialog box. |
|[Save](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.Save.aspx) method  <br/> |Saves the form to the Uniform Resource Locator (URL) that it is currently associated with. |
|[SaveAs](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.SaveAs.aspx) method  <br/> |Saves the form to the specified Uniform Resource Locator (URL). |
|[SetSaveAsDialogFilename](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.SetSaveAsDialogFilename.aspx) method  <br/> |Sets the default filename for the **SaveAs** dialog box. |
|[SetSaveAsDialogLocation](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.SetSaveAsDialogLocation.aspx) method  <br/> |Sets the default path for saving the form using the **SaveAs** dialog box. |
|[Submit](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.Submit.aspx) method  <br/> |Submits the form using the submit operation defined in the form template. |
|[CurrentView](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.CurrentView.aspx) property  <br/> |Gets a [View](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.View.aspx) object that represents the current view of the form. |
|[DataConnections](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.DataConnections.aspx) property  <br/> |Gets a [DataConnectionCollection](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.DataConnectionCollection.aspx) object associated with the form. |
|[DataSources](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.DataSources.aspx) property  <br/> |Gets the [DataSourceCollection](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.DataSourceCollection.aspx) object associated with the form. |
|[Dirty](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.Dirty.aspx) property  <br/> |Gets a value that indicates whether the data in a form has been modified since it was last saved. |
|[Errors](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.Errors.aspx) property  <br/> |Gets a reference to the [FormErrorCollection](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.FormErrorCollection.aspx) that is associated with a form. |
|[Extension](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.Extension.aspx) property  <br/> |Gets an [System.Object](https://msdn.microsoft.com/library/system.object%28v=vs.110%29.aspx) for accessing the functions and global variables contained in a form's primary form code file using [System.Reflection](https://msdn.microsoft.com/library/system.reflection(v=vs.110).aspx). |
|[FormState](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.FormState.aspx) property  <br/> |Gets a reference to a property bag of type [System.Collections.IDictionary](https://msdn.microsoft.com/library/system.collections.idictionary%28v=vs.110%29.aspx) that browser-enabled forms can use to maintain state information across sessions on the server. |
|[Host](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.Host.aspx) property  <br/> |Gets a [System.Object](https://msdn.microsoft.com/library/system.object%28v=vs.110%29.aspx) that code running in a hosted instance of InfoPath can use to access the object model of the host application. |
|[Hosted](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.Hosted.aspx) property  <br/> |Gets whether InfoPath is hosted as a control in another application. |
|[HostName](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.HostName.aspx) property  <br/> |Gets the name of the application hosting InfoPath as a control. |
|[MainDataSource](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.MainDataSource.aspx) property  <br/> |Gets a [DataSource](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.DataSource.aspx) object that represents the main data source of the form. |
|[NamespaceManager](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.NamespaceManager.aspx) property  <br/> |Gets a reference to a [XmlNamespaceManager](https://msdn.microsoft.com/library/System.Xml.XmlNamespaceManager.aspx) object that can be used to resolve, add, or remove namespaces used in the form. |
|[New](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.New.aspx) property  <br/> |Gets a value that specifies whether a form is new. |
|[Permission](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.Permission.aspx) property  <br/> |Gets a reference to a [Permission](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Permission.aspx) object associated with the form. |
|[QueryDataConnection](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.QueryDataConnection.aspx) property  <br/> |Gets a reference to the [DataConnection](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.DataConnection.aspx) object that represents the data connection that is associated with the form. |
|[ReadOnly](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.ReadOnly.aspx) property  <br/> |Gets a value that indicates whether a form template is read-only or locked. |
|[Recovered](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.Recovered.aspx) property  <br/> |Gets a value that indicates whether a form was last saved by an AutoRecover save operation. |
|[Signed](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.Signed.aspx) property  <br/> |Gets a value that indicates whether a form has been digitally signed using digital signatures. |
|[SignedDataBlocks](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.SignedDataBlocks.aspx) property  <br/> |Gets a reference to the [SignedDataBlockCollection](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.SignedDataBlockCollection.aspx) collection that is associated with a form. |
|[TaskPanes](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.TaskPanes.aspx) property  <br/> |Gets a reference to the [TaskPaneCollection](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.TaskPaneCollection.aspx) that is associated with a form template. |
|[Template](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.Template.aspx) property  <br/> |Gets a reference to the [FormTemplate](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.FormTemplate.aspx) object that represents the manifest (.xsf) of the form template associated with the form. |
|[Uri](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.Uri.aspx) property  <br/> |Gets the Uniform Resource Identifier (URI) of a form. |
|[UserRole](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.UserRole.aspx) property  <br/> |Gets or sets the current user of the form's role name. |
|[ViewInfos](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.ViewInfos.aspx) property  <br/> |Gets a reference to the [ViewInfoCollection](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.ViewInfoCollection.aspx) object associated with the form template. |
|[XmlLang](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.XmlLang.aspx) property  <br/> |Gets the value of the **xml:lang** attribute in the underlying XML document of the form. |
   
## Using the XmlFormCollection Class

The **XmlFormCollection** class is accessed through the [XmlForms](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Application.XmlForms.aspx) property of the [Application](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Application.aspx) class. In a managed code form template created using the object model provided by the members of the [Microsoft.Office.InfoPath](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.aspx) namespace, you can use the **this** (C#) or **Me** (Visual Basic) keyword in your form code to access the **Application** class and its members. 
  
The following example uses the **XmlForms** property of the **Application** class to create an object variable named myForms that references the **XDocumentsCollection** object of the currently running instance of InfoPath. This variable is then used to display the count of forms that are open. 
  
```cs
// Create variable for accessing the XmlFormCollection.
XmlFormCollection myForms = this.Application.XmlForms;
// Display the number of forms that are currently open.
MessageBox.Show("Forms open: " + myForms.Count);
```

```vb
// Create variable for accessing the XmlFormCollection.
Dim myForms As XmlFormCollection = Me.Application.XmlForms
' Display the number of forms that are currently open.
MessageBox.Show("Forms open: " + myForms.Count)
```

The myForms variable can then also be used to create new forms (using one of the **New** or **NewFromTemplate** methods) or open existing forms (using one of the **Open** methods). 
  
## Using the XmlForm Class

In a managed code form template created using the object model provided by the members of the [Microsoft.Office.InfoPath](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.aspx) namespace, you can use the **this** (C#) or **Me** (Visual Basic) keyword in your form code to access the members of the [XmlForm](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.aspx) class directly (without requiring an object variable that establishes a reference to the [XmlForm](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.aspx) class). 
  
### Accessing a Form's Property Values

The following example uses the **this** or **Me** keyword to access the **New**, **ReadOnly**, **Signed**, and **Uri** properties of the **XmlForm** class and display the values returned for the current form in a message box. 
  
```cs
MessageBox.Show(
   "Is new: " + this.New + System.Environment.NewLine +
   "Is read-only: " + this.ReadOnly + System.Environment.NewLine +
   "Is signed: " + this.Signed + System.Environment.NewLine +
   "Form URI: " + this.Uri);
```

```vb
MessageBox.Show( _
   "Is new: " &amp; Me.New &amp; System.Environment.NewLine &amp; _
   "Is read-only: " &amp; Me.ReadOnly &amp; System.Environment.NewLine + _
   "Is signed: " &amp; Me.Signed &amp; System.Environment.NewLine &amp; _
   "Form URI: " &amp; this.Uri)
```

### Accessing a Form's Data Source

A key property of the **XmlForm** class with respect to form data is the **MainDataSource** property. This property returns a reference to a [DataSource](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.DataSource.aspx) object that represents the underlying XML data of the current form, which is also referred to as the form's main or primary data source. The **DataSource** class provides the [CreateNavigator](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.DataSource.CreateNavigator.aspx) method, which creates a [XPathNavigator](https://msdn.microsoft.com/library/system.xml.xpath.xpathnavigator%28v=vs.110%29.aspx) object positioned at the root of the form's underlying XML document. The properties and methods of the **XPathNavigator** class can then be used to navigate and edit the form's underlying XML data. 
  
The following example uses the **MainDataSource** property of the **XmlForm** class to create an **XPathNavigator** object positioned at the root of the form's main data source. The **OuterXml** property of the **XPathNavigator** class is then used to return and display all of the contents of a form's underlying XML document. 
  
```cs
// Get outer XML of the underlying XML document.
string myDoc = this.MainDataSource.CreateNavigator.OuterXml.ToString();
// Display XML.
MessageBox.Show(myDoc);
```

```vb
' Get outer XML of the underlying XML document.
Dim myDoc As String myDoc = _
   Me.MainDataSource.CreateNavigator.OuterXml.ToString()
' Display XML.
MessageBox.Show(myDoc)
```

> [!NOTE]
> Because InfoPath treats the **MainDataSource** property as a default property of the **XmlForm** object accessed when using the **this** or **Me** keywords, you can omit it from the line of code used to create the **XPathNavigator** object. 
  
To learn more about the **XPathNavigator** class in an InfoPath form template's business logic, see [Work with the XPathNavigator and XPathNodeIterator Classes](how-to-work-with-the-xpathnavigator-and-xpathnodeiterator-classes.md).
  
### Accessing Data About a Form's Form Template File

Information about the form template associated with a form, including the form definition file (.xsf ) and the source XML data that it contains, can also be accessed using the **XmlForm** class. This information is accessed using the [Template](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.Template.aspx) property, which returns a reference to a [FormTemplate](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.FormTemplate.aspx) object that represents the form template associated with the current form. 
  
In the following example, the first message box displays some of the data that is available through the **Template** class, such as its Uniform Resource Identifier (URI) location (using the [Uri](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.FormTemplate.Uri.aspx) property), the cache identifier (using the [CacheId](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.FormTemplate.CacheId.aspx) property) and its version number (using the [Version](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.FormTemplate.Version.aspx) property). The next message box uses the [Manifest](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.FormTemplate.Manifest.aspx) property of the **Template** class to create an **XPathNavigator** object that is used to display the source XML of the form definition file (.xsf). 
  
```cs
// Display form template properties.
MessageBox.Show(
   "Cache ID: " + this.Template.CacheId + System.Environment.NewLine +
   "URI: " + this.ReadOnly + System.Environment.NewLine +
   "Version: " + this.Signed, "Form Template Properties");
// Display form definition file XML.
MessageBox.Show(this.Template.Manifest.OuterXml, 
   "Form Definition File XML");
```

```vb
' Display form template properties.
MessageBox.Show( _
   "Cache ID: " &amp; Me.Template.CacheId &amp; System.Environment.NewLine &amp;
   "URI: " &amp; Me.ReadOnly &amp; System.Environment.NewLine &amp;
   "Version: " &amp; Me.Signed, "Form Template Properties")
' Display form definition file XML.
MessageBox.Show(Me.Template.Manifest.OuterXml, _
   "Form Definition File XML")
```


