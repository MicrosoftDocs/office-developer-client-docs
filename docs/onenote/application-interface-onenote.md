---
title: "Application interface (OneNote)"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: overview
localization_priority: Normal
ms.assetid: 87926f7d-e1dc-41d5-8805-6ba91fc7b154
description: "The Application interface includes methods help retrieve, manipulate, and update OneNote information and content. The methods are in four general categories:"
---

# Application interface (OneNote)

The **Application** interface includes methods help retrieve, manipulate, and update OneNote information and content. The methods are in four general categories: 
  
- **Notebook structure** —Methods for working with notebook structure, including those for discovering, opening, modifying, closing, and deleting notebooks, section groups, and sections. 
    
- **Page content** —Methods for working with pages and page content, including those for discovering, modifying, saving, and deleting page content. Page content includes binary objects, such as ink and images, and text objects, such as outlines. 
    
- **Navigation** —Methods for finding, linking to, and navigating to pages and objects. 
    
- **Functional** —All other methods that perform certain actions or set parameters in OneNote. 
    
In addition, the **Application** interface includes a number of  *properties*  and  *events*  . 
  
## Notebook Structure Methods
<a name="ON14DevRef_Application_NotebookStructure"> </a>

The methods described in this section enable you to discover, open, modify, close, and delete OneNote notebooks, section groups, and sections.
  
### GetHierarchy Method

|||
|:-----|:-----|
|**Description** <br/> |Gets the notebook node hierarchy structure, starting from the node you specify (all notebooks or a single notebook, section group, or section), and extending downward to all descendants at the level you specify.  <br/> |
|**Syntax** <br/> | `HRESULT GetHierarchy(`           ` [in]BSTR bstrStartNodeID, `           ` [in]HierarchyScope hsScope, `           ` [out]BSTR * pbstrHierarchyXmlOut, `           ` [in,defaultvalue(xs2013)]XMLSchema xsSchema); ` <br/> |
|**Parameters** <br/> | _bstrStartNodeID_—The node (notebook, section group, or section) whose descendants you want. If you pass a null string (""), the method gets all nodes below the root node (that is, all notebooks, section groups, and sections). If you specify a notebook, section group, or section node, the method gets only descendants of that node.  <br/>  _hsScope_—The lowest descendant node level you want. For example, if you specify pages, the method gets all nodes as far down as the page level. If you specify sections, the method gets only section nodes below the notebook. For more information, see the **HierarchyScope** enumeration in the [Enumerations](enumerations-onenote-developer-reference.md#odc_HierarchyScope) topic.  <br/>  _pbstrHierarchyXmlOut_—(Output parameter) A pointer to the string in which you want OneNote to write the XML output.  <br/>  _xsSchema_—(Optional) The version of the OneNote XML schema, of type **XMLSchema**, that you want to be output. You can specify whether you want XML Schema version 2013, 2010, 2007, or the current version.  <br/> > [!NOTE]>  We recommend specifying a version of OneNote (such as **xs2013** ) instead of using **xsCurrent** or leaving it blank, because this will allow your add-in to work with future versions of OneNote.           |
   
The GetHierarchy method returns a string in OneNote 2013 XML format by default or you can set the preferred XML schema version by using the optional  _xsSchema_ parameter. 
  
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

### UpdateHierarchy Method

|||
|:-----|:-----|
|**Description**|Modifies or updates the hierarchy of notebooks. For example, you can add sections or section groups to a notebook, add a new notebook, move sections within a notebook, change the name of a section, add pages to a section, or change the order of pages within sections.|
|**Syntax**| `HRESULT UpdateHierarchy(`           ` [in]BSTR bstrChangesXmlIn, `           ` [in,defaultvalue(xsCurrent)] XMLSchema xsSchema); `|
|**Parameters**| _bstrChangesXmlIn_—A string that contains OneNote XML code that specifies the hierarchy changes to make. For example, if you want to insert a new section, you can add a **Section** element in the XML string to indicate where you want the new section to be added. Alternatively, if you want to change the name of an existing section, you can keep the same section ID and change its **name** attribute in the XML code.  _xsSchema_—(Optional) The OneNote schema version of the string  _bstrChangesXmln_. This optional value is used to specify the version of the OneNote XML schema that the  _bstrChangesXmlIn_ string is in. If this value is not specified, OneNote will assume that the XML is in schema version  _xsCurrent_. > [!NOTE]>  We recommend specifying a version of OneNote (such as **xs2013** ) instead of using **xsCurrent** or leaving it blank, because this will allow your add-in to work with future versions of OneNote.           |
   
If you pass only a partial OneNote XML string for the  _bstrChangesXmlIn_ parameter, OneNote attempts to infer the changes you want. For example, if you include a **Notebook** element that contains only one section, OneNote adds the section after any existing sections. However, if the operation you specify is ambiguous, the result can be hard to determine. For example, if an existing notebook contains four sections, and the XML string you pass includes the notebook and only the fourth and first sections (in that order), OneNote might place the second and third sections before the fourth section or after the first section. 
  
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

The following C# example shows a complete console application that searches for a section named " `Sample_Section`", prompts the user to input a new name for the section, and then uses the **UpdateHierarchy** method to change the section name to the name that the user typed. Before running the code, change "  `Sample_Section`" to the name of a section that exists in your OneNote hierarchy.
  
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

### OpenHierarchy Method

|||
|:-----|:-----|
|**Description** <br/> |Opens a section group or section that you specify.  <br/> |
|**Syntax** <br/> | `HRESULT OpenHierarchy(`           ` [in]BSTR bstrPath, `           ` [in]BSTR bstrRelativeToObjectID, `           ` [out]BSTR * pbstrObjectID, `           ` [in,defaultvalue(cftNone)]CreateFileType cftIfNotExist); ` <br/> |
|**Parameters** <br/> | _bstrPath_—The path that you want to open. For a notebook, or for a section group in a notebook,  _bstrPath_ can be a folder path or the path to an .one section file. If you specify the path to an .one section file, you must include the .one extension on the file-path string.  <br/>  _bstrRelativeToObjectID_—The OneNote ID of the parent object (notebook or section group) under which you want the new object to open. If the  _bstrPath_ parameter is an absolute path, you can pass an empty string ("") for  _bstrRelativeToObjectID_. Alternatively, you can pass the object ID of the notebook or section group that should contain the object (section or section group) that you want to create, and then specify the file name (for example, section1.one) of the object that you want to create under that parent object.  <br/>  _pbstrObjectID_—(Output parameter) The object ID that OneNote returns for the notebook, section group, or section that the **OpenHierarchy** method opens. This parameter is a pointer to the string into which you want the method to write the ID.  <br/>  _cftlfNotExist_—(Optional) An enumerated value from the [CreateFileType](enumerations-onenote-developer-reference.md#odc_CreateFileType) enumeration. If you pass a value for  _cftIfNotExist_, the **OpenHierarchy** method creates the section group or section file at the specified path only if the file does not already exist.  <br/> |
   
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

### DeleteHierarchy Method

|||
|:-----|:-----|
|**Description** <br/> |Deletes any hierarchy object (a section group, section, or page) from the OneNote notebook hierarchy.  <br/> |
|**Syntax** <br/> | `HRESULT DeleteHierarchy(`           ` [in]BSTR bstrObjectID, `           ` [in,defaultvalue(0)]DATE dateExpectedLastModified, `           ` [in,defaultvalue(false)]VARIANT_BOOL deletePermanently); ` <br/> |
|**Parameters** <br/> | _bstrObjectID_—The OneNote ID of the object you want to delete. The object can be a section group, section, or page.  <br/>  _dateExpectedLastModified_—(Optional) The date and time that you think the object you want to delete was last modified. If you pass a non-zero value for this parameter, OneNote proceeds with the update only if the value you pass matches the actual date and time the object was last modified. Passing a value for this parameter helps prevent accidentally overwriting edits users made since the last time the object was modified.  <br/>  _deletePermanently_—(Optional) **true** to permanently delete the content; **false** to move the content into the OneNote recycle bin for the corresponding Notebook (the default). If the Notebook is in OneNote 2007 format, no recycle bin exists, so the content is permanently deleted.  <br/> |
   
### CreateNewPage Method

|||
|:-----|:-----|
|**Description** <br/> |Adds a new page to the section you specify. The new page is added as the last page of the section  <br/> |
|**Syntax** <br/> | `HRESULT CreateNewPage(`           ` [in]BSTR bstrSectionID, `           ` [out]BSTR * pbstrPageID); `           ` [in,defaultvalue(npsDefault)]NewPageStyle npsNewPageStyle); ` <br/> |
|**Parameters** <br/> | _bstrSectionID_—A string that contains the OneNote ID of the section in which you want to create the new page.  <br/>  _pbstrPageID_—(Output parameter) A pointer to the string into which the method writes the OneNote ID for the newly created page.  <br/>  _npsNewPageStyle_—A value from the **NewPageStyle** enumeration that specifies the style of the page to be created.  <br/> |
   
The OneNote API includes the **CreateNewPage** method as a convenience. You can achieve the same result, with greater control over how the new page is positioned in the hierarchy, by calling the **UpdateHierarchy** method. The **UpdateHierarchy** method also lets you create subpages at the same time as you create a new page. 
  
### CloseNotebook Method

|||
|:-----|:-----|
|**Description** <br/> |Closes the specified notebook.  <br/> |
|**Syntax** <br/> | `HRESULT CloseNotebook(`           ` [in]BSTR bstrNotebookID, `           ` [in,defaultvalue(false)]VARIANT_BOOL force); ` <br/> |
|**Parameters** <br/> | _bstrNotebookID_—The OneNote ID of the notebook you want to close.  <br/>  _force_—(Optional) **true** to close the notebook, even if there are changes in the notebook that OneNote cannot sync before closing; otherwise, **false** (the default).  <br/> |
   
You can use the **CloseNotebook** method to close the notebook you specify. When you call this method, OneNote synchronizes any offline files with current notebook content, if necessary, and then closes the specified notebook. After the method returns, the notebook no longer appears in the list of open notebooks in the OneNote user interface (UI). 
  
### GetHierarchyParent Method

|||
|:-----|:-----|
|**Description** <br/> |Gets the OneNote ID for the parent object of a OneNote object.  <br/> |
|**Syntax** <br/> | `HRESULT GetHierarchyParent (`           ` [in]BSTR bstrObjectID, `           ` [out]BSTR * pbstrParentID); ` <br/> |
|**Parameters** <br/> | _bstrObjectID_—A string that contains the OneNote ID of the object of which you want to find the parent object.  <br/>  _pbstrParentID_—(Output parameter) A pointer to the string into which the method writes the OneNote ID of the parent object.  <br/> |
   
If the OneNote object has no parent object (for example, when a user wants to get the parent of a Notebook), an exception is thrown.
  
### GetSpecialLocation Method

|||
|:-----|:-----|
|**Description** <br/> |Finds the path to the location where OneNote stores certain special items, such as backups, unfiled notes, and the default notebook.  <br/> |
|**Syntax** <br/> | `HRESULT GetSpecialLocation(`           ` [in]SpecialLocation slToGet, `           ` [out]BSTR * pbstrSpecialLocationPath); ` <br/> |
|**Parameters** <br/> | _slToGet_—One of the [SpecialLocation](enumerations-onenote-developer-reference.md#odc_SpecialLocation) enumeration values that specifies the special folder location to get.  <br/>  _pbstrSpecialLocationPath_—(Output parameter) A pointer to the string into which you want OneNote to write the path of the special folder.  <br/> |
   
You can use this method to determine the location on disk of the Unfiled Notes folder. That is the folder in which OneNote stores notes that are created when you drag an item into OneNote, as well as notes that come directly from other applications (such as those that result when you click **Send to OneNote** in Microsoft Outlook or Microsoft Internet Explorer). 
  
## Page Content Methods
<a name="ON14DevRef_Application_PageContent"> </a>

The methods described in this section enable you to discover, update, and delete the content on pages in OneNote notebooks, as well as to publish OneNote content.
  
### GetPageContent Method

|||
|:-----|:-----|
|**Description**|Gets all of the content (in OneNote XML format) of the specified page.|
|**Syntax**| `HRESULT GetPageContent(`           ` [in]BSTR bstrPageID, `           ` [out]BSTR * pbstrPageXmlOut, `           ` [in,defaultvalue(piBasic)]PageInfo pageInfoToExport, `           ` [in,defaultvalue(xsCurrent)]XMLSchema xsSchema); `|
|**Parameters**| _bstrPageId_—The OneNote ID of the page whose content you want to get.  _pbstrPageXmlOut_—(Output parameter) A pointer to the string into which you want OneNote to write the XML output.  _pageInfoToExport_—(Optional) Specifies whether the **GetPageContent** method returns binary content, embedded in the XML code and base-64 encoded. Binary content can include, for example, images and ink data. The  _pageInfoToExport_ parameter also specifies whether to mark up the selection in the XML code that the **GetPageContent** method returns. It takes an enumerated value from the [PageInfo](enumerations-onenote-developer-reference.md#odc_PageInfo) enumeration.  _xsSchema_—(Optional) The version of the OneNote XML schema, of type **XMLSchema**, that you want to be output. You can specify whether you want XML Schema version 2013, 2010, 2007, or the current version. > [!NOTE]>  We recommend specifying a version of OneNote (such as **xs2013** ) instead of using **xsCurrent** or leaving it blank, because this will allow your add-in to work with future versions of OneNote.           |
   
By default, to avoid excess length in the XML string it returns, OneNote does not embed binary content in the XML code. For the same reason, it does not mark up the current selection with selection attributes. Binary objects include a OneNote ID in their tags. To get a binary object, you call the **GetBinaryPageContent** method and pass it the OneNote ID you get from the **GetPageContent** method. You use the **GetPageContent** method when you do not need the binary data immediately. 
  
### UpdatePageContent Method

|||
|:-----|:-----|
|**Description**|Updates or modifies the content on the page.|
|**Syntax**| `HRESULT UpdatePageContent(`           ` [in]BSTR bstrPageChangesXmlIn, `           ` [in,defaultvalue(0)]DATE dateExpectedLastModified, `           ` [in,defaultvalue(xsCurrent)]XMLSchema xsSchema, `           ` [in,defaultvalue(false)]VARIANT_BOOL force); `|
|**Parameters**| _bstrPageChangesXmlIn_—A string that contains OneNote XML code that includes the changes you want to make to the page.  _dateExpectedLastModified_—(Optional) The date and time that you think the page you want to update was last modified. If you pass a non-zero value for this parameter, OneNote proceeds with the update only if the value you pass matches the actual date and time the page was last modified. Passing a value for this parameter helps prevent accidentally overwriting edits users made since the last time the page was modified.  _xsSchema_—(Optional) The version of the OneNote XML schema, of type **XMLSchema**, that you want to be output. You can specify whether you want XML schema version 2013, 2010, 2007, or the current version. > [!NOTE]>  We recommend specifying a version of OneNote (such as **xs2013** ) instead of using **xsCurrent** or leaving it blank, because this will allow your add-in to work with future versions of OneNote.            _force_(Optional) **true** to update the page content, even if there is unknown data on the page from a future version of OneNote; otherwise, **false** (the default). |
   
You can use this method to modify the page in various ways. For example, you can use the **UpdatePageContent** method to add an outline to a page, change the content of an outline, add images, add ink, move content, or modify text in outlines. 
  
As a more specific example, you might use the **GetPageContent** method to export an existing page, make some changes to the XML code for the page, and then use the **UpdatePageContent** method to import the entire page again. Or, you might use this method to add new page objects, such as images, to the bottom of an existing page. 
  
The only objects that you must include in the XML code that you pass to the **UpdatePageContent** method are page-level objects (such as outlines, images on the page, or ink on the page) that have changed. This method does not modify or remove page-level objects that you do not specify in the  _bstrPageChangesXmlIn_ parameter. The method entirely replaces page-level objects, such as outlines, whose IDs match those of the objects you pass. Consequently, you must fully specify all page-level objects in your code, including their existing content and changes you want to make to them. 
  
For example, if your page contains an outline and a background page image, you can replace the outline and leave the image unchanged by completely specifying the outline in the XML code, using the ID of the existing outline, and not including the image in the code. Because the revised outline you include in the code completely replaces the existing outline, you must include the entire contents of the outline.
  
Also, the **UpdatePageContent** method modifies only element properties that you specify in the  _bstrPageChangesXmlIn_ parameter. For example, if you specify some, but not all, properties of the **PageSettings** element, the properties that you do not specify remain unchanged. 
  
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

### GetBinaryPageContent Method

|||
|:-----|:-----|
|**Description** <br/> |Returns a binary object, such as ink or images, on an OneNote page as a base-64-encoded string.  <br/> |
|**Syntax** <br/> | `HRESULT GetBinaryPageContent(`           ` [in]BSTR bstrPageID, `           ` [in]BSTR bstrCallbackID, `           ` [out]BSTR * pbstrBinaryObjectB64Out); ` <br/> |
|**Parameters** <br/> | _bstrPageID_—The OneNote ID of the page that contains the binary object to get.  <br/>  _bstrCallBackID_—The OneNote ID of the binary object you want to get. This ID, known as a **callbackID**, is in the OneNote XML code for a page returned by the **GetPageContent** method.  <br/>  _pbstrBinaryObectB64Out_—(Output parameter) A pointer to a string into which OneNote writes the binary object as a base-64-encoded string.  <br/> |
   
### DeletePageContent Method

|||
|:-----|:-----|
|**Description** <br/> |Deletes an object—such as an **Outline**, **Ink**, or **Image** object—from a page.  <br/> |
|**Syntax** <br/> | `HRESULT DeletePageContent(`           ` [in]BSTR bstrPageID, `           ` [in]BSTR bstrObjectID, `           ` [in,defaultvalue(0)]DATE dateExpectedLastModified, `           ` [in,defaultvalue(#)]VARIANT_BOOL force); ` <br/> |
|**Parameters** <br/> | _bstrPageID_—The OneNote ID of the page that contains the object to delete.  <br/>  _bstrObjectID_—The OneNote ID of the object that you want to delete.  <br/>  _dateExpectedLastModified_—(Optional) The date and time that you think the page that contains content you want to delete was last modified. If you pass a non-zero value for this parameter, OneNote proceeds with the deletion only if the value you pass matches the actual date and time the page was last modified. Passing a value for this parameter helps prevent accidentally overwriting edits made by users since the last time the page was modified.  <br/>  _force_(Optional) **true** to update the page content, even if there is unknown data on the page from a future version of OneNote; otherwise, **false** (the default).  <br/> |
   
### Publish Method

|||
|:-----|:-----|
|**Description** <br/> |Exports the page you specify to a file in any format that OneNote supports.  <br/> |
|**Syntax** <br/> | `HRESULT Publish(`           ` [in]BSTR bstrHierarchyID, `           ` [in]BSTR bstrTargetFilePath, `           ` [in,defaultvalue(pfOneNote)]PublishFormat pfPublishFormat, `           ` [in,defaultvalue(0)]BSTR bstrCLSIDofExporter); ` <br/> |
|**Parameters** <br/> | _bstrHierarchyID_—The OneNote ID of the hierarchy you want to export.  <br/>  _bstrTargetFilePath_—The absolute path to the location where you want to save the resulting output file. The file you specify must be one that does not already exist at that location.  <br/>  _pfPublishFormat_—One of the [PublishFormat](enumerations-onenote-developer-reference.md#odc_PublishFormat) enumeration values that specifies the format in which you want the published page to be (for example, MTHML, PDF, and so on).  <br/>  _bstrCLSIDofExporter_—The class ID (CLSID) of a registered COM application that can export Microsoft Windows enhanced metafiles (.emf). The COM application must implement the **IMsoDocExporter** interface. This parameter is included to permit third-party developers to write their own code to publish OneNote content in a custom format. For more information about the **IMsoDocExporter** interface, see [Extending the Office 2007 Fixed-Format Export Feature](http://msdn.microsoft.com/en-us/library/office/aa338206%28v=office.12%29.aspx).  <br/> |
   
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
  
## Navigation Methods
<a name="ON14DevRef_Application_Navigation"> </a>

The methods described in this section enable you to find, navigate to, and link to OneNote notebooks, section groups, sections, pages, and page objects.
  
### NavigateTo Method

|||
|:-----|:-----|
|**Description** <br/> |Navigates to the specified object (for example, sections, pages, and **Outline** elements within pages).  <br/> |
|**Syntax** <br/> | `HRESULT NavigateTo(`           ` [in]BSTR bstrHierarchyObjectID, `           ` [in,defaultvalue(#)]BSTR bstrObjectID, `           ` [in,defaultvalue(0)]VARIANT_BOOL fNewWindow); ` <br/> |
|**Parameters** <br/> | _bstrHierarchyObjectID_—The OneNote ID of the object you want to navigate to in the OneNote Hierarchy.  <br/>  _bstrObjectID_—The OneNote ID of the object you want to navigate to on the OneNote page.  <br/>  _fNewWindow_—(Optional) **true** to open specified object in a new OneNote window. **false** does not open a new OneNote window if one is open.  <br/> |
   
### NavigateToUrl Method

|||
|:-----|:-----|
|**Description** <br/> |If passed a OneNote link (onenote://), opens the OneNote window to the corresponding location in OneNote. If the link is external to OneNote (such as http:// or file://), a security dialog box will appear. Upon dismissal, OneNote attempts to open the link and an **HResult.hrObjectDoesNotExist** error is returned.  <br/> |
|**Syntax** <br/> | `HRESULT NavigateTo(`           ` [in]BSTR bstrUrl, `           ` [in,defaultvalue(0)]VARIANT_BOOL fNewWindow); ` <br/> |
|**Parameters** <br/> | _bstrUrl_—A string that indicates where to navigate to. This could be a OneNote link, or any other URL, such as a web link or network location.  <br/>  _fNewWindow_—(Optional) **true** to open the specified URL in a new OneNote window. **false** does not open a new OneNote window if one is open.  <br/> |
   
### GetHyperLinkToObject Method

|||
|:-----|:-----|
|**Description** <br/> |Gets a OneNote hyperlink to the specified notebook, section group, section, page, or page object.  <br/> |
|**Syntax** <br/> | `HRESULT GetHyperlinkToObject(`           ` [in] BSTR bstrHierarchyID, `           ` [in] BSTR bstrPageContentObjectID, `           ` [out] BSTR * pbstrHyperlinkOut); ` <br/> |
|**Parameters** <br/> | _bstrHierarchyID_—The OneNote ID for the notebook, section group, section, or page for which you want a hyperlink.  <br/>  _bstrPageContentObjectID_—(Optional) The OneNote ID for the object within the page for which you want a hyperlink. For example, the object can be an outline or **Outline** element. If you pass an empty string (""), the returned link points to the notebook, section group, section, or page that you specified in the  _bstrHierarchyID_ parameter. If you pass a non-empty string for the  _bstrPageContentObjectID_ parameter, the  _bstrHierarchyID_ parameter must be a reference to the page that contains the specified object.  <br/>  _pbstrHyperlinkOut_—(Output parameter) A pointer to a string into which the **GetHyperlinkToObject** method writes the output hyperlink text.  <br/> |
   
When you attempt to navigate to the resulting link, OneNote opens and displays the specified object in the browser.
  
### GetWebHyperlinktoObject

|||
|:-----|:-----|
|**Description** <br/> |Returns a hyperlink to an object that opens in the OneNote Web Client.  <br/> |
|**Syntax** <br/> | `HRESULT GetWebHyperlinkToObject (`           `[in] BSTR bstrHierarchyID,`           `[in] BSTR bstrPageContentObjectID,`           `[out] BSTR * pbstrHyperlinkOut);` <br/> |
|**Parameters** <br/> | _bstrHierarchyID_ - The OneNote ID for the notebook, section group, section or page for which you want a web hyperlink.  <br/>  _bstrPageContentObjectID_ - (Optional) The OneNote ID for the object within the page for which you want a hyperlink. For example, the object can be an outline or **Outline** element. If you pass an empty string (""), the returned link points to the notebook, section group, section, or page that you specified in the  _bstrHierarchyID_ parameter. If you pass a non-empty string for the  _bstrPageContentObjectID_ parameter, the  _bstrHierarchyID_ parameter must be a reference to the page that contains the specified object.  <br/>  _pbstrHyperlinkOut_ - (Output parameter) A pointer to a string into which the **GetWebHyperlinkToObject** method writes the output hyperlink text. If a web hyperlink cannot be created for the notebook, a null value is returned.  <br/> |
   
### FindPages Method

|||
|:-----|:-----|
|**Description**|Returns a list of pages that match the specified query term.|
|**Syntax**| `HRESULT FindPages(`           ` [in]BSTR bstrStartNodeID, `           ` [in]BSTR bstrSearchBSTR, `           ` [out]BSTR * pbstrHierarchyXmlOut, `           ` [in,defaultvalue(#)]VARIANT_BOOL fIncludeUnindexedPages, `           ` [in,defaultvalue(0)]VARIANT_BOOL fDisplay, `           ` [in,defaultvalue(#)]XMLSchema xsSchema); `|
|**Parameters**| _bstrStartNodeID_—The node (root, notebook, section group, or section) below which to search for content. This parameter sets the scope for the search.  _bstrSearchString_—The search string. Pass exactly the same string that you would type into the search box in the OneNote UI. You can use bitwise operators, such as **AND** and **OR**, which must be all uppercase.  _pbstrHierarchyXmlOut_—(Output parameter) A pointer to a string into which you want OneNote to write the output XML string. The resulting XML string contains the notebook hierarchy from the root downward to, and including, any pages that match the search string. For example, the **FindPages** method does not list sections that have no page matches in the hierarchy. Also, if only one page in a single section matches the string, the returned hierarchy includes the path to that section and page, but to no other parts of the notebook hierarchy.  _fIncludeUnindexedPages_—(Optional) **true** to search pages that have not been indexed by Windows Search; otherwise, **false**.  _fDisplay_—(Optional) **true** to also run the search in the UI for the user, just as if the user had typed it themselves. **false** to perform the query with no change to the UI (the default).  _xsSchema_—(Optional) The OneNote schema version of the string  _pbstrHierarchyXmlOut_. This optional value is used to specify the version of the OneNote XML schema that contains the  _pbstrHierarchyXmlOut_ string. If this value is not specified, OneNote will assume that the XML is in schema version  _xsCurrent_. > [!NOTE]>  We recommend specifying a version of OneNote (such as **xs2013** ) instead of using **xsCurrent** or leaving it blank, because this will allow your add-in to work with future versions of OneNote.           |
   
 **FindPages** works only if you have Microsoft Search 3.0 or 4.0 installed on your computer. Windows Vista and Windows 7 include this component. However, if you are running an earlier version of Windows, you must install [Windows Search](http://www.microsoft.com/windows/products/winfamily/desktopsearch/getitnow.mspx) for **FindPages** to work. 
  
### FindMeta Method

|||
|:-----|:-----|
|**Description**|Returns a list of OneNote objects that contain metadata that matches the specified query term.|
|**Syntax**| `HRESULT FindMeta (`           ` [in]BSTR bstrStartNodeID, `           ` [in]BSTR bstrSearchBSTRName, `           ` [out]BSTR * pbstrHierarchyXmlOut, `           ` [in,defaultvalue(#)]VARIANT_BOOL fIncludeUnindexedPages, `           ` [in,defaultvalue(#)]XMLSchema xsSchema); `|
|**Parameters**| _bstrStartNodeID_—The node (root, notebook, section group, or section) below which to search for content. This parameter sets the scope for the search.  _bstrSearchStringName_—The search string. Pass in any part of the metadata name. If you pass in an empty string or a null value, all objects that have metadata will match the query.  _pbstrHierarchyXmlOut_—(Output parameter) A pointer to a string into which you want OneNote to write the output XML string. The resulting XML string contains the notebook hierarchy from the root downward to, and including, any pages that match the search string. For example, the **FindPages** method does not list sections that have no page matches in the hierarchy. Also, if only one page in a single section matches the string, the returned hierarchy includes the path to that section and page, but to no other parts of the notebook hierarchy.  _fIncludeUnindexedPages_—(Optional) **true** to search pages that have not been indexed by Windows Search; otherwise, **false**.  _xsSchema_—(Optional) The OneNote schema version of the string  _pbstrHierarchyXmlOut_. This optional value is used to specify the version of the OneNote XML schema that contains the  _pbstrHierarchyXmlOut_ string. If this value is not specified, OneNote will assume that the XML is in schema version  _xsCurrent_. > [!NOTE]>  We recommend specifying a version of OneNote (such as **xs2013** ) instead of using **xsCurrent** or leaving it blank, because this will allow your add-in to work with future versions of OneNote.           |
   
 **FindMeta** works only if you have Microsoft Windows Search 3.0 or 4.0 installed on your computer. Windows Vista and Windows 7 include this component. However, if you are running an earlier version of Windows, you must install [Windows Search](http://www.microsoft.com/windows/products/winfamily/desktopsearch/getitnow.mspx) for **FindMeta** to work. 
  
## Functional Methods
<a name="ON14DevRef_Application_Functional"> </a>

The methods described in this section enable you to perform certain actions or set parameters within the OneNote application.
  
### MergeFiles Method

|||
|:-----|:-----|
|**Description** <br/> |Allows users to merge changes for the same file into one. For the files to be considered the same, they must have the same OneNote ID.  <br/> |
|**Syntax** <br/> | `HRESULT MergeFiles (`           ` [in]BSTR bstrBaseFile, `           ` [in]BSTR bstrClientFile, `           ` [in]BSTR bstrServerFile, `           ` [in]BSTR bstrTargetFile); ` <br/> |
|**Parameters** <br/> | _bstrBaseFile_—The path string to the .one file location of the initial state of the file.  <br/>  _bstrClientFile_—The path string to the .one file location of the second set of changes to be merged with the base file after the server file changes are merged with the base.  <br/>  _bstrServerFile_—The path string to the .one file location of the first set of changes to be merged with the base file.  <br/>  _bstrTargetFile_—The path string to the .one file location of the file with the merged changes.  <br/> |
   
The **MergeFiles** method was intended for mobile scenarios in which multiple versions of an OneNote file may exist. 
  
### MergeSections Method

|||
|:-----|:-----|
|**Description** <br/> |Merges the content of one section into another in OneNote.  <br/> |
|**Syntax** <br/> | `HRESULT MergeSections (`           ` [in]BSTR bstrSectionSourceId, `           ` [in]BSTR bstrSectionDestinationId); ` <br/> |
|**Parameters** <br/> | _bstrSectionSourceId_—The OneNote ID of the section to be merged.  <br/>  _bstrSectionDestinationId_—The OneNote ID of the section to be merged into. The source section will be merged into this destination section.  <br/> |
   
This method performs the same operation as the **Merge into Another Section** feature that is visible when you right-click a section. 
  
### QuickFiling Method

|||
|:-----|:-----|
|**Description** <br/> |Returns an instance of the [IQuickFilingDialog](quick-filing-dialog-box-interfaces-onenote.md#odc_IQuickFilingDialog) dialog box, which can be used to select a location within the OneNote hierarchy tree.  <br/> |
|**Syntax** <br/> | `HRESULT QuickFiling (`           ` ); ` <br/> |
   
### SyncHierarchy Method

|||
|:-----|:-----|
|**Description** <br/> |Forces OneNote to sync the specified object with the source file on disk.  <br/> |
|**Syntax** <br/> | `HRESULT SyncHierarchy (`           ` [in]BSTR bstrHierarchyID); ` <br/> |
|**Parameters** <br/> | _bstrHierarchyID_—The OneNote ID of the object to be synced.  <br/> |
   
### SetFilingLocation Method

|||
|:-----|:-----|
|**Description** <br/> |Allows users to specify where and how certain types of content should be filed in OneNote.  <br/> |
|**Syntax** <br/> | `HRESULT SetFilingLocation (`           ` [in]FilingLocation flToSet, `           ` [in]FilingLocationType fltToSet, `           ` [in]BSTR bstrFilingSectionID); `           <br/> |
|**Parameters** <br/> | _flToSet_—The object type of the filing location to set.  <br/>  _fltToSet_—The location in which to file the type.  <br/>  _bstrFilingSectionID_—The OneNote ID of the section or page at which location you want to set. If not applicable, the user can pass in null or an empty string.  <br/> |
   
The types of content that can be filed include Outlook items and Web Notes from Internet Explorer that are imported to OneNote through the **Send to OneNote** command in each application. The filing location of items that are printed into OneNote can also be set with this method. 
  
## Properties
<a name="ON14DevRef_Application_Properties"> </a>

This section describes the properties of the **Application** interface. 
  
|**Property**|**Description**|
|:-----|:-----|
|**Windows** <br/> |Gives users access to opened OneNote windows. This property allows users to enumerate through the set of OneNote windows and modify certain window properties. For more information, see [Windows Interfaces](window-interfaces-onenote.md).  <br/> |
|**COMAddIns** <br/> |Returns the **COMAddIns** collection for OneNote. This collection contains all of the COM add-ins that are available to OneNote. The **Count** property of the **COMAddins** collection returns the number of available COM add-ins. For more information, see the [COMAddIns](http://msdn.microsoft.com/en-us/library/office/ff865489.aspx) object.  <br/> |
|**LanguageSettings** <br/> |Enables you to access some APIs to change the common language settings of OneNote.  <br/> |
   
## Events
<a name="ON14DevRef_Application_Events"> </a>

This section describes the events of the Application interface.
  
> [!CAUTION]
> Events cannot currently be added in managed code. 
  
### OnNavigate Event

|||
|:-----|:-----|
|**Description** <br/> |Allows a user to assign a function to be called when the OneNote UI is navigated away from the current OneNote location.  <br/> |
|**Syntax** <br/> | `Event OnNavigate (`           ` ); ` <br/> |
   
### OnHierarchyChange Method

|||
|:-----|:-----|
|**Description** <br/> |Allows a user to assign a function to be called any time the OneNote hierarchy changes (for example, adding or deleting pages, or moving sections). Hierarchy changes are batched, so if multiple changes occur at or near the same time, OneNote raises the event once.  <br/> |
|**Syntax** <br/> | `Event OnHierarchyChange (`           ` BSTR bstrActivePageID); ` <br/> |
|**Parameters** <br/> | _bstrActivePageID_—Passes the OneNote ID of the active page.  <br/> |
   
## See also

- [OneNote developer reference](onenote-developer-reference.md)

