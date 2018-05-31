---
title: "PidTagFolderWebViewInfo Cannonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagFolderWebViewInfo
api_type:
- HeaderDef
ms.assetid: 96ea23df-aa4f-4b3e-9663-e7db39f668c1
description: "Last modified: March 09, 2015"
---

# PidTagFolderWebViewInfo Cannonical Property

  
  
**Applies to**: Outlook 
  
Contains the URL for the home page of a folder in Microsoft Outlook. This property contains a binary stream called **WebViewPersistenceObject**.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_FOLDER_WEBVIEWINFO  <br/> |
|Identifier:  <br/> |0x36DF  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |MAPI folder  <br/> |
   
## Remarks

A home page URL can be specified for any Outlook folder. This information can be accessed in Outlook from the **Home Page** tab of the Properties dialog box for a folder. 
  
Depending on certain policy settings, the home page might be ignored by Outlook if the MAPI store that contains this folder does not report MSCAP_SECURE_FOLDER_HOMEPAGES in its [IMSCapabilities::GetCapabilities](pidtagfolderwebviewinfo-cannonical-property.md) implementation. 
  
Both the **Outlook Today** folder and a public folder can have home page URLs. However the **Outlook Today** folder uses a different mechanism to manage its home page URL; that mechanism is not covered in this topic. A public folder might also have a home page URL defined in it that is specific to a user. However, that capability is not described in this topic. 
  
The value of this property is a binary stream called **WebViewPersistenceObject**.
  
### WebViewPersistenceObject Stream Structure

The **WebViewPersistenceObject** stream structure contains information about a home page URL for a folder. 
  
Data elements in this structure are stored in little-endian byte order, immediately following one another in the following specified order. 
  
> [!NOTE]
> The following description may not list all of the field values supported by Outlook; therefore, when your code reads an existing stream, some flags that are not listed here might also be found. However, you can use this description to programmatically create values for the **PidTagFolderWebViewInfo** property that Outlook will understand. 
  
 _dwVersion_
  
> DWORD (4 bytes). The version of the structure's format. As of Microsoft Office Outlook 2007, the only supported value for this field is as follows.
    
|**Value name**|**Value**|
|:-----|:-----|
|WEBVIEW_PERSISTENCE_VERSION  <br/> |0x00000002  <br/> |
   
 _dwType_
  
> DWORD (4 bytes). The type of the home page information. As of Microsoft Office Outlook 2007, the only supported value for this field is as follows.
    
|**Value name**|**Value**|
|:-----|:-----|
|WEBVIEWURL  <br/> |0x00000001  <br/> |
   
 _dwFlags_
  
> DWORD (4 bytes). A combination of zero or more flags whose values and meanings are listed in the following table.
    
|****Flag name****|****Value****|****Description****|
|:-----|:-----|:-----|
|WEBVIEW_FLAGS_SHOWBYDEFAULT  <br/> |0x00000001  <br/> |The **Show home page by default for this folder** check box was checked in the **Home Page** tab of the Properties dialog box for a folder.  <br/> |
   
 _dwUnused[7]_
  
> An array of 7 DWORD elements (28 bytes total). Unused.
    
cbData
  
> A ULONG (4 bytes). The size, in bytes, of the  _wzURL_ data element. 
    
 _wzURL_
  
> An array of WCHAR elements. The UTF-16 representation of the zero-terminated home page URL string.
    
### WebViewPersistenceObject Stream Sample

This section describes an example of a **WebViewPersistenceObject** stream. The stream specifies the home page URL "http://www.microsoft.com". 
  
 **Data dump**
  
The following is a data dump of the stream as it would be displayed in a binary editor.
  
|**Stream offset**|**Data bytes**|**ASCII data**|
|:-----|:-----|:-----|
|0000000000  <br/> | `02 00 00 00 01 00 00 00 01 00 00 00 00 00 00 00` <br/> | `?...?...?.......` <br/> |
|0000000010  <br/> | `00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00` <br/> | `................` <br/> |
|0000000020  <br/> | `00 00 00 00 00 00 00 00 32 00 00 00 68 00 74 00` <br/> | `........2...h.t.` <br/> |
|0000000030  <br/> | `74 00 70 00 3A 00 2F 00 2F 00 77 00 77 00 77 00` <br/> | `t.p.:././.w.w.w.` <br/> |
|0000000040  <br/> | `2E 00 6D 00 69 00 63 00 72 00 6F 00 73 00 6F 00` <br/> | `..m.i.c.r.o.s.o.` <br/> |
|0000000050  <br/> | `66 00 74 00 2E 00 63 00 6F 00 6D 00 00 00` <br/> | `f.t...c.o.m...` <br/> |
   
The following is a parse of the sample data for the **WebViewPersistenceObject** stream. 
  
 _dwVersion_
  
> Offset 0x0, 4 bytes: 0x00000002 (WEBVIEW_PERSISTENCE_VERSION).
    
 _dwType_
  
> Offset 0x4, 4 bytes: 0x00000001 (WEBVIEWURL).
    
 _dwFlags_
  
> Offset 0x8, 4 bytes: 0x00000001 (WEBVIEW_FLAGS_SHOWBYDEFAULT).
    
 _dwUnused[7]_
  
> Offset 0xC, 28 bytes: all zeros.
    
 _cbData_
  
> Offset 0x28, 4 bytes: 0x00000032.
    
 _wzURL_
  
> Offset 0x2C, 0x32 bytes: array of 25 WCHARs. A Unicode zero-terminated string value: "http://www.microsoft.com".
    

