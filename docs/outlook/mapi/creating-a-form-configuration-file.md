---
title: "Creating a Form Configuration File"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: aaf3b33d-ad2d-4ef8-847f-1ab1eaf08706
description: "Last modified: July 23, 2011"
 
 
---

# Creating a Form Configuration File

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
A form configuration file provides information about a form both to the form manager being used and to client applications. A form configuration file contains an extensive specification for a form, including the properties published by the form for use by messaging clients, the verbs implemented by the form, and the platforms supported by the form.
  
A form configuration file is a file with a .cfg extension, and has a format similar to a Windows initialization file. It is a plain text file with a number of sections. Each section begins with a section name, enclosed in square brackets. Each section contains one or more lines that define values and settings relevant to that section. Values have one of the following types:
  
- String
    
- Displayed string
    
- Platform string
    
- Path name
    
- Integer
    
- GUID
    
For more information about the sections of a .cfg file, see [File Format of Form Configuration Files](file-format-of-form-configuration-files.md).
  
## See also



[Developing MAPI Form Servers](developing-mapi-form-servers.md)

