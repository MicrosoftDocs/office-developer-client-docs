---
title: "About InfoPath Support for XML Technologies"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 074181a2-3a75-824c-049d-549aabff0f9f
description: "Microsoft InfoPath is a hybrid tool that combines the best of a traditional document editing experience, such as a word processor or e-mail application, with the rigorous data-capture capabilities of a forms package. This article describes the problems InfoPath is designed to address and explains the design principles and XML industry standards used to solve these problems."
---

# About InfoPath Support for XML Technologies

Microsoft InfoPath is a hybrid tool that combines the best of a traditional document editing experience, such as a word processor or e-mail application, with the rigorous data-capture capabilities of a forms package. This article describes the problems InfoPath is designed to address and explains the design principles and XML industry standards used to solve these problems.
  
## Introduction

InfoPath is a high-level XML authoring tool that enables ordinary end-users to create XML documents that belong to a custom-defined XML schema. When the user edits an XML document, modifications to the document are controlled by the XML schema.
  
The user interacts with the XML document through a rich, formatted view that is displayed by applying an XSLT style sheet to the document. A leaf node or attribute value from the XML document is displayed as a field, such as a text box or check box, whereas a hierarchy of nodes is rendered as a group of fields.
  
InfoPath enables validated, structured editing of XML data by showing the editing actions that are valid for the field or field group that is currently selected. This structured editing enables the user to add and remove valid XML elements and attributes by working with groups of fields displayed in rich dynamic views, without seeing the elements and attributes.
  
InfoPath solves a problem in the area of data gathering that could not be solved before the advent of XML: by providing forms that can grow by adding groups of fields that use the hierarchical data model of XML, InfoPath adds the flexibility of word processor documents to the rigorous validation features of a forms application. Complex XSLT transformations are an integral part of this solution that provides dynamic, easy-to-use views of the XML data.
  
## Limitations of Traditional Forms and Documents for Gathering Data

When gathering corporate data, users often want more flexibility than static forms provide, but more structured editing and validation than word processor documents provide.
  
Traditional forms are static and limited in length. They have a fixed number of repeating rows, and cannot be extended when the form is being filled out. Traditional forms are difficult to use because they do not have rich editing features. Often, the user must provide all the information in one pass.
  
On the other hand, traditional documents created by using a word processor enable the user to freely add and remove content, but provide little guidance about how to enter complete, structured, and valid information; any fields that are defined in the document have minimal or no validation of data values and data types. Data in the fields is not properly labeled to enable easy referencing and automatic reuse. The data is free-form rather than structured; you cannot group information, such as applying an "Address" label to a group of "Street", "City", and "State" fields.
  
Thus there is a need for such flexible yet structured editing, but because this kind of technology was not available before the advent of XML, developers have had to create custom applications, which require extensive coding. Custom applications are expensive and difficult to modify, and require custom coding for validation. Custom applications often require end-user training, and it is difficult to reuse the resulting data for other business processes.
  
## Providing Structured Editing by Displaying XML Data as Field Groups

An important technical design problem that had to be solved was how to provide an easy user interface for adding and removing XML elements and attributes, without showing the elements and attributes, but keeping the DOM tree valid according to the custom-defined XML schema. The user interface needed to provide a natural way to edit the DOM tree that includes inserting optional subtrees, replacing choices of subtrees, and extending existing subtrees.
  
To provide this easy user interface, a DOM subtree is displayed as a field group, or section. A field group is a group of UI controls, such as text boxes and drop-down lists, and serves as an easy user interface that enables the user to visualize and edit hierarchical XML data. A field group can contain other field groups and can be optional or repeating, just as a DOM subtree can contain other subtrees and can be optional or repeating. A subtree is added to the DOM tree when the user rests the mouse pointer over a field group, clicks the drop-down menu that appears on the field group, and then selects **Insert \<field group name\>**.
  
InfoPath provides this structured editing of XML data by using the specified XML schema to constrain and guide editing. The schema controls whether the **Insert** and **Remove** commands appear on the drop-down menu for a field group. The schema is also used for validation. To enable editing of an XML document for which there is no XML schema, InfoPath can generate a schema from the XML document. 
  
## Providing Easy-to-Use Views of XML Data by Using XSLT Transformations

Another technical design challenge that needed to be solved was how to enable the content of the UI views to be organized very differently than the structure of the XML data. To present the data in a way that makes the most sense for the user and enables the user to easily read and edit the data, the designer must be able to display data in a different sequence than in the DOM data tree, omit some data from a view, reorganize adjacent data tree nodes into separate views, and collect data from different parts of the data tree into a single view.
  
The order and structure of the content of the views must therefore be independent of the order and structure of the DOM tree nodes. This structural independence of presentation and data requires a complex, dynamic binding or mapping between the grouped fields in the views and the nodes in the DOM tree.
  
To provide this complex mapping between views and data, InfoPath uses XSL Transformations (XSLT) extensively. XSLT is a powerful style sheet language that supports complex XSLT transformations and supports rich views with dynamic, flexible presentation of content. One XSLT file is used for each view. By using a style sheet is a common, well-established design approach in SGML and XML authoring tools, and XSLT is the W3C standard for stylesheets that are used for this kind of complex transformation.
  
To avoid running the whole XSLT transformation every time that the user modifies the structure of a subtree in the DOM, algorithms are used to determine which part of the view must be refreshed. Then only the relevant part of the XSLT style sheet is applied, and the affected part of the view is refreshed.
  
## How XML Standards Are Used When Editing a Form

InfoPath is built from the ground up on XML standards that includes the following:
  
- Extensible Markup Language (XML) 1.0 Second Edition
    
- Namespaces in XML
    
- XML Path Language (XPath) 1.0
    
- XML Schema (XSD) 1.0 Part 1: Structures, and Part 2: Datatypes
    
- Extensible Stylesheet Language Transformations (XSLT) 1.0
    
- Extensible Hypertext Markup Language (XHTML) 1.0
    
- Cascading Style Sheets (CSS)
    
- Document Object Model (DOM) 1.0
    
- XML Digital Signatures (XML DSig)
    
- Simple Object Access Protocol (SOAP) 1.1
    
- Web Services Description Language (WSDL) 1.1
    
- Universal Description, Discovery, and Integration (UDDI) 1.0
    
For example, InfoPath uses and generates standard XML, XSLT, and XSD files that can be reused in various business processes. InfoPath uses MSXML, the SOAP Toolkit, and the .NET System.XML namespace to support these standards, and provides full integrated support for XML Web services.
  
Figure 1 shows the context-sensitive drop-down menu for a **customer** field group, which enables the user to add another **customer** field group, remove this **customer** field group, insert an **item** row in the table of purchase items in this field group, or insert an optional **actions** field group within this field group. The **Click here** link provides another way to insert the **actions** field group. A shorter drop-down menu appears on each purchase-item row. 
  
1. In InfoPath, the user creates a new XML document based on an InfoPath form template, or opens an existing XML document that is based on a form template. The XML document is an XML data file that contains a reference to the form template and can use XML namespaces. 
    
    A form template is the set of files that provide structured editing of XML documents that comply with a particular custom-defined XML schema. The files that make up the form template may be packaged as individual files inside a ordinary folder or as files residing in a cabinet folder. In either case, the files are standard XML files and optional supporting files such as managed code assemblies.
    
2. If the XML document is digitally signed using XML Signature, InfoPath confirms that the XML file is consistent before it opens it.
    
3. InfoPath creates a DOM data tree of the XML document in-memory.
    
4. XSLT transformations are applied to the DOM tree, producing views that show an appropriate presentation of the document to the user. Elements at the beginning of the XML document could be displayed at the bottom of the view and also in a different arrangement in another view. The views consist of UI containers such as sections that contain text and controls, such as text boxes, rich text boxes, date pickers, and drop-down lists. Containers can also contain other containers.
    
5. The XSLT transformation produces XHTML as output, and then a CSS is used to control the presentation of the XHTML.
    
6. If the XML schema allows adding nodes to a node of the data tree, the field or field group that is mapped to the node has a drop-down menu that enables the user to add or remove field groups. The user edits the document by adding a repeating or optional field group, entering a value, selecting an option, or entering rich text. If an XML schema node is associated with the schema for XHTML, InfoPath presents a UI for creating rich text. When the user enters rich text, XHTML content is created as a subtree in the DOM.
    
7. The DOM tree is always kept valid. As the user edits the XML document, the edits are validated against the associated XML schema. The attempted changes to the DOM structure and leaf node values are validated against the XML schema to ensure that their data types and values are valid. If the attempted changes are invalid, a validation dialog box opens, and the changes are not applied to the DOM tree. If the changes are valid, the DOM tree is updated.
    
8. The changed part of the view is refreshed, by applying only the required parts of the XSLT style sheet to the DOM tree.
    
9. The user can save the XML document or submit the XML document by using plain HTTP or SOAP. The user is not allowed to submit the document unless it is valid according to the XML schema.
    
## How XML Standards Are Used When Designing a Form

You can design a form by starting with an existing XML schema, by connecting to an XML Web service or database and obtaining its XML schema, or by automatically generating a schema from a new form or from an XML data file. These scenarios are described in the following procedures. Figure 3 shows the basic user interface for designing a form template.
  
1. Create a new form in the InfoPath Designer by selecting the **XML or Schema** form template, and then select an existing XML schema file as the data source. The XML schema is loaded into the task pane and shown as a tree control. 
    
2. Use the design layout tools to lay out the UI controls, such as rows and the background design, in one or more views. This generates some of the XSLT elements. The XSLT views and the XML schema are automatically associated with the form template.
    
3. Map the XML schema elements to the UI controls in the views by using drag-and-drop. InfoPath helps you choose appropriate controls for the XML schema elements, based on the kind of the schema elements. For example, if the XML data type is date, InfoPath suggests a date picker control. Based on choices in the XML schema, InfoPath can insert groups of optional or repeating fields. Mapping the XML schema elements to the UI controls generates the XSLT structure.
    
4. Save the form template. You can save the files that make up the form template as individual files in a regular folder or as files inside a cabinet folder. In either case, the files are standard XML files. The form template is now ready for the user to use.
    
A form template contains all the semantic information that is needed to provide structured editing when a form is opened in InfoPath. A form template includes a manifest file, the XSLT files that define the views, the information that is needed to validate data, and an optional resource identifier for an XML Web service.
  
The manifest, or form definition file , is the common hub and entry point for all of the files that are required by the form template. The manifest contains references to the other files in the form template, and contains the information that is needed to validate data and provide structured editing. The XML schema validation information is customized for the resulting user interface and added to the manifest file. For example, if the schema allows inserting multiple optional elements in a specific subtree, you can design the UI so that multiple optional elements are added when the user performs a single UI operation. This customization is important for providing a great user experience for the ordinary user. 
  
You can also design a form by using an existing XML Web service to provide the XML schema. To do this:
  
1. Use UDDI to locate relevant Web services.
    
2. Select the Web service to use. InfoPath reads the WSDL file associated with the Web service and identifies the XML schema to be used.
    
3. Open the XML schema to load it.
    
4. Lay out the UI controls and associate them with XML schema elements and attributes.
    
5. Define how to submit the XML document to the Web service that uses SOAP.
    
If you want to design a form from scratch and automatically generate the XML schema:
  
1. On the **File** tab, select either the **Blank Form** or **Blank Form (InfoPath Filler)** form template, and then click **Design Form**.
    
2. On the **Home** tab, click the arrow in the lower-right corner of the **Controls** group to display the **Controls** task pane, and then make sure that the **Automatically create the data source** check box is selected. (By default, this check box is selected.) 
    
3. Lay out the UI controls. As you lay them out, InfoPath automatically creates the XML schema and maps its elements and attributes to the UI controls.
    
To design a form by starting with any well-formed XML data file:
  
1. On the **File** tab, select the **XML or Schema** form template, and then click **Design Form**.
    
2. In the **Data Source Wizard**, select the XML file that you want to use as the data source. An XML schema is automatically created, based on the XML data file.
    
3. Lay out the UI controls as described earlier in this section.
    
## Designed as an Ideal Client for Web Services

Broad industry-wide support for Web services is becoming available. Many back-end and middle-tier systems can be configured to communicate by using Web services standards such as SOAP, UDDI, and WSDL. These Web services-enabled systems include databases, workflow systems, enterprise resource planning (ERP), customer relationship management (CRM), and other systems. Now, InfoPath provides an ideal UI to view and edit the XML data that is being sent through Web services. Figure 4 shows the integrated support for XML Web services.
  
InfoPath fits well with the loosely coupled model of Web services, in which data is sent between computers as complete XML documents. This coarse-grained communication model fits well with the asynchronous nature of the Web. As a high-level authoring tool for XML documents, InfoPath supports the document/literal SOAP encoding instead of Remote Procedure Call (RPC) SOAP encoding. InfoPath is an ideal client for Web services, because it can natively read the XML schema specified in a SOAP message and then create a UI based on the schema, which enables users to easily view and edit XML documents that are generated or received by the corresponding Web service. InfoPath also provides support for ADO.NET DataSets that includes change-tracking.
  
## Terminology

|||
|:-----|:-----|
|**field group:** <br/> |A section, repeating section, optional section, or repeating table. Sections and repeating tables are controls on a form that contain other controls and that repeat as needed. Users can insert multiple sections or rows when filling out the form.  <br/> |
|**DOM tree:** <br/> |The structure of the data source of the form. In particular, the collection of fields and groups that define and store the data for an InfoPath form.  <br/> |
   
## Conclusion

InfoPath uses open XML standards to provide users with flexible yet structured XML editing for data gathering. To provide an easy user interface for visualizing and editing hierarchical XML data, nested field groups that contains UI controls are mapped to the DOM tree. XSLT transformations enable the content of the UI views to be organized differently than the structure of the XML data.
  
InfoPath provides more flexibility than static forms, with more structured editing and validation than word processor documents. The result is a hybrid tool that combines the best of a traditional document editing experience with the rigorous data-capture capabilities of a forms package, which enables ordinary users to create valid XML documents that belong to a custom-defined XML schema. Integrated support for Web services enables easily defining views for editing XML documents that comply with a Web services schema.
  

