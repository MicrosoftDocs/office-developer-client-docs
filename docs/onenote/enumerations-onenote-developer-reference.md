---
title: "Enumerations (OneNote developer reference)"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: overview
localization_priority: Normal
ms.assetid: 62912d6e-c39e-4f8b-8cdb-ae9b6376cbc0
description: "This topic describes the enumerations in the OneNote 2013 object model."
---

# Enumerations (OneNote developer reference)

This topic describes the enumerations in the OneNote 2013 object model.
  
## CreateFileType
<a name="odc_CreateFileType"> </a>

When passed to the **OpenHierarchy** method, specifies the type of object to create, if any, if the path passed to the method does not yet exist. 
  
|**Member**|**Value**|**Description**|
|:-----|:-----|:-----|
|**cftNone** <br/> |0  <br/> |Creates no new object.  <br/> |
|**cftNotebook** <br/> |1  <br/> |Creates a notebook by using the specified name and location.  <br/> |
|**cftFolder** <br/> |2  <br/> |Creates a section group by using the specified name and location.  <br/> |
|**cftSection** <br/> |3  <br/> |Creates a section by using the specified name and location.  <br/> |
   
## DockLocation
<a name="odc_CreateFileType"> </a>

Indicates the docked location of a OneNote 2013 window by using the [Window](window-interfaces-onenote.md) interface. When set to the **DockedLocation** property, specifies the location at which to dock a OneNote window. This enumeration is new in OneNote 2013. 
  
|**Member**|**Value**|**Description**|
|:-----|:-----|:-----|
|**dlDefault** <br/> |-1  <br/> |The OneNote window is docked at the default location on the desktop.  <br/> |
|**dlLeft** <br/> |1  <br/> |The OneNote window is docked on the left side of the desktop.  <br/> |
|**dlRight** <br/> |2  <br/> |The OneNote window is docked on the right side of the desktop.  <br/> |
|**dlTop** <br/> |3  <br/> |The OneNote window is docked at the top of the desktop.  <br/> |
|**dlBottom** <br/> |4  <br/> |The OneNote window is docked at the bottom of the desktop.  <br/> |
   
## FilingLocation
<a name="odc_CreateFileType"> </a>

When passed to the **SetFilingLocation** method, specifies what type of content the filing location is set for when the content type is sent to OneNote. This enumeration is new in OneNote 2013. 
  
|**Member**|**Value**|**Description**|
|:-----|:-----|:-----|
|**flEMail** <br/> |0  <br/> |Sets where Outlook email messages will be filed.  <br/> |
|**flContacts** <br/> |1  <br/> |Sets where Outlook contacts will be filed.  <br/> |
|**flTasks** <br/> |2  <br/> |Sets where Outlook tasks will be filed.  <br/> |
|**flMeetings** <br/> |3  <br/> |Sets where Outlook meetings will be filed.  <br/> |
|**flWebContent** <br/> |4  <br/> |Sets where Internet Explorer contents will be filed.  <br/> |
|**flPrintOuts** <br/> |5  <br/> |Sets where printouts from the OneNote printer will be filed.  <br/> |
   
## FilingLocationType
<a name="odc_CreateFileType"> </a>

When passed to the **SetFilingLocation** method, specifies where content that is sent to OneNote is filed. This enumeration is new in OneNote 2013. 
  
|**Member**|**Value**|**Description**|
|:-----|:-----|:-----|
|**fltNamedSectionNewPage** <br/> |0  <br/> |Sets content to be filed on a new page in a specified section.  <br/> |
|**fltCurrentSectionNewPage** <br/> |1  <br/> |Sets content to be filed on a new page in the current section.  <br/> |
|**fltCurrentPage** <br/> |2  <br/> |Sets content to be filed on the current page.  <br/> |
|**fltNamedPage** <br/> |4  <br/> |Sets content to be filed on a specified page.  <br/> |
   
## HierarchyElement
<a name="odc_CreateFileType"> </a>

When assigned to the **TreeDepth** property of the [IQuickFilingDialog](quick-filing-dialog-box-interfaces-onenote.md) interface, specifies the depth of the OneNote tree to display when the quick filing dialog is rendered. When passed to the **AddButton** method of the **IQuickFilingDialog** object, references certain elements in the OneNote hierarchy. This enumeration is new in OneNote 2013. 
  
|**Member**|**Value**|**Description**|
|:-----|:-----|:-----|
|**heNone** <br/> |0  <br/> |Refers to no element.  <br/> |
|**heNotebooks** <br/> |1  <br/> |Refers to the Notebook elements.  <br/> |
|**heSectionGroups** <br/> |2  <br/> |Refers to the Section Group elements.  <br/> |
|**heSections** <br/> |4  <br/> |Refers to the Section elements.  <br/> |
|**hePages** <br/> |8  <br/> |Refers to the Page elements.  <br/> |
   
## HierarchyScope
<a name="odc_HierarchyScope"> </a>

When passed to the **GetHierarchy** method, specifies the lowest level to get in the notebook node hierarchy. 
  
|**Member**|**Value**|**Description**|
|:-----|:-----|:-----|
|**hsSelf** <br/> |0  <br/> |Gets just the start node specified and no descendants.  <br/> |
|**hsChildren** <br/> |1  <br/> |Gets the immediate child nodes of the start node, and no descendants in higher or lower subsection groups.  <br/> |
|**hsNotebooks** <br/> |2  <br/> |Gets all notebooks below the start node, or root.  <br/> |
|**hsSections** <br/> |3  <br/> |Gets all sections below the start node, including sections in section groups and subsection groups.  <br/> |
|**hsPages** <br/> |4  <br/> |Gets all pages below the start node, including all pages in section groups and subsection groups.  <br/> |
   
## NewPageStyle
<a name="odc_HierarchyScope"> </a>

When passed to the **CreateNewPage** method, specifies the style of the new page. 
  
|**Member**|**Value**|**Description**|
|:-----|:-----|:-----|
|**npsDefault** <br/> |0  <br/> |Creates a page that has the default page style.  <br/> |
|**npsBlankPageWithTitle** <br/> |1  <br/> |Creates a blank page that has a title.  <br/> |
|**npsBlankPageNoTitle** <br/> |2  <br/> |Creates a blank page that has no title.  <br/> |
   
## NotebookFilterOutType
<a name="odc_HierarchyScope"> </a>

When passed to the **NotebookFilterOut** method of the **QFD** object, specifies what notebooks to display when the QFD box is rendered. 
  
|**Member**|**Value**|**Description**|
|:-----|:-----|:-----|
|**nfoLocal** <br/> |1  <br/> |Allow only Local Notebooks.  <br/> |
|**nfoNetwork** <br/> |2  <br/> |Allows UNC or SharePoint Notebooks.  <br/> |
|**nfoWeb** <br/> |4  <br/> |Allows OneDrive notebooks.  <br/> |
|**nfoNoWacUrl** <br/> |8  <br/> |Any notebooks in locations that do not have a web client.  <br/> |
   
## PageInfo (Updated for OneNote 2013)
<a name="odc_PageInfo"> </a>

When passed to the **GetPageContent** method, specifies the type of information to return with the page content. 
  
|**Member**|**Value**|**Description**|
|:-----|:-----|:-----|
|**piBasic** <br/> |0  <br/> |Returns only basic page content, without selection markup, file types for binary data objects and binary data objects. This is the standard value to pass.  <br/> |
|**piBinaryData** <br/> |1  <br/> |Returns page content with no selection markup, but with all binary data.  <br/> |
|**piSelection** <br/> |2  <br/> |Returns page content with selection markup, but no binary data.  <br/> |
|**piBinaryDataSelection** <br/> |3  <br/> |Returns page content with selection markup and all binary data.  <br/> |
|**piFileType** <br/> |4  <br/> |Returns page content with file type info for binary data objects.  <br/> |
|**piBinaryDataFileType** <br/> |5  <br/> |Returns page content with file type info for binary data objects and binary data objects  <br/> |
|**piSelectionFileType** <br/> |6  <br/> |Returns page content with selection markup and file type info for binary data.  <br/> |
|**piAll** <br/> |7  <br/> |Returns all page content.  <br/> |
   
## PublishFormat
<a name="odc_PublishFormat"> </a>

When passed to the **Publish** method, specifies the format in which the published page will appear. 
  
|**Member**|**Value**|**Description**|
|:-----|:-----|:-----|
|**pfOneNote** <br/> |0  <br/> |Published page is in the .one format.  <br/> |
|**pfOneNotePackage** <br/> |1  <br/> |Published page is in the .onepkg format.  <br/> |
|**pfMHTML** <br/> |2  <br/> |Published page is in the .mht format.  <br/> |
|**pfPDF** <br/> |3  <br/> |Published page is in the .pdf format.  <br/> |
|**pfXPS** <br/> |4  <br/> |Published page is in the .xps format.  <br/> |
|**pfWord** <br/> |5  <br/> |Published page is in the .doc or .docx format.  <br/> |
|**pfEMF** <br/> |6  <br/> |Published page is in the enhanced metafile (.emf) format.  <br/> |
|**pfHTML** <br/> |7  <br/> |Published page is in the .html format. This member is new in OneNote 2013.  <br/> |
|**pfOneNote2007** <br/> |8  <br/> |Published page is in the 2007 .one format. This member is new in OneNote 2013.  <br/> |
   
## RecentResultType
<a name="odc_RecentResultType"> </a>

When passed to the **SetRecentResults** method of the **IQuickFilingDialog** object, specifies what recent result list to display when the Quick Filing dialog box is rendered. Recent result lists are used to track the set of OneNote locations that the user selects in the Quick Filing dialog box. There are three recent-result lists in OneNote 2013 that track filing, search, and linking actions. This enumeration is new in OneNote 2013. 
  
|**Member**|**Value**|**Description**|
|:-----|:-----|:-----|
|**rrtNone** <br/> |0  <br/> |Sets no recent-result list to be rendered.  <br/> |
|**rrtFiling** <br/> |1  <br/> |Sets the "Filing" recent-result list to be rendered.  <br/> |
|**rrtSearch** <br/> |2  <br/> |Sets the "Search" recent-result list to be rendered.  <br/> |
|**rrtLinks** <br/> |3  <br/> |Sets the "Links" recent-result list to be rendered.  <br/> |
   
## SpecialLocation
<a name="odc_SpecialLocation"> </a>

When passed to the **GetSpecialLocation** method, specifies the special location path to get. 
  
|**Member**|**Value**|**Description**|
|:-----|:-----|:-----|
|**slBackupFolder** <br/> |0  <br/> |Gets the path to the Backup Folders folder location.  <br/> |
|**slUnfiledNotesSection** <br/> |1  <br/> |Gets the path to the Unfiled Notes folder location.  <br/> |
|**slDefaultNotebookFolder** <br/> |2  <br/> |Gets the path to the Default Notebook folder location.  <br/> |
   
## TreeCollapsedStateType
<a name="odc_SpecialLocation"> </a>

When passed to the **TreeCollapsedState** method of the **QFD** object, specifies whether the hierarchy tree should be expanded or collapsed. 
  
|**Member**|**Value**|**Description**|
|:-----|:-----|:-----|
|**tcsExpanded** <br/> |0  <br/> |Sets the hierarchy tree to expanded.  <br/> |
|**tcsCollapsed** <br/> |1  <br/> |Sets the hierarchy tree to collapsed.  <br/> |
   
## XMLSchema (Updated for OneNote 2013)
<a name="odc_SpecialLocation"> </a>

When passed to one of the following methods, specifies the version of the OneNote XML schema to use:
  
- **OneNote15.Application.GetPageContent**
    
- **OneNote15.Application.FindMeta**
    
- **OneNote15.Application.FindPages**
    
- **OneNote15.Application.GetHierarchy**
    
- **OneNote15.Application.GetPageContent**
    
- **OneNote15.Application.UpdateHierarchy**
    
- **OneNote15.Application.UpdatePageContent**
    
|**Member**|**Value**|**Description**|
|:-----|:-----|:-----|
|**xs2007** <br/> |0  <br/> |References the OneNote 2007 schema.  <br/> |
|**xs2010** <br/> |1  <br/> |References the OneNote 2010 schema.  <br/> |
|**xs2013** <br/> |2  <br/> |References the OneNote 2013 schema.  <br/> |
|**xsCurrent** <br/> |2  <br/> |References the schema of the current OneNote version.  <br/> <br/>**NOTE**: We do not recommend using **xsCurrent** in most cases, as it can cause compatibility issues with future versions of OneNote. Instead specify the version of the schema that your app was built to handle, like xs2013.           |
   
## See also

- [OneNote developer reference](onenote-developer-reference.md)

