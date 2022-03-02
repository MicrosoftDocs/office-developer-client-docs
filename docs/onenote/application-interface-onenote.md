---
title: "Application interface (OneNote)"
manager: lindalu
ms.date: 02/22/2022
ms.audience: Developer
ms.topic: overview
ms.assetid: 87926f7d-e1dc-41d5-8805-6ba91fc7b154
description: "The Application interface includes methods help retrieve, manipulate, and update OneNote information and content. The methods are in four general categories:"
ms.localizationpriority: high
---

# Application interface (OneNote)

The **Application** interface includes methods help retrieve, manipulate, and update OneNote information and content. The methods are in four general categories:
  
- **Notebook structure** &ndash; Methods for working with notebook structure, including those for discovering, opening, modifying, closing, and deleting notebooks, section groups, and sections.

- **Page content** &ndash; Methods for working with pages and page content, including those for discovering, modifying, saving, and deleting page content. Page content includes binary objects, such as ink and images, and text objects, such as outlines.

- **Navigation** &ndash; Methods for finding, linking to, and navigating to pages and objects.

- **Functional** &ndash; All other methods that perform certain actions or set parameters in OneNote.

In addition, the **Application** interface includes a number of *properties* and *events*.
  
## Notebook Structure methods

<a name="ON14DevRef_Application_NotebookStructure"> </a>

The methods described in this section enable you to discover, open, modify, close, and delete OneNote notebooks, section groups, and sections.
  
### GetHierarchy method

|||
|:-----|:-----|
|**Description** <br/> |Gets the notebook node hierarchy structure, starting from the node you specify (all notebooks or a single notebook, section group, or section), and extending downward to all descendants at the level you specify. |
|**Syntax** <br/> | `HRESULT GetHierarchy(`<br/>`[in]BSTR bstrStartNodeID,`<br/>`[in]HierarchyScope hsScope,`<br/>`[out]BSTR * pbstrHierarchyXmlOut,`<br/>`[in,defaultvalue(xs2013)]XMLSchema xsSchema);` <br/> |
|**Parameters** <br/> | *bstrStartNodeID* &ndash; The node (notebook, section group, or section) whose descendants you want. If you pass a null string (""), the method gets all nodes below the root node (that is, all notebooks, section groups, and sections). If you specify a notebook, section group, or section node, the method gets only descendants of that node.<br/>*hsScope* &ndash; The lowest descendant node level you want. For example, if you specify pages, the method gets all nodes as far down as the page level. If you specify sections, the method gets only section nodes below the notebook. For more information, see the **HierarchyScope** enumeration in the [Enumerations](enumerations-onenote-developer-reference.md#odc_HierarchyScope) topic.<br/>*pbstrHierarchyXmlOut* &ndash; (Output parameter) A pointer to the string in which you want OneNote to write the XML output.<br/>*xsSchema* &ndash; (Optional) The version of the OneNote XML schema, of type **XMLSchema**, that you want to be output. You can specify whether you want XML Schema version 2013, 2010, 2007, or the current version.<br/>**NOTE**:  We recommend specifying a version of OneNote (such as **xs2013**) instead of using **xsCurrent** or leaving it blank, because this will allow your add-in to work with future versions of OneNote.           |

The GetHierarchy method returns a string in OneNote 2013 XML format by default or you can set the preferred XML schema version by using the optional  *xsSchema* parameter.
  
Depending on the parameters you pass, the **GetHierarchy** method can return various lists (for example all notebooks, all sections in all notebooks, all pages within a given section, or all pages within a given notebook). For each node, the XML string returned provides properties (for example, the section or page title, ID, and last-modified time).
  
Not all combinations of start node and scope are valid. For example, if you specify a section start node and a notebook scope, **GetHierarchy** returns a null result because a notebook is higher in the node hierarchy than a section.
  
The following C# example shows how to use the **GetHierarchy** method to get the entire OneNote hierarchy, including all notebooks, down to the page level. It copies the output string to the Clipboard, from which you can paste the string into a text editor for review.
  
```cs
static void GetEntireHierarchy()
    {
        String strXML;
        OneNote.Application onApplication = new OneNote.Application();
        onApplication.GetHierarchy(null, 
            OneNote.HierarchyScope.hsPages, out strXML);
        Clipboard.SetText(strXML);
        MessageBox.Show("The XML has been copied to the clipboard");
    }

```

### UpdateHierarchy method

|||
|:-----|:-----|
|**Description**|Modifies or updates the hierarchy of notebooks. For example, you can add sections or section groups to a notebook, add a new notebook, move sections within a notebook, change the name of a section, add pages to a section, or change the order of pages within sections.|
|**Syntax**| `HRESULT UpdateHierarchy(`<br/>`[in]BSTR bstrChangesXmlIn,`<br/>`[in,defaultvalue(xsCurrent)] XMLSchema xsSchema);`|
|**Parameters**| *bstrChangesXmlIn* &ndash; A string that contains OneNote XML code that specifies the hierarchy changes to make. For example, if you want to insert a new section, you can add a **Section** element in the XML string to indicate where you want the new section to be added. Alternatively, if you want to change the name of an existing section, you can keep the same section ID and change its **name** attribute in the XML code.<br/><br/>*xsSchema* &ndash; (Optional) The OneNote schema version of the string  *bstrChangesXmln*. This optional value is used to specify the version of the OneNote XML schema that the  *bstrChangesXmlIn* string is in. If this value is not specified, OneNote will assume that the XML is in schema version  *xsCurrent*. <br/><br/>**NOTE**:  We recommend specifying a version of OneNote (such as **xs2013**) instead of using **xsCurrent** or leaving it blank, because this will allow your add-in to work with future versions of OneNote.           |

If you pass only a partial OneNote XML string for the  *bstrChangesXmlIn* parameter, OneNote attempts to infer the changes you want. For example, if you include a **Notebook** element that contains only one section, OneNote adds the section after any existing sections. However, if the operation you specify is ambiguous, the result can be hard to determine. For example, if an existing notebook contains four sections, and the XML string you pass includes the notebook and only the fourth and first sections (in that order), OneNote might place the second and third sections before the fourth section or after the first section.
  
You cannot use the **UpdateHierarchy** method to delete part of a notebook. That is, passing an XML string that includes only part of an existing hierarchy does not delete sections that are not included in the string. To delete part of a hierarchy, use the **DeleteHierarchy** method.
  
The following C# code shows one way to use the **UpdateHierarchy** method to change the OneNote hierarchy, by changing the name of an existing section. It reads XML code from a sample file named ChangeSectionName.xml at the root of drive C, loads it into an XML document, and then passes the XML structure of that document to the method.
  
```cs
static void UpdateExistingHierarchy()
    {
        OneNote.Application onApplication = new OneNote.Application();
        
        // Get the XML from the file.
        XmlTextReader reader = new XmlTextReader("C:\\ChangeSectionName.xml");
        reader.WhitespaceHandling = WhitespaceHandling.None;
        XmlDocument xmlDocIn = new XmlDocument();
        xmlDocIn.Load(reader);
        
        // Update the hierarchy.
        onApplication.UpdateHierarchy(xmlDocIn.OuterXml,
        OneNote.XMLSchema.xs2007);   
    }

```

The following XML code is an excerpt of the ChangeSectionName.xml file that the previous C# code passes to the method. When the XML is passed to the **UpdateHierarchy** method, it changes the name of one of the sections in the existing hierarchy (by changing the value of the **name** attribute to "My Renamed Section"). It then removes all the sections except the one whose name was changed. In addition, the code removes unnecessary attributes from the target **Section** element, including the **lastModifiedTime**, **isCurrentlyViewed**, and **color** attributes, leaving only the **name**, **ID**, and **path** attributes intact.
  
```XML
<?xml version="1.0" ?> 
    <one:Notebooks xmlns:one="http://schemas.microsoft.com/office/onenote/12/2004/onenote"> 
        <one:Notebook name="My Notebook" nickname="My Notebook" ID="{0B8E7305-AC2C-4BCB-8651-1CDA55AAE14C}{1}{B0}"> 
            <one:Section name="My Renamed Section" ID="{5F4E2908-44BA-4C02-91FE-49FC665E9A33}{1}{B0}" path="C:\My Section.one" /> 
        </one:Notebook> 
    </one:Notebooks>
```

The preceding XML code was obtained by using the code shown in the example for the **GetHierarchy** method, which is modified, as follows, to limit the scope to sections.
  
```cs
static void GetAllSections()
    {
        String strXML;
        OneNote.Application onApplication = new OneNote.Application();
        onApplication.GetHierarchy(System.String.Empty, 
            OneNote.HierarchyScope.hsSections, out strXML);
        Clipboard.SetText(strXML.ToString());
        MessageBox.Show("The XML has been copied to the Clipboard");
    }

```

The following C# example shows a complete console application that searches for a section named "`Sample_Section`", prompts the user to input a new name for the section, and then uses the **UpdateHierarchy** method to change the section name to the name that the user typed. Before running the code, change "`Sample_Section`" to the name of a section that exists in your OneNote hierarchy.
  
```cs
    static void Main(string[] args)
    {
        
        // OneNote 2013 Schema namespace.
        string strNamespace = "http://schemas.microsoft.com/office/onenote/2013/onenote";
        string outputXML;
        Application onApplication = new Application();
        onApplication.GetHierarchy(null, HierarchyScope.hsSections, out outputXML);
        // Load a new XmlDocument.
        XmlDocument xmlDoc = new XmlDocument();
        xmlDoc.LoadXml(outputXML);
        XmlNamespaceManager nsmgr = new XmlNamespaceManager(xmlDoc.NameTable);
            nsmgr.AddNamespace("one", strNamespace);
        // Search for the section named "Sample_Section".
        XmlNode xmlNode = xmlDoc.SelectSingleNode("//one:Section[@name='Sample_Section']", nsmgr);
        // Prompt for a new section title.
        System.Console.Write("Please enter a new title for the section: ");
        string input = System.Console.ReadLine();
        xmlNode.Attributes["name"].Value = input; 
        // Update the section with the new title.
        onApp.UpdateHierarchy(xmlNode.OuterXml);
        System.Console.Write("Done!\n");
    }

```

### OpenHierarchy method

|||
|:-----|:-----|
|**Description** <br/> |Opens a section group or section that you specify. |
|**Syntax** <br/> | `HRESULT OpenHierarchy(`<br/>`[in]BSTR bstrPath,`<br/>`[in]BSTR bstrRelativeToObjectID,`<br/>`[out]BSTR * pbstrObjectID,`<br/>`[in,defaultvalue(cftNone)]CreateFileType cftIfNotExist);` <br/> |
|**Parameters** <br/> | *bstrPath* &ndash; The path that you want to open. For a notebook, or for a section group in a notebook, *bstrPath* can be a folder path or the path to an .one section file. If you specify the path to an .one section file, you must include the .one extension on the file-path string.<br/>*bstrRelativeToObjectID* &ndash; The OneNote ID of the parent object (notebook or section group) under which you want the new object to open. If the *bstrPath* parameter is an absolute path, you can pass an empty string ("") for *bstrRelativeToObjectID*. Alternatively, you can pass the object ID of the notebook or section group that should contain the object (section or section group) that you want to create, and then specify the file name (for example, section1.one) of the object that you want to create under that parent object.<br/>*pbstrObjectID* &ndash; (Output parameter) The object ID that OneNote returns for the notebook, section group, or section that the **OpenHierarchy** method opens. This parameter is a pointer to the string into which you want the method to write the ID.<br/>*cftlfNotExist* &ndash; (Optional) An enumerated value from the [CreateFileType](enumerations-onenote-developer-reference.md#odc_CreateFileType) enumeration. If you pass a value for  *cftIfNotExist*, the **OpenHierarchy** method creates the section group or section file at the specified path only if the file does not already exist. |

If you specify a section group that is not in an open notebook, the **OpenHierarchy** method opens the section group as a notebook. If you specify a section that is not in an open notebook, the **OpenHierarchy** method opens the section in the Recent Opened Sections section group. If you specify a section group or section that is already in an open notebook, nothing happens because the section group or section is already open, as well. In any case, **OpenHierarchy** returns the object ID for the section group, notebook, or section that you specify, so that you can use it in other operations.
  
You can also use the **OpenHierarchy** method to create new sections, instead of doing so by importing XML.
  
The following code shows how to use the **OpenHierarchy** method to open the Meetings section in the Work notebook and get the ID for the section. If the section does not already exist, OneNote creates it in the location that you specify.
  
```cs
static void OpenSection()
    {
        String strID;
        OneNote.Application onApplication = new OneNote.Application();
        onApplication.OpenHierarchy("C:\\Documents and Settings\\user\\My Documents\\OneNote Notebooks\\Work\\Meetings.one", 
        System.String.Empty, out strID, OneNote.CreateFileType.cftSection);
    }

```

### DeleteHierarchy method

|||
|:-----|:-----|
|**Description** <br/> |Deletes any hierarchy object (a section group, section, or page) from the OneNote notebook hierarchy. |
|**Syntax** <br/> | `HRESULT DeleteHierarchy(`<br/>`[in]BSTR bstrObjectID,`<br/>`[in,defaultvalue(0)]DATE dateExpectedLastModified,`<br/>`[in,defaultvalue(false)]VARIANT_BOOL deletePermanently);` <br/> |
|**Parameters** <br/> | *bstrObjectID* &ndash; The OneNote ID of the object you want to delete. The object can be a section group, section, or page.<br/>*dateExpectedLastModified* &ndash; (Optional) The date and time that you think the object you want to delete was last modified. If you pass a non-zero value for this parameter, OneNote proceeds with the update only if the value you pass matches the actual date and time the object was last modified. Passing a value for this parameter helps prevent accidentally overwriting edits users made since the last time the object was modified.<br/>*deletePermanently* &ndash; (Optional) **true** to permanently delete the content; **false** to move the content into the OneNote recycle bin for the corresponding Notebook (the default). If the Notebook is in OneNote 2007 format, no recycle bin exists, so the content is permanently deleted. |

### CreateNewPage method

|||
|:-----|:-----|
|**Description** <br/> |Adds a new page to the section you specify. The new page is added as the last page of the section  <br/> |
|**Syntax** <br/> | `HRESULT CreateNewPage(`<br/>`[in]BSTR bstrSectionID,`<br/>`[out]BSTR * pbstrPageID);`<br/>`[in,defaultvalue(npsDefault)]NewPageStyle npsNewPageStyle);` <br/> |
|**Parameters** <br/> | *bstrSectionID* &ndash; A string that contains the OneNote ID of the section in which you want to create the new page.<br/>*pbstrPageID* &ndash; (Output parameter) A pointer to the string into which the method writes the OneNote ID for the newly created page.<br/>*npsNewPageStyle* &ndash; A value from the **NewPageStyle** enumeration that specifies the style of the page to be created. |

The OneNote API includes the **CreateNewPage** method as a convenience. You can achieve the same result, with greater control over how the new page is positioned in the hierarchy, by calling the **UpdateHierarchy** method. The **UpdateHierarchy** method also lets you create subpages at the same time as you create a new page.
  
### CloseNotebook method

|||
|:-----|:-----|
|**Description** <br/> |Closes the specified notebook. |
|**Syntax** <br/> | `HRESULT CloseNotebook(`<br/>`[in]BSTR bstrNotebookID,`<br/>`[in,defaultvalue(false)]VARIANT_BOOL force);` <br/> |
|**Parameters** <br/> | *bstrNotebookID* &ndash; The OneNote ID of the notebook you want to close.<br/>*force* &ndash; (Optional) **true** to close the notebook, even if there are changes in the notebook that OneNote cannot sync before closing; otherwise, **false** (the default). |

You can use the **CloseNotebook** method to close the notebook you specify. When you call this method, OneNote synchronizes any offline files with current notebook content, if necessary, and then closes the specified notebook. After the method returns, the notebook no longer appears in the list of open notebooks in the OneNote user interface (UI).
  
### GetHierarchyParent method

|||
|:-----|:-----|
|**Description** <br/> |Gets the OneNote ID for the parent object of a OneNote object. |
|**Syntax** <br/> | `HRESULT GetHierarchyParent (`<br/>`[in]BSTR bstrObjectID,`<br/>`[out]BSTR * pbstrParentID);` <br/> |
|**Parameters** <br/> | *bstrObjectID* &ndash; A string that contains the OneNote ID of the object of which you want to find the parent object.<br/>*pbstrParentID* &ndash; (Output parameter) A pointer to the string into which the method writes the OneNote ID of the parent object. |

If the OneNote object has no parent object (for example, when a user wants to get the parent of a Notebook), an exception is thrown.
  
### GetSpecialLocation method

|||
|:-----|:-----|
|**Description** <br/> |Finds the path to the location where OneNote stores certain special items, such as backups, unfiled notes, and the default notebook. |
|**Syntax** <br/> | `HRESULT GetSpecialLocation(`<br/>`[in]SpecialLocation slToGet,`<br/>`[out]BSTR * pbstrSpecialLocationPath);` <br/> |
|**Parameters** <br/> | *slToGet* &ndash; One of the [SpecialLocation](enumerations-onenote-developer-reference.md#odc_SpecialLocation) enumeration values that specifies the special folder location to get.<br/>*pbstrSpecialLocationPath* &ndash; (Output parameter) A pointer to the string into which you want OneNote to write the path of the special folder. |

You can use this method to determine the location on disk of the Unfiled Notes folder. That is the folder in which OneNote stores notes that are created when you drag an item into OneNote, as well as notes that come directly from other applications (such as those that result when you click **Send to OneNote** in Microsoft Outlook or Microsoft Internet Explorer).
  
## Page Content methods

<a name="ON14DevRef_Application_PageContent"> </a>

The methods described in this section enable you to discover, update, and delete the content on pages in OneNote notebooks, as well as to publish OneNote content.
  
### GetPageContent method

|||
|:-----|:-----|
|**Description**|Gets all of the content (in OneNote XML format) of the specified page.|
|**Syntax**| `HRESULT GetPageContent(`<br/>`[in]BSTR bstrPageID,`<br/>`[out]BSTR * pbstrPageXmlOut,`<br/>`[in,defaultvalue(piBasic)]PageInfo pageInfoToExport,`<br/>`[in,defaultvalue(xsCurrent)]XMLSchema xsSchema);`|
|**Parameters**| *bstrPageId* &ndash; The OneNote ID of the page whose content you want to get.<br/><br/>*pbstrPageXmlOut* &ndash; (Output parameter) A pointer to the string into which you want OneNote to write the XML output.<br/><br/>*pageInfoToExport* &ndash; (Optional) Specifies whether the **GetPageContent** method returns binary content, embedded in the XML code and base-64 encoded. Binary content can include, for example, images and ink data. The *pageInfoToExport* parameter also specifies whether to mark up the selection in the XML code that the **GetPageContent** method returns. It takes an enumerated value from the [PageInfo](enumerations-onenote-developer-reference.md#odc_PageInfo) enumeration.<br/><br/>*xsSchema* &ndash; (Optional) The version of the OneNote XML schema, of type **XMLSchema**, that you want to be output. You can specify whether you want XML Schema version 2013, 2010, 2007, or the current version. <br/><br/>**NOTE**:  We recommend specifying a version of OneNote (such as **xs2013**) instead of using **xsCurrent** or leaving it blank, because this will allow your add-in to work with future versions of OneNote.           |

By default, to avoid excess length in the XML string it returns, OneNote does not embed binary content in the XML code. For the same reason, it does not mark up the current selection with selection attributes. Binary objects include a OneNote ID in their tags. To get a binary object, you call the **GetBinaryPageContent** method and pass it the OneNote ID you get from the **GetPageContent** method. You use the **GetPageContent** method when you do not need the binary data immediately.
  
### UpdatePageContent method

|||
|:-----|:-----|
|**Description**|Updates or modifies the content on the page.|
|**Syntax**| `HRESULT UpdatePageContent(`<br/>`[in]BSTR bstrPageChangesXmlIn,`<br/>`[in,defaultvalue(0)]DATE dateExpectedLastModified,`<br/>`[in,defaultvalue(xsCurrent)]XMLSchema xsSchema,`<br/>`[in,defaultvalue(false)]VARIANT_BOOL force);`|
|**Parameters**| *bstrPageChangesXmlIn* &ndash; A string that contains OneNote XML code that includes the changes you want to make to the page.<br/><br/>*dateExpectedLastModified* &ndash; (Optional) The date and time that you think the page you want to update was last modified. If you pass a non-zero value for this parameter, OneNote proceeds with the update only if the value you pass matches the actual date and time the page was last modified. Passing a value for this parameter helps prevent accidentally overwriting edits users made since the last time the page was modified.<br/><br/>*xsSchema* &ndash; (Optional) The version of the OneNote XML schema, of type **XMLSchema**, that you want to be output. You can specify whether you want XML schema version 2013, 2010, 2007, or the current version. <br/><br/>**NOTE**:  We recommend specifying a version of OneNote (such as **xs2013**) instead of using **xsCurrent** or leaving it blank, because this will allow your add-in to work with future versions of OneNote.<br/><br/>*force*(Optional) **true** to update the page content, even if there is unknown data on the page from a future version of OneNote; otherwise, **false** (the default). |

You can use this method to modify the page in various ways. For example, you can use the **UpdatePageContent** method to add an outline to a page, change the content of an outline, add images, add ink, move content, or modify text in outlines.
  
As a more specific example, you might use the **GetPageContent** method to export an existing page, make some changes to the XML code for the page, and then use the **UpdatePageContent** method to import the entire page again. Or, you might use this method to add new page objects, such as images, to the bottom of an existing page.
  
The only objects that you must include in the XML code that you pass to the **UpdatePageContent** method are page-level objects (such as outlines, images on the page, or ink on the page) that have changed. This method does not modify or remove page-level objects that you do not specify in the *bstrPageChangesXmlIn* parameter. The method entirely replaces page-level objects, such as outlines, whose IDs match those of the objects you pass. Consequently, you must fully specify all page-level objects in your code, including their existing content and changes you want to make to them.
  
For example, if your page contains an outline and a background page image, you can replace the outline and leave the image unchanged by completely specifying the outline in the XML code, using the ID of the existing outline, and not including the image in the code. Because the revised outline you include in the code completely replaces the existing outline, you must include the entire contents of the outline.
  
Also, the **UpdatePageContent** method modifies only element properties that you specify in the *bstrPageChangesXmlIn* parameter. For example, if you specify some, but not all, properties of the **PageSettings** element, the properties that you do not specify remain unchanged.
  
The following example shows how to use the **UpdatePageContent** method to change the title of a page and add some sample text to the page. Before running the code, substitute a valid page ID for the page ID shown in the code, so that the code works on your computer. You can get the page ID for a page by using the **GetHierarchy** method and examining the output.
  
```cs
static void UpdatePageContent()
    {
        OneNote.Application onApplication = new OneNote.Application();
        String strImportXML;
        strImportXML = "<?xml version=\"1.0\"?>" +
            "<one:Page xmlns:one=\"http://schemas.microsoft.com/office/onenote/12/2004/onenote\" 
            ID=\"{3428B7BB-EF39-4B9C-A167-3FAE20630C37}{1}{B0}\">" +
            "    <one:PageSettings RTL=\"false\" color=\"automatic\">" +
            "        <one:PageSize>" +
            "            <one:Automatic/>" +
            "        </one:PageSize>" +
            "        <one:RuleLines visible=\"false\"/>" +
            "    </one:PageSettings>" +
            "    <one:Title style=\"font-family:Calibri;
                 font-size:17.0pt\" lang=\"en-US\">" +
            "        <one:OE alignment=\"left\">" +
            "            <one:T>" +
            "                <![CDATA[My Sample Page]]>" +
            "            </one:T>" +
            "        </one:OE>" +
            "    </one:Title>" +
            "    <one:Outline >" +
            "        <one:Position x=\"120\" y=\"160\"/>" +
            "        <one:Size width=\"120\" height=\"15\"/>" +
            "        <one:OEChildren>" +
            "            <one:OE alignment=\"left\">" +
            "                <one:T>" +
            "                    <![CDATA[Sample Text]]>" +
            "                </one:T>" +
            "            </one:OE>" +
            "        </one:OEChildren>" +
            "    </one:Outline>" +
            "</one:Page>";
        // Update the page content.
        onApplication.UpdatePageContent(strImportXML, System.DateTime.MinValue);
    }

```

### GetBinaryPageContent method

|||
|:-----|:-----|
|**Description** <br/> |Returns a binary object, such as ink or images, on an OneNote page as a base-64-encoded string. |
|**Syntax** <br/> | `HRESULT GetBinaryPageContent(`<br/>`[in]BSTR bstrPageID,`<br/>`[in]BSTR bstrCallbackID,`<br/>`[out]BSTR * pbstrBinaryObjectB64Out);` <br/> |
|**Parameters** <br/> | *bstrPageID* &ndash; The OneNote ID of the page that contains the binary object to get.<br/>*bstrCallBackID* &ndash; The OneNote ID of the binary object you want to get. This ID, known as a **callbackID**, is in the OneNote XML code for a page returned by the **GetPageContent** method.<br/>*pbstrBinaryObectB64Out* &ndash; (Output parameter) A pointer to a string into which OneNote writes the binary object as a base-64-encoded string. |

### DeletePageContent method

|||
|:-----|:-----|
|**Description** <br/> |Deletes an object &ndash; such as an **Outline**, **Ink**, or **Image** object from a page. |
|**Syntax** <br/> | `HRESULT DeletePageContent(`<br/>`[in]BSTR bstrPageID,`<br/>`[in]BSTR bstrObjectID,`<br/>`[in,defaultvalue(0)]DATE dateExpectedLastModified,`<br/>`[in,defaultvalue(#)]VARIANT_BOOL force);` <br/> |
|**Parameters** <br/> | *bstrPageID* &ndash; The OneNote ID of the page that contains the object to delete.<br/>*bstrObjectID* &ndash; The OneNote ID of the object that you want to delete.<br/>*dateExpectedLastModified* &ndash; (Optional) The date and time that you think the page that contains content you want to delete was last modified. If you pass a non-zero value for this parameter, OneNote proceeds with the deletion only if the value you pass matches the actual date and time the page was last modified. Passing a value for this parameter helps prevent accidentally overwriting edits made by users since the last time the page was modified.<br/>*force* &ndash; (Optional) **true** to update the page content, even if there is unknown data on the page from a future version of OneNote; otherwise, **false** (the default). |

### Publish method

|||
|:-----|:-----|
|**Description** <br/> |Exports the page you specify to a file in any format that OneNote supports. |
|**Syntax** <br/> | `HRESULT Publish(`<br/>`[in]BSTR bstrHierarchyID,`<br/>`[in]BSTR bstrTargetFilePath,`<br/>`[in,defaultvalue(pfOneNote)]PublishFormat pfPublishFormat,`<br/>`[in,defaultvalue(0)]BSTR bstrCLSIDofExporter);` <br/> |
|**Parameters** <br/> | *bstrHierarchyID* &ndash; The OneNote ID of the hierarchy you want to export.<br/>*bstrTargetFilePath* &ndash; The absolute path to the location where you want to save the resulting output file. The file you specify must be one that does not already exist at that location.<br/>*pfPublishFormat* &ndash; One of the [PublishFormat](enumerations-onenote-developer-reference.md#odc_PublishFormat) enumeration values that specifies the format in which you want the published page to be (for example, MTHML, PDF, and so on).<br/>*bstrCLSIDofExporter* &ndash; The class ID (CLSID) of a registered COM application that can export Microsoft Windows enhanced metafiles (.emf). The COM application must implement the **IMsoDocExporter** interface. This parameter is included to permit third-party developers to write their own code to publish OneNote content in a custom format. For more information about the **IMsoDocExporter** interface, see [Extending the Office 2007 Fixed-Format Export Feature](https://msdn.microsoft.com/library/office/aa338206%28v=office.12%29.aspx). |

Currently, OneNote supports the following file formats:
  
- MHTML files (.mht)
- Adobe Acrobat PDF files (.pdf)
- XML Paper Specification (XPS) files (.xps)
- OneNote 2013, 2010 or 2007 files (.one)
- OneNote Package files (.onepkg)
- Microsoft Word documents (.doc or .docx)
- Microsoft Windows Enhanced Metafiles (.emf)
- HTML files (.html)

This method produces exactly the same results you would get by clicking **Publish** in the UI and specifying the format.
  
## Navigation methods

<a name="ON14DevRef_Application_Navigation"> </a>

The methods described in this section enable you to find, navigate to, and link to OneNote notebooks, section groups, sections, pages, and page objects.
  
### NavigateTo method

|||
|:-----|:-----|
|**Description** <br/> |Navigates to the specified object (for example, sections, pages, and **Outline** elements within pages). |
|**Syntax** <br/> | `HRESULT NavigateTo(`<br/>`[in]BSTR bstrHierarchyObjectID,`<br/>`[in,defaultvalue(#)]BSTR bstrObjectID,`<br/>`[in,defaultvalue(0)]VARIANT_BOOL fNewWindow);` <br/> |
|**Parameters** <br/> | *bstrHierarchyObjectID* &ndash; The OneNote ID of the object you want to navigate to in the OneNote Hierarchy.<br/>*bstrObjectID* &ndash; The OneNote ID of the object you want to navigate to on the OneNote page.<br/>*fNewWindow* &ndash; (Optional) **true** to open specified object in a new OneNote window. **false** does not open a new OneNote window if one is open. |

### NavigateToUrl method

|||
|:-----|:-----|
|**Description** <br/> |If passed a OneNote link (onenote://), opens the OneNote window to the corresponding location in OneNote. If the link is external to OneNote (such as https:// or file://), a security dialog box will appear. Upon dismissal, OneNote attempts to open the link and an **HResult.hrObjectDoesNotExist** error is returned. |
|**Syntax** <br/> | `HRESULT NavigateTo(`<br/>`[in]BSTR bstrUrl,`<br/>`[in,defaultvalue(0)]VARIANT_BOOL fNewWindow);` <br/> |
|**Parameters** <br/> | *bstrUrl* &ndash; A string that indicates where to navigate to. This could be a OneNote link, or any other URL, such as a web link or network location.<br/>*fNewWindow* &ndash; (Optional) **true** to open the specified URL in a new OneNote window. **false** does not open a new OneNote window if one is open. |

### GetHyperLinkToObject method

|||
|:-----|:-----|
|**Description** <br/> |Gets a OneNote hyperlink to the specified notebook, section group, section, page, or page object. |
|**Syntax** <br/> | `HRESULT GetHyperlinkToObject(`<br/>`[in] BSTR bstrHierarchyID,`<br/>`[in] BSTR bstrPageContentObjectID,`<br/>`[out] BSTR * pbstrHyperlinkOut);` <br/> |
|**Parameters** <br/> | *bstrHierarchyID* &ndash; The OneNote ID for the notebook, section group, section, or page for which you want a hyperlink.<br/>*bstrPageContentObjectID* &ndash; (Optional) The OneNote ID for the object within the page for which you want a hyperlink. For example, the object can be an outline or **Outline** element. If you pass an empty string (""), the returned link points to the notebook, section group, section, or page that you specified in the *bstrHierarchyID* parameter. If you pass a non-empty string for the  *bstrPageContentObjectID* parameter, the _*bstrHierarchyID*parameter must be a reference to the page that contains the specified object.<br/>*pbstrHyperlinkOut* &ndash; (Output parameter) A pointer to a string into which the **GetHyperlinkToObject** method writes the output hyperlink text. |

When you attempt to navigate to the resulting link, OneNote opens and displays the specified object in the browser.
  
### GetWebHyperlinktoObject method

|||
|:-----|:-----|
|**Description** <br/> |Returns a hyperlink to an object that opens in the OneNote Web Client. |
|**Syntax** <br/> | `HRESULT GetWebHyperlinkToObject (`<br/>`[in] BSTR bstrHierarchyID,`<br/>`[in] BSTR bstrPageContentObjectID,`<br/>`[out] BSTR * pbstrHyperlinkOut);` <br/> |
|**Parameters** <br/> | *bstrHierarchyID* &ndash; The OneNote ID for the notebook, section group, section or page for which you want a web hyperlink.<br/>*bstrPageContentObjectID* &ndash; (Optional) The OneNote ID for the object within the page for which you want a hyperlink. For example, the object can be an outline or **Outline** element. If you pass an empty string (""), the returned link points to the notebook, section group, section, or page that you specified in the *bstrHierarchyID* parameter. If you pass a non-empty string for the  *bstrPageContentObjectID* parameter, the _*bstrHierarchyID*parameter must be a reference to the page that contains the specified object.<br/>*pbstrHyperlinkOut* &ndash; (Output parameter) A pointer to a string into which the **GetWebHyperlinkToObject** method writes the output hyperlink text. If a web hyperlink cannot be created for the notebook, a null value is returned. |

### FindPages method

|||
|:-----|:-----|
|**Description**|Returns a list of pages that match the specified query term.|
|**Syntax**| `HRESULT FindPages(`<br/>`[in]BSTR bstrStartNodeID,`<br/>`[in]BSTR bstrSearchBSTR,`<br/>`[out]BSTR * pbstrHierarchyXmlOut,`<br/>`[in,defaultvalue(#)]VARIANT_BOOL fIncludeUnindexedPages,`<br/>`[in,defaultvalue(0)]VARIANT_BOOL fDisplay,`<br/>`[in,defaultvalue(#)]XMLSchema xsSchema);`|
|**Parameters**| *bstrStartNodeID* &ndash; The node (root, notebook, section group, or section) below which to search for content. This parameter sets the scope for the search.<br/><br/>*bstrSearchString* &ndash; The search string. Pass exactly the same string that you would type into the search box in the OneNote UI. You can use bitwise operators, such as **AND** and **OR**, which must be all uppercase.<br/><br/>*pbstrHierarchyXmlOut* &ndash; (Output parameter) A pointer to a string into which you want OneNote to write the output XML string. The resulting XML string contains the notebook hierarchy from the root downward to, and including, any pages that match the search string. For example, the **FindPages** method does not list sections that have no page matches in the hierarchy. Also, if only one page in a single section matches the string, the returned hierarchy includes the path to that section and page, but to no other parts of the notebook hierarchy.<br/><br/>*fIncludeUnindexedPages* &ndash; (Optional) **true** to search pages that have not been indexed by Windows Search; otherwise, **false**.<br/><br/>*fDisplay* &ndash; (Optional) **true** to also run the search in the UI for the user, just as if the user had typed it themselves. **false** to perform the query with no change to the UI (the default).<br/><br/>*xsSchema* &ndash; (Optional) The OneNote schema version of the string  *pbstrHierarchyXmlOut*. This optional value is used to specify the version of the OneNote XML schema that contains the _pbstrHierarchyXmlOut_ string. If this value is not specified, OneNote will assume that the XML is in schema version  *xsCurrent*. <br/><br/>**NOTE**:  We recommend specifying a version of OneNote (such as **xs2013**) instead of using **xsCurrent** or leaving it blank, because this will allow your add-in to work with future versions of OneNote.           |

 **FindPages** works only if you have Microsoft Search 3.0 or 4.0 installed on your computer. Windows Vista and Windows 7 include this component. However, if you are running an earlier version of Windows, you must install [Windows Search](https://www.microsoft.com/windows/products/winfamily/desktopsearch/getitnow.mspx) for **FindPages** to work.
  
### FindMeta method

|||
|:-----|:-----|
|**Description**|Returns a list of OneNote objects that contain metadata that matches the specified query term.|
|**Syntax**| `HRESULT FindMeta (`<br/>`[in]BSTR bstrStartNodeID,`<br/>`[in]BSTR bstrSearchBSTRName,`<br/>`[out]BSTR * pbstrHierarchyXmlOut,`<br/>`[in,defaultvalue(#)]VARIANT_BOOL fIncludeUnindexedPages,`<br/>`[in,defaultvalue(#)]XMLSchema xsSchema);`|
|**Parameters**| *bstrStartNodeID* &ndash; The node (root, notebook, section group, or section) below which to search for content. This parameter sets the scope for the search.<br/><br/>*bstrSearchStringName* &ndash; The search string. Pass in any part of the metadata name. If you pass in an empty string or a null value, all objects that have metadata will match the query.<br/><br/>*pbstrHierarchyXmlOut* &ndash; (Output parameter) A pointer to a string into which you want OneNote to write the output XML string. The resulting XML string contains the notebook hierarchy from the root downward to, and including, any pages that match the search string. For example, the **FindPages** method does not list sections that have no page matches in the hierarchy. Also, if only one page in a single section matches the string, the returned hierarchy includes the path to that section and page, but to no other parts of the notebook hierarchy.<br/>*fIncludeUnindexedPages* &ndash; (Optional) **true** to search pages that have not been indexed by Windows Search; otherwise, **false**.<br/><br/>*xsSchema* &ndash; (Optional) The OneNote schema version of the string  *pbstrHierarchyXmlOut*. This optional value is used to specify the version of the OneNote XML schema that contains the _pbstrHierarchyXmlOut_ string. If this value is not specified, OneNote will assume that the XML is in schema version  *xsCurrent*. <br/><br/>**NOTE**:  We recommend specifying a version of OneNote (such as **xs2013**) instead of using **xsCurrent** or leaving it blank, because this will allow your add-in to work with future versions of OneNote.           |

**FindMeta** works only if you have Microsoft Windows Search 3.0 or 4.0 installed on your computer. Windows Vista and Windows 7 include this component. However, if you are running an earlier version of Windows, you must install [Windows Search](https://www.microsoft.com/windows/products/winfamily/desktopsearch/getitnow.mspx) for **FindMeta** to work.
  
## Functional methods

<a name="ON14DevRef_Application_Functional"> </a>

The methods described in this section enable you to perform certain actions or set parameters within the OneNote application.
  
### MergeFiles method

|||
|:-----|:-----|
|**Description** <br/> |Allows users to merge changes for the same file into one. For the files to be considered the same, they must have the same OneNote ID. |
|**Syntax** <br/> | `HRESULT MergeFiles (`<br/>`[in]BSTR bstrBaseFile,`<br/>`[in]BSTR bstrClientFile,`<br/>`[in]BSTR bstrServerFile,`<br/>`[in]BSTR bstrTargetFile);` <br/> |
|**Parameters** <br/> | *bstrBaseFile* &ndash; The path string to the .one file location of the initial state of the file.<br/>*bstrClientFile* &ndash; The path string to the .one file location of the second set of changes to be merged with the base file after the server file changes are merged with the base.<br/>*bstrServerFile* &ndash; The path string to the .one file location of the first set of changes to be merged with the base file.<br/>*bstrTargetFile* &ndash; The path string to the .one file location of the file with the merged changes. |

The **MergeFiles** method was intended for mobile scenarios in which multiple versions of an OneNote file may exist.
  
### MergeSections method

|||
|:-----|:-----|
|**Description** <br/> |Merges the content of one section into another in OneNote. |
|**Syntax** <br/> | `HRESULT MergeSections (`<br/>`[in]BSTR bstrSectionSourceId,`<br/>`[in]BSTR bstrSectionDestinationId);` <br/> |
|**Parameters** <br/> | *bstrSectionSourceId* &ndash; The OneNote ID of the section to be merged.<br/>*bstrSectionDestinationId* &ndash; The OneNote ID of the section to be merged into. The source section will be merged into this destination section. |

This method performs the same operation as the **Merge into Another Section** feature that is visible when you right-click a section.
  
### QuickFiling method

|||
|:-----|:-----|
|**Description** <br/> |Returns an instance of the [IQuickFilingDialog](quick-filing-dialog-box-interfaces-onenote.md#odc_IQuickFilingDialog) dialog box, which can be used to select a location within the OneNote hierarchy tree. |
|**Syntax** <br/> | `HRESULT QuickFiling (`<br/>`);` <br/> |

### SyncHierarchy method

|||
|:-----|:-----|
|**Description** <br/> |Forces OneNote to sync the specified object with the source file on disk. |
|**Syntax** <br/> | `HRESULT SyncHierarchy (`<br/>`[in]BSTR bstrHierarchyID);` <br/> |
|**Parameters** <br/> | *bstrHierarchyID* &ndash; The OneNote ID of the object to be synced. |

### SetFilingLocation method

|||
|:-----|:-----|
|**Description** <br/> |Allows users to specify where and how certain types of content should be filed in OneNote. |
|**Syntax** <br/> | `HRESULT SetFilingLocation (`<br/>`[in]FilingLocation flToSet,`<br/>`[in]FilingLocationType fltToSet,`<br/>`[in]BSTR bstrFilingSectionID);`           <br/> |
|**Parameters** <br/> | *flToSet* &ndash; The object type of the filing location to set.<br/>*fltToSet* &ndash; The location in which to file the type.<br/>*bstrFilingSectionID* &ndash; The OneNote ID of the section or page at which location you want to set. If not applicable, the user can pass in null or an empty string. |

The types of content that can be filed include Outlook items and Web Notes from Internet Explorer that are imported to OneNote through the **Send to OneNote** command in each application. The filing location of items that are printed into OneNote can also be set with this method.
  
## Properties

<a name="ON14DevRef_Application_Properties"> </a>

This section describes the properties of the **Application** interface.
  
|**Property**|**Description**|
|:-----|:-----|
|**Windows** <br/> |Gives users access to opened OneNote windows. This property allows users to enumerate through the set of OneNote windows and modify certain window properties. For more information, see [Windows Interfaces](window-interfaces-onenote.md). |
|**COMAddIns** <br/> |Returns the **COMAddIns** collection for OneNote. This collection contains all of the COM add-ins that are available to OneNote. The **Count** property of the **COMAddins** collection returns the number of available COM add-ins. For more information, see the [COMAddIns](https://msdn.microsoft.com/library/office/ff865489.aspx) object. |
|**LanguageSettings** <br/> |Enables you to access some APIs to change the common language settings of OneNote. |

## Events

<a name="ON14DevRef_Application_Events"> </a>

This section describes the events of the Application interface.
  
> [!CAUTION]
> Events cannot currently be added in managed code.
  
### OnNavigate event

|||
|:-----|:-----|
|**Description** <br/> |Allows a user to assign a function to be called when the OneNote UI is navigated away from the current OneNote location. |
|**Syntax** <br/> | `Event OnNavigate (`<br/>`);` <br/> |

### OnHierarchyChange method

|||
|:-----|:-----|
|**Description** <br/> |Allows a user to assign a function to be called any time the OneNote hierarchy changes (for example, adding or deleting pages, or moving sections). Hierarchy changes are batched, so if multiple changes occur at or near the same time, OneNote raises the event once. |
|**Syntax** <br/> | `Event OnHierarchyChange (`<br/>`BSTR bstrActivePageID);` <br/> |
|**Parameters** <br/> | *bstrActivePageID* &ndash; Passes the OneNote ID of the active page. |

## See also

- [OneNote developer reference](onenote-developer-reference.md)
