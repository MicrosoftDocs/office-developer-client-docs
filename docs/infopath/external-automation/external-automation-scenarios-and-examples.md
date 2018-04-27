---
title: "External Automation Scenarios and Examples"
  
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
keywords:
- automating infopath 2007,forms [InfoPath 2007], adding data programmatically,automation [InfoPath 2007], external scenarios
 
localization_priority: Normal
ms.assetid: dfa880e6-de23-41c4-b80b-6935e0c8563d
description: "The members provided by the Microsoft Office InfoPath primary interop assembly (Microsoft.Office.Interop.InfoPath.dll) and the InfoPath XML interop assembly (Microsoft.Office.Interop.InfoPath.Xml.dll) support writing managed code for automating InfoPath."
---

# External Automation Scenarios and Examples

The members provided by the Microsoft Office InfoPath primary interop assembly (Microsoft.Office.Interop.InfoPath.dll) and the InfoPath XML interop assembly (Microsoft.Office.Interop.InfoPath.Xml.dll) support writing managed code for automating InfoPath.
  
## Establishing References to the Microsoft Office InfoPath Primary Interop and InfoPath XML Interop Assemblies

To write managed code for automating InfoPath, you must establish references to the Microsoft InfoPath primary interop and the InfoPath XML interop assemblies. The Microsoft InfoPath primary interop assembly provides support for interoperability with the COM object model exposed by IPEDITOR.DLL by using the members of the [Microsoft.Office.Interop.InfoPath](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.aspx) namespace. The InfoPath XML interop assembly provides support for interoperability with the COM object model exposed by Microsoft XML Core Services (MSXML) by using the members of the [Microsoft.Office.Interop.InfoPath.Xml](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.Xml.aspx) namespace. 
  
> [!IMPORTANT]
> Users of managed-code applications that automate InfoPath must have InfoPath, the Microsoft Office InfoPath primary interop assembly, and the InfoPath XML interop assembly installed on their computers. The **.NET Programmability Support** option in the InfoPath setup program is set to **Run from My Computer** for a typical installation of InfoPath. As a result, as long as the .NET Framework 1.1 Redistributable or .NET Framework 1.1 Software Development Kit (SDK) or later is installed, these interop assemblies will also be installed by default. If these interop assemblies are not available on a user's computer, you must confirm that the .NET Framework 1.1 or later is installed, and then run **Programs and Features** from the **Control Panel** to change setup and set the **.NET Programmability Support** option of InfoPath to **Run from My Computer**. 
  
The following procedures describe how to set references to the Microsoft Office InfoPath primary interop and the InfoPath XML interop assemblies in a Visual Studio project.
  
To set a reference to the Microsoft.Office.Interop.InfoPath primary interop assembly, set a reference to **Microsoft InfoPath 3.0 Type Library** on the **COM** tab of the **Add Reference** dialog box. Even though you set a reference from the **COM** tab, a reference is established to the Microsoft.Office.Interop.InfoPath.dll primary interop assembly that is installed in the Global Assembly Cache (GAC) by the InfoPath setup program. 
  
### Set a reference to the Microsoft.Office.Interop.InfoPath primary interop assembly

1. Open a Visual Studio managed code project.
    
2. In **Solution Explorer**, right-click **References**, and then click **Add Reference**.
    
3. On the **COM** tab, double-click **Microsoft InfoPath 3.0 Type Library**, and then click **OK**.
    
To set a reference to the Microsoft.Office.Interop.InfoPath.Xml interop assembly, browse to the Microsoft.Office.Interop.InfoPath.Xml.dll file that is installed by default in the < _drive_>:\Program Files\Microsoft Office\OFFICE14 folder. Even though you specify the copy of the assembly in the local file system, this procedure establishes a reference to the Microsoft.Office.Interop.InfoPath.Xml.dll assembly that is installed in the Global Assembly Cache (GAC) by the InfoPath setup program.
  
### Set a reference to the Microsoft.Office.Interop.InfoPath.Xml interop assembly

1. Open or create a Visual Studio managed code project, such as a **Console Application** or **Windows Application**.
    
2. In **Solution Explorer**, right-click **References**, and then click **Add Reference**.
    
3. On the **.NET** tab, click **Browse**, navigate to the < _drive_>:\Program Files\Microsoft Office\OFFICE14 folder, and then click Microsoft.Office.Interop.InfoPath.Xml.dll.
    
4. Click **OK**.
    
## Automate Changing the Value of a Field

Suppose one of the customers of the user of an InfoPath sales report form template recently changed its name from "Company A" to "Company B." A developer is asked to write code that will automatically update the sales report forms saved from this form template to reflect the name change. The following scenario assumes a form that contains a text box that is bound to a field named customerName.
  
### Create the sample form template and form

1. Open InfoPath and create a blank form template.
    
2. Add a **Text Box** control to the form, and name the field bound to the control customerName.
    
3. In the **Fields** task pane, right-click the **myFields** folder, and then click **Properties**.
    
4. On the **Details** tab, select and copy the value following **Namespace:**, and then paste this into Notepad or some other location where you can retrieve it. You will need this value later for setting the value of the **SelectionNamespaces** property in your code. 
    
5. Publish the form template to a folder named C:\Test and accept the default name, Template1. 
    
6. Open the form template, add the name "Company A" to text box bound to the customerName field, and then save the form as "Form1". 
    
### Create a managed code console application to change the name from 'Company A' to 'Company B'

1. Open Visual Studio and create a new Visual C# or Visual Basic Console Application named UpdateCustomer.
    
2. Establish references to the Microsoft Office InfoPath primary interop and InfoPath XML interop assemblies as described above.
    
3. Add the following code to the Program.cs or Module1.vb file, making sure to update the value of the namespace in the setting for the **SelectionNamespaces** property with the value you copied when you created the sample form. 
    
  ```cs
  using System;
  using System.Collections.Generic;
  using System.Text;
  using Microsoft.Office.Interop.InfoPath;
  using Microsoft.Office.Interop.InfoPath.Xml;
  namespace UpdateCustomer
  {
     class Program
     {
        static void Main(string[] args)
        {
           // Create an InfoPath Application object.
           Application myApp = 
              new Microsoft.Office.Interop.InfoPath.Application();
           // Get a reference the XDocuments collection 
           // and open the sample form.
           XDocumentsCollection myXDocs = myApp.XDocuments;
           XDocument myXDoc = myXDocs.Open("C:\\Test\\Form1.xml",
              (int) XdDocumentVersionMode.xdFailOnVersionOlder);
           
           // Access the XML DOM for the underlying XML document using
           // the DOM property. Note that you must cast to the 
           // IXMLDOMDocument2 type from the
           // Microsoft.Office.Interop.InfoPath.Xml namespace
           // to access the XML DOM.
           IXMLDOMDocument2 myXMLDoc = myXDoc.DOM as IXMLDOMDocument2;
           // Set the MSXML SelectionNamespaces property to the my
           // namespace of the form. IMPORTANT:Replace the namespace 
           // value below with that of your sample form.
           myXMLDoc.setProperty("SelectionNamespaces",
  "xmlns:my='http://schemas.microsoft.com/office/infopath/2003/myXSD/2006-09-06T23:17:34'");
           // Select all instances of customerName that contain 
           //'Company A'.
           IXMLDOMNodeList myNames = 
              myXMLDoc.selectNodes(
              "//my:customerName[. = 'Company A']");
           // Check to determine if any nodes were returned.
           if (myNames.length < 1)
           Console.WriteLine(
              "No elements containing 'Company A' were found.");
           // Loop through the list updating to 'Company B'.
           IXMLDOMNode myName = myNames.nextNode();
           while (myName != null)
           {
              myName.text = "Company B";
              myName = myNames.nextNode();
           }
           // Save the updated form as Form2.xml and close out.
           myXDoc.SaveAs("C:\\Test\\Form2.xml");
           myXDocs.Close(0);
           myApp.Quit(false);
           Console.WriteLine("Finished!");
        }
     }
  }
  ```

  ```VB.net
  Imports Microsoft.Office.Interop.InfoPath
  Imports Microsoft.Office.Interop.InfoPath.Xml
  Module Module1
     Sub Main()
        ' Create an InfoPath Application object.
        Dim myApp As Application = _
           New Microsoft.Office.Interop.InfoPath.Application()
        ' Get a reference the XDocuments collection 
        ' and open the sample form.
        Dim myXDocs As XDocumentsCollection = myApp.XDocuments
        Dim myXDoc As XDocument = myXDocs.Open( _
           "C:\\Test\\Form1.xml", _
           XdDocumentVersionMode.xdFailOnVersionOlder)
        ' Access the XML DOM for the underlying XML document using
        ' the DOM property. Note that you must cast to the 
        ' IXMLDOMDocument2 type from the
        ' Microsoft.Office.Interop.InfoPath.Xml namespace
        ' to access the XML DOM.
        Dim myXMLDoc As IXMLDOMDocument2 = _
           DirectCast(myXDoc.DOM, IXMLDOMDocument2)
        ' Set the MSXML SelectionNamespaces property to the my
        ' namespace of the form. IMPORTANT:Replace the namespace 
        ' value below with that of your sample form.
        myXMLDoc.setProperty("SelectionNamespaces", _
  "xmlns:my='http://schemas.microsoft.com/office/infopath/2003/myXSD/2006-09-06T23:17:34'")
        ' Select all instances of customerName that contain 
        ''Company A'.
        Dim myNames As IXMLDOMNodeList = _
     myXMLDoc.selectNodes("//my:customerName[. = 'Company A']")
        ' Check to determine if any nodes were returned.
        If (myNames.length < 1) Then
           Console.WriteLine( _
              "No elements containing 'Company A' were found.")
        Else
           ' Loop through the list updating to 'Company B'.
           Dim myName As IXMLDOMNode = myNames.nextNode()
           While (myName IsNot Nothing)
              myName.text = "Company B"
              myName = myNames.nextNode()
           End While
        End If
        ' Save the updated form as Form2.xml and close out.
        myXDoc.SaveAs("C:\\Test\\Form2.xml")
        myXDocs.Close(0)
        myApp.Quit(False)
        Console.WriteLine("Finished!")
     End Sub
  End Module
  
  ```

4. Click **Start Debugging** on the **Debug** menu to compile and run the console application. 
    
    The application opens the form saved as Form1.xml and loops through all customerName elements that contain the value Company A and changes that value to Company B. When the operation is complete, a new copy of the form is saved as Form2.xml in the C:\Test folder. 
    
## Automate Opening a Form and Populating Field Values

The following example automates opening a blank form and populating the first name, last name, and address fields in the form. This scenario assumes a form that contains three text boxes that are bound to fields named FirstName, LastName, and Address.
  
### Create the sample form template and form

1. Open InfoPath and create a blank form.
    
2. Add three text box controls to the form, and name the fields bound to the controls: FirstName, LastName, and Address. Add any other fields you want.
    
3. In the **Fields** task pane, right-click the **myFields** folder, and then click **Properties**.
    
4. On the **Details** tab, select and copy the value following **Namespace:**, and then paste this into Notepad or some other location where you can retrieve it. You will need this value later for setting the value of the **SelectionNamespaces** property in your code. 
    
5. Publish the form template to a folder named C:\Temp and accept the default name, Template1.
    
6. Open the form template and save a blank form as "Form1" to C:\Temp.
    
### Create a managed code console application to open the form and populate the fields

1. Open Visual Studio and create a new Visual C# or Visual Basic Console Application named OpenForm.
    
2. Establish references to the Microsoft Office InfoPath primary interop and InfoPath XML interop assemblies as described above.
    
3. Add the following code to the Program.cs or Module1.vb file, making sure to update the value of the namespace in the setting for the **SelectionNamespaces** property with the value you copied when you created the sample form. 
    
  ```cs
  using System;
  using System.Collections.Generic;
  using System.Text;
  using Microsoft.Office.Interop.InfoPath;
  using Microsoft.Office.Interop.InfoPath.Xml;
  namespace OpenForm
  {
     class Program
     {
        static void Main(string[] args)
        {
           // Create an InfoPath Application object.
           Application myApp=
              new Microsoft.Office.Interop.InfoPath.Application();
           // Create an InfoPath XDocument variable and open 
           // the blank form.
           XDocument myXDoc = myApp.XDocuments.Open(
              "c:\\temp\\Form1.xml",
              (int) XdDocumentVersionMode.xdFailOnVersionOlder);
           
           // Create an IXMLDOMDocument2 variable and access 
           // the XML DOM from the underlying XML document
           // using the DOM property of the XDocument object. 
           // Note that you must cast to IXMLDOMDocument2 to do so.
           IXMLDOMDocument2 doc= myXDoc.DOM as IXMLDOMDocument2;
           // Set the MSXML SelectionNamespaces property to the my
           // namespace of the form. IMPORTANT:Replace the namespace
           // value below with that of your sample form.
           doc.setProperty("SelectionNamespaces","xmlns:my='http://schemas.microsoft.com/office/infopath/2003/myXSD/2006-09-06T23:17:34'");
           // Pre-populate the fields with specified values.
           doc.selectSingleNode("//my:FirstName").text="My Name";
           doc.selectSingleNode("//my:LastName").text="My LastName";
           doc.selectSingleNode("//my:Address").text="My Address";
           // Save the form, leaving InfoPath open.
           myXDoc.Save();
           
        }
     }
  }
  ```

  ```VB.net
  Imports Microsoft.Office.Interop.InfoPath
  Imports Microsoft.Office.Interop.InfoPath.Xml
  Module Module1
     Sub Main()
        ' Create an InfoPath Application object.
        Dim myApp As Application = _
           New Microsoft.Office.Interop.InfoPath.Application
        ' Create an InfoPath XDocument variable and open 
        ' the blank form.
        Dim myXDoc As XDocument = myApp.XDocuments.Open( _
           "c:\\temp\\Form1.xml", _
           XdDocumentVersionMode.xdFailOnVersionOlder)
        ' Create an IXMLDOMDocument2 variable and access 
        ' the XML DOM from the underlying XML document
        ' using the DOM property of the XDocument object.
        Dim doc As IXMLDOMDocument2 = myXDoc.DOM
        ' Set the MSXML SelectionNamespaces property to the my
        ' namespace of the form. IMPORTANT:Replace the namespace
        ' value below with that of your sample form.
        doc.setProperty("SelectionNamespaces", "xmlns:my='http://schemas.microsoft.com/office/infopath/2003/myXSD/2006-09-06T23:17:34'")
        ' Pre-populate the fields with specified values.
        doc.selectSingleNode("//my:FirstName").text = "My Name"
        doc.selectSingleNode("//my:LastName").text = "My LastName"
        doc.selectSingleNode("//my:Address").text = "My Address"
        ' Save the form, leaving InfoPath open.
        myXDoc.Save()
     End Sub
  End Module
  
  ```

4. On the **Debug** menu, click **Start Debugging** to compile and run the console application. 
    
    The application will open the form saved as Form1.xml and fill in the FirstName, LastName, and Address fields with the values specified in the code, and then save the form, leaving InfoPath open. 
    
## See also

#### Concepts

[About the Microsoft Office InfoPath Primary Interop Assembly](about-the-microsoft-office-infopath-primary-interop-assembly.md)
  
[About the InfoPath XML Interop Assembly](about-the-infopath-xml-interop-assembly.md)

