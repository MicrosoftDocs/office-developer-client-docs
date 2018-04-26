---
title: "What's New in ADO"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: overview
  
localization_priority: Normal
ms.assetid: fd3d0f9c-e9df-d130-13e3-757620e9400c
description: "The following new features and enhanced documentation are included in the ADO 2.5 release. This list covers ADO, ADO MD, and ADOX."
---

# What's New in ADO

The following new features and enhanced documentation are included in the ADO 2.5 release. This list covers ADO, ADO MD, and ADOX.
  
## New Features

 **[Records and Streams](chapter-10-records-and-streams.md)**
  
This release of ADO introduces the [Record](record-object-ado.md) object, which can represent and manage things like directories and files in a file system, and folders and messages in an e-mail system. A **Record** can also represent a row in a [Recordset](recordset-object-ado.md), although **Record** and **Recordset** objects have different methods and properties. 
  
The new [Stream](stream-object-ado.md) object provides the means to read, write, and manage the binary stream of bytes or text that comprise a file or message stream. 
  
 **[URL Usage](absolute-and-relative-urls.md)**
  
This release also introduces the use of Uniform Resource Locators (URLs), as an alternative to connection strings and command text, to name data store objects. URLs may be used with the existing [Connection](connection-object-ado.md) and **Recordset** objects, as well as with the new **Record** and **Stream** objects. 
  
With this release, ADO supports OLE DB providers that recognize their own URL schemes. For example, the [OLE DB Provider for Internet Publishing](microsoft-ole-db-provider-for-internet-publishing.md) *,*  which accesses the Windows 2000 file system, recognizes the existing HTTP scheme. 
  
 **[Special Fields for Document Source Providers](records-and-provider-supplied-fields.md)**
  
A special class of providers, called  *document source*  providers, manage folders and documents. When a **Record** object represents a document, or a **Recordset** object represents a folder of documents, the document source provider populates those objects with a unique set of fields that describe characteristics of the document. These fields constitute a  *resource* **Record** or **Recordset**. 
  
## New Reference Topics

The following new properties are included in this release.
  
|**Property**|**Description**|
|:-----|:-----|
|[Charset](charset-property-ado.md) <br/> |Indicates the character set into which the contents of a text **Stream** object should be translated.  <br/> |
|[EOS](eos-property-ado.md) <br/> |Indicates whether the current position is at the end of the stream.  <br/> |
|[LineSeparator](lineseparator-property-ado.md) <br/> |Indicates the binary character to be used as the line separator in text **Stream** objects.  <br/> |
|[Mode](mode-property-ado.md) <br/> |Indicates the available permissions for modifying data in a **Connection**, **Record**, or **Stream** object.  <br/> |
|[ParentURL](parenturl-property-ado.md) <br/> |Indicates an absolute URL string that points to the parent **Record** of the current **Record** object.  <br/> |
|[Position](position-property-ado.md) <br/> |Indicates the current position within a **Stream** object.  <br/> |
|[RecordType](recordtype-property-ado.md) <br/> |Indicates the type of **Record** object.  <br/> |
|[Size](http://msdn.microsoft.com/library/deb84313-36d1-fa49-e4cd-daecab96f343%28Office.15%29.aspx) <br/> |Indicates the size of the stream in number of bytes.  <br/> |
|[Source](source-property-ado-record.md) <br/> |Indicates the entity represented by the **Record** object.  <br/> |
|[State](state-property-ado.md) <br/> |Indicates for all applicable objects whether the state of the object is open or closed. Indicates for all applicable objects executing an asynchronous method, whether the current state of the object is connecting, executing, or retrieving.  <br/> |
|[Type](type-property-ado-stream.md) <br/> |Indicates the type of data contained in the **Stream** object (binary or text).  <br/> |
   
The following new methods are included in this release.
  
|**Method**|**Description**|
|:-----|:-----|
|[CopyRecord](copyrecord-method-ado.md) <br/> |Copies a file or directory, and its contents, to another location.  <br/> |
|[CopyTo](copyto-method-ado.md) <br/> |Copies the specified number of characters or bytes (depending on **Type** ) in the **Stream** **object** to another **Stream** object.  <br/> |
|[DeleteRecord](deleterecord-method-ado.md) <br/> |Deletes a file or directory, and all its subdirectories.  <br/> |
|[Flush](flush-method-ado.md) <br/> |Forces the contents of the **Stream** object remaining in the ADO buffer to the underlying object with which the **Stream** object is associated.  <br/> |
|[GetChildren](getchildren-method-ado.md) <br/> |Returns a **Recordset** whose rows represent the files and subdirectories in the directory represented by this **Record.** <br/> |
|[LoadFromFile](loadfromfile-method-ado.md) <br/> |Loads the contents of an existing file into a **Stream** object.  <br/> |
|[MoveRecord](moverecord-method-ado.md) <br/> |Moves a file, or a directory and its contents, to another location.  <br/> |
|[Open](open-method-ado-record.md) <br/> |Opens an existing **Record** object, or creates a new file or directory.  <br/> |
|[Open](open-method-ado-stream.md) <br/> |Opens a **Stream** object to manipulate streams of binary or text data.  <br/> |
|[Read](read-method-ado.md) <br/> |Reads a specified number of bytes from a binary **Stream** object.  <br/> |
|[ReadText](readtext-method-ado.md) <br/> |Reads specified number of characters from a text **Stream** object.  <br/> |
|[SaveToFile](savetofile-method-ado.md) <br/> |Saves the binary contents of a **Stream** to a file.  <br/> |
|[SetEOS](seteos-method-ado.md) <br/> |Sets the position that is the end of the stream.  <br/> |
|[SkipLine](skipline-method-ado.md) <br/> |Skips one entire line when reading a text **Stream** object.  <br/> |
|[Write](write-method-ado.md) <br/> |Writes binary data to a **Stream** object.  <br/> |
|[WriteText](writetext-method-ado.md) <br/> |Writes a specified text string to a **Stream** object.  <br/> |
   
## New and Enhanced Documentation

 **[Code Example Topics](ado-code-examples.md)**
  
The examples have been expanded to contain code examples written in Microsoft Visual C++® and Microsoft Visual J++®. You can copy and paste these code examples into your editor.
  
 **[Provider Topics](appendix-a-providers.md)**
  
A new topic is included that explains how to use ADO with the [OLE DB Provider for Internet Publishing](microsoft-ole-db-provider-for-internet-publishing.md).
  
 **[Programming with ADO](appendix-c-programming-with-ado.md)**
  
This new section contains tips and tricks for using ADO with various programming languages. It contains the existing syntax indexes for the Visual C++ Extensions for ADO and ADO/WFC, as well as new information specific to developers using Microsoft Visual Basic®, Microsoft Visual Basic® Scripting Edition, Microsoft JScript®, Microsoft Visual C++, or Microsoft Visual J++.
  

