---
title: "Introduction to the Visio file format (.vsdx)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: overview
 
ms.assetid: 69736f40-8f67-46c2-abf6-82dffecb2274

description: "Learn about the new file format in Visio 2013, explore some high-level concepts for working with the Visio 2013 file format programmatically, and create a simple console application that examines a Visio 2013 file."
ms.localizationpriority: high
---

# Introduction to the Visio file format (.vsdx)

Learn about the new file format in Visio 2013, explore some high-level concepts for working with the Visio 2013 file format programmatically, and create a simple console application that examines a Visio 2013 file.
  
|||
|:-----|:-----|
|**In this article**         [Introduction](#vis15_IntroVSDX_Intro)          [What is the Visio 2013 file format "under the hood"?](#vis15_IntroVSDX_What)          [Developer scenarios for working with the Visio 2013 file format](#vis15_IntroVSDX_Scenarios)          [Exploring the Visio 2013 file format programmatically](#vis15_IntroVSDX_Explore)          [Additional resources](#vis15_IntroVSDX_Resources)||
   
## Introduction
<a name="vis15_IntroVSDX_Intro"> </a>

Visio 2013 introduces a new file format (.vsdx) for Visio that replaces the Visio binary file format (.vsd) and Visio XML Drawing file format (.vdx). Because the Visio 2013 file format is based upon Open Packaging Conventions and XML, developers who are familiar with these technologies can quickly learn how to work with Visio 2013 files programmatically. Developers who are familiar with the Visio XML Drawing file format (.vdx) from previous versions of Visio can find many of the same XML structures within the parts of .vsdx file format. Interoperability with Visio files is greatly increased since third-party software can manipulate Visio files at a file format level. The Visio 2013 file format is supported on Visio Services in Microsoft SharePoint Server 2013, without the need of an "intermediary" file format for publishing to SharePoint Server.
  
There are several file types, by extension, that comprise the Visio 2013 file format. These extensions include:
  
- .vsdx (Visio drawing)
    
- .vsdm (Visio macro-enabled drawing)
    
- .vssx (Visio stencil)
    
- .vssm (Visio macro-enabled stencil)
    
- .vstx (Visio template)
    
- .vstm (Visio macro-enabled template)
    
> [!NOTE]
> Only the macro-enabled files (.vsdm, .vssm, .vstm) can store VBA macros. You cannot store macros in files with a .vsdx, .vssx, or .vstx extension. 
  
## What is the Visio 2013 file format "under the hood"?
<a name="vis15_IntroVSDX_What"> </a>

The Visio 2013 file format uses the Open Packing Conventions (OPC), which defines a structured means to store application data together with related resources using a container of some sort─for example, a ZIP file. At a basic level, a Visio 2013 file is really a ZIP container that contains other types of files. In fact, you can save a drawing in Visio 2013 as a .vsdx file, rename the file extension to "\*.zip" in Windows Explorer, and then open the file like a folder to see the contents inside.
  
> [!NOTE]
>  This article contains only a brief overview of the Open Packaging Conventions. You can find more detailed coverage of the conventions in other articles: >  For more information about the Open Packaging Conventions themselves, see [OPC: A New Standard for Packaging Your Data](https://msdn.microsoft.com/magazine/cc163372.aspx). >  For more information about the Open Packaging Conventions and their use in Microsoft Office files, see [Essentials of the Open Packaging Conventions](https://msdn.microsoft.com/library/ee361919.aspx) and [Introducing the Office (2007) Open XML File Formats](https://msdn.microsoft.com/library/aa338205.aspx). 
  
### Packages and Package Parts

As started earlier, Visio 2013 files are ZIP containers or "packages" that hold other files (called "package parts") within them. A package part can be an XML file, an image, even a VBA solution. The parts within the package can be further divided into two broad categories, "document parts" and "relationship parts." The document parts contain the actual content and metadata of the Visio file, like the name of the file, the first page and all of the shapes that it contains, and even the data connections for the shapes. Images and text files within the package are considered document parts. Relationship parts are described in more detail later in this article.
  
> [!NOTE]
> If you open a Visio 2013 file using a ZIP utility, you can probably see several folders contained inside of the ZIP package. You can even manipulate these sub-addresses like folders using a ZIP utility. However, these "folders" represent sub-addresses within the ZIP package, not actual folders. You cannot use the programmatic equivalents of folders to work with these sub-addresses in your solution. 
  
Package parts─both document parts and relationship parts─also have associated content types. These content types are strings that define a MIME media type. These content types specify and scope the kind of MIME types that can be contained in the file.
  
### Relationships

The relationship parts (which end with the extension "\*.rels" and are stored in a "_rels" folder) describe how the parts within the package relate to each other and provide the structure of the file. A standalone XML document uses the parent/child relationship of elements to determine the relationship of entities to each other. Other files may use other hierarchies or file folder structure to describe the interaction of content in the file. For the Visio 2013 file format, the package is a valid Visio file if it contains the correct set of parts and the package contains the relationships between the parts. 
  
Relationship parts are XML documents that describe the relationships between different document parts within the package. They define an association between two items: a specified source (defined by the name and location of the relationship file) and a specified target document part. For example, relationship parts are used to describe which shape masters are associated with the file, how pages relate to the file and to each other, or how images and objects relate to a specific page. 
  
### Similarities and differences with Visio VDX schema

As mentioned, past versions of Visio also included an XML-based file format, the Visio XML Drawing Format or .vdx. (In previous versions of Visio, the schema used for the Visio XML Drawing Format is called DatadiagramML.) Some pieces from the Visio XML schema have stayed the same between the two file formats. For example, the **Windows** element and its children remain unchanged─with the exception that the **Windows** element is now a root element of an XML document (window.xml). 
  
The largest difference between the XML Drawing Format and the Visio 2013 file format is the packaging. An XML Drawing Format file could be manipulated like a normal stand-alone XML; the Visio 2013 file format must be manipulated as a package. In the Visio 2013, the XML has been divided up into parts for easier consumption. Another noticeable change is that the Visio 2013 file format stores all document properties in document parts described by the OPC standard (app.xml, core.xml, custom.xml).
  
However, there is one significant change that all Visio developers must be aware of: the introduction of the **Cell**, **Row**, and **Section** elements. In the XML Drawing File Format schema, individual rows and cells in the ShapeSheet are represented by named elements. For example, imagine that you have a document with a single page that contains a shape with a **PinX** value of "2" (meaning that the rotation pin of the shape is 2 inches from the left edge of the drawing). The relevant markup for that setting in the XML Drawing File Format is shown in the following code. 
  
```XML
<Shape ID="1" TextStyle="3" FillStyle="3" LineStyle="3" Type="Shape">
    <XForm> 
        <PinX Unit="IN">2</Pinx>
        <!--- Other cells in the Shape Transform section -->
    </XForm>
    <!--- Other rows and cells in the ShapeSheet -->
</Shape>

```

Here, the **PinX** element is a child of the **XForm** element, which is in turn a child of the **Shape** element. This models the Visio ShapeSheet UI, where the **PinX** cell is included in the **Shape Transform** section of a shape. 
  
In the Visio 2013 file format, all cells in the ShapeSheet─ **PinX**, **LinePattern**, an **X** cell in a **MoveTo** row in a **Geometry** section, etc.─are represented by one type of XML element, the **Cell** element. Different **Cell** elements are individuated from each other by the value of their **N** attribute. Thus, in the example from above, the data contained in the **PinX** cell in the ShapeSheet is stored in a VSDX file as shown in the following code. 
  
```XML
<Shape TextStyle="3" FillStyle="3" LineStyle="3" Type="Shape" ID="1">
    <Cell N="PinX" U="IN" V="2"/>
    <!--- Other cells in the ShapeSheet --> 
</Shape>
```

The **Cell** element for **PinX** (as well as other individual, named cells called "singleton cells" like **LinePattern** or **LockSelect**) is a direct child of the **Shape** element. No unique element is needed to represent the row that contains the **PinX** cell, as each shape can only have one **PinX**.
  
What about sections that include tabular data, like **Geometry** sections? For the cells in those sections, the Visio 2013 file format schema uses **Section** and **Row** elements─also distinguished by their **N** attribute or **T** attribute as shown below─to contain the data. For example, the same shape from the previous example might contain data in the **Geometry 1** section that looks like the following code in the XML Drawing schema. 
  
```XML
<Shape TextStyle="3" FillStyle="3" LineStyle="3" Type="Shape" ID="1">
    <!--- Other cells in the ShapeSheet -->
    <Geom IX="0">
        <!--- Other cells and rows in the Geometry 1 section -->
        <LineTo IX="1">
            <X F="Width*0">0</X>
            <Y F="Height*0">0</Y>
        </LineTo>
    </Geom>
</Shape>

```

However, it looks like the following code in the Visio 2013 file.
  
```XML
<Shape TextStyle="3" FillStyle="3" LineStyle="3" Type="Shape" ID="1">
    <!--- Other cells in the ShapeSheet -->
    <Section N="Geometry" IX="0"> 
        <!--- Other cells and rows in the Geometry 1 section -->
        <Row IX="1" T="LineTo">
            <Cell V="0" N="X" V="Width*0" />
            <Cell V="0" N="Y" V="Height*0" />
        </Row>
    </Section>
</Shape>

```

## Developer scenarios for working with the Visio 2013 file format
<a name="vis15_IntroVSDX_Scenarios"> </a>

As explained above, the Visio 2013 file format leverages several well-understood technologies like ZIP files and XML to store data. To manipulate a Visio 2013 drawing at the file level, a solution need only to use the .NET Framework namespaces and classes associated with working with ZIP files or XML, like [System.IO.Packaging](https://msdn.microsoft.com/library/system.io.packaging%28v=vs.110%29.aspx) or [System.Xml](https://msdn.microsoft.com/library/system.xml%28v=vs.110%29.aspx).
  
The key benefit to developers of the Visio 2013 file format is that you can read and write to Visio 2013 files without automating the Visio client application. Some scenarios that you might consider as a developer for working with Visio 2013 file format include:
  
- Checking individual Visio 2013 files for specific data. You can selectively read one item out of the ZIP container without having to extract the whole file.
    
- Updating libraries of Visio 2013 files with specific content. You can programmatically change the logo in all of the background pages to reflect new branding guidelines.
    
- Creating applications that consume Visio 2013 files. For example, you can build a tool that reads a Visio workflow diagram and then executes its own business logic based upon that workflow.
    
Be aware that because these solutions use standard .NET Framework assemblies, most solutions that can be run on a client machine can also be run on a server!
  
## Exploring the Visio 2013 file format programmatically
<a name="vis15_IntroVSDX_Explore"> </a>

The most basic and fundamental task for any developer working with the Visio 2013 file format is opening the file as a package and then accessing individual parts within the package. The **System.IO.Packaging.Package** in the WindowsBase.dll contains many classes that enable you to open and manipulate packages and parts. 
  
In the following code sample, you can see how to open a .vsdx file, read the list of parts in the package, and get information about each part.
  
### To open a .vsdx file and view the document parts

1. Open Visio 2013 and create a new document.
    
2. Create a new document and save it to the Desktop.
    
3. Open Visual Studio 2012.
    
4. On the **File** menu, choose **New**, and then choose ** Project **.
    
5. Under **Visual C#** or **Visual Basic**, expand **Windows**, and then select **Console Application**.
    
6. In the **Name** box, type 'VisioFileExplorer'. The Console Application project opens. 
    
7. In the **Solution Explorer**, right-click **VisioFileExplorer**, and then click **Add Reference**. 
    
8. In the **Add Reference** dialog box, under **Assemblies**, expand **Framework**, and then choose **WindowsBase**.
    
9. Paste the following code into the solution.
    
  ```cs
  using System;
  using System.Collections.Generic;
  using System.Linq;
  using System.Text;
  using System.IO;
  using System.IO.Packaging;
  using System.Diagnostics;
  namespace VisioFileExplorer
  {
      class Program
      {
          static void Main(string[] args)
          {    
              try
              {
                  Console.WriteLine("Opening the VSDX file ...");
                  // Need to get the folder path for the Desktop
                  // where the file is saved.
                  string dirPath = System.Environment.GetFolderPath(
                      System.Environment.SpecialFolder.Desktop);
                  DirectoryInfo myDir = new DirectoryInfo(dirPath);
                  // It is a best practice to get the file name string
                  // using a FileInfo object, but it isn't necessary.
                  FileInfo[] fInfos = myDir.GetFiles("*.vsdx");
                  FileInfo fi = fInfos[0];
                  string fName = fi.FullName;
                  // We're not going to do any more than open
                  // and read the list of parts in the package, although
                  // we can create a package or read/write what's inside.
                  using (Package fPackage = Package.Open(
                      fName, FileMode.Open, FileAccess.Read))
                  {
                      
                      // The way to get a reference to a package part is
                      // by using its URI. Thus, we're reading the URI
                      // for each part in the package.
                      PackagePartCollection fParts = fPackage.GetParts();
                      foreach (PackagePart fPart in fParts)
                      {
                          Console.WriteLine("Package part: {0}", fPart.Uri);
                      }
                  }   
              }
              catch (Exception err)
              {
                  Console.WriteLine("Error: {0}", err.Message);
              }
              finally
              {
                  Console.Write("\nPress any key to continue ...");
                  Console.ReadKey();
              }   
          }
      }
  }
  ```

  ```vb
  Imports System
  Imports System.Collections.Generic
  Imports System.Linq
  Imports System.Text
  Imports System.IO
  Imports System.IO.Packaging
  Imports System.Diagnostics
  Module Module1
      Sub Main()
          Try
              Console.WriteLine("Opening the VSDX file ...")
              ' Need to get the folder path for the Desktop
              ' or where the file is saved.
              Dim dirPath As String = System.Environment.GetFolderPath( _
                  System.Environment.SpecialFolder.Desktop)
              Dim myDir As New DirectoryInfo(dirPath)
              ' It is a best practice to get the file name string
              ' using a FileInfo object, but it isn't necessary.
              Dim fInfos As FileInfo() = myDir.GetFiles("*.vsdx")
              Dim fi As FileInfo = fInfos(0)
              Dim fName As String = fi.FullName
              ' We don't need to do any more than open
              ' and read the list of parts in the package, although
              ' we can create a package or read/write what's inside.
              Using fPackage As Package = Package.Open( _
                  fName, FileMode.Open, FileAccess.Read)
                  ' The way to get a reference to a document part is
                  ' by using its URI. Thus, we're reading the URI
                  ' for each document part in the package.
                  Dim fParts As PackagePartCollection = fPackage.GetParts()
                  For Each fPart As PackagePart In fParts
                      Console.WriteLine("Package part: {0}", fPart.Uri)
                  Next
              End Using
          Catch err As Exception
              Console.WriteLine("Error: {0}", err.Message)
          Finally
              Console.Write(vbLf &amp; "Press any key to continue ...")
              Console.ReadKey()
          End Try
      End Sub
  End Module
  
  ```

10. Press F5 to debug the solution. When the program has completed running, press any key to exit.
    
## See also
<a name="vis15_IntroVSDX_Resources"> </a>

For more information about the Visio 2013 file format, the Open Packaging Convention, or how to work with Visio 2013or Office OpenXML files programmatically, see the following resources:
  
- [Visio for developers](https://msdn.microsoft.com/office/aa905478.aspx)
    
- [OPC: A New Standard for Packaging Your Data](https://msdn.microsoft.com/magazine/cc163372.aspx).
    
- [Essentials of the Open Packaging Conventions](https://msdn.microsoft.com/library/ee361919.aspx)
    
- [Introducing the Office (2007) Open XML File Formats](https://msdn.microsoft.com/library/aa338205.aspx)
    

