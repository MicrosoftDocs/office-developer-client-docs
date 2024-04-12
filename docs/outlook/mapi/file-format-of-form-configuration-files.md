---
title: "File format of form configuration files"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 86e4ebd9-6df2-4346-9ce9-580f80a83884
---

# File format of form configuration files

**Applies to**: Outlook 2013 | Outlook 2016 
  
A form configuration file is a formatted file created by form developers to define a form.
  
Because form configuration files are used by form managers to load forms, each form must be defined using a form configuration file. Form configuration files must have the .cfg filename extension. The file follows the general syntax of a Windows initialization file (.ini file). 

It is divided into named sections, and each section contains a series of entries and values. Values have one of the following types: string, displayed string, platform string, path, integer, or globally unique identifier, **GUID**. Form configuration files can be created with any text editor or word processor that is capable of saving text files.
  

