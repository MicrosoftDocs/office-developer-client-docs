---
title: Application.SaveAsText
TOCTitle: Application.SaveAsText
ms:assetid: 7cf8dc49-8a68-450f-bdc1-a55bcf6d485c
ms.date: 08/06/2024
ms.localizationpriority: medium
---

# Application.SaveAsText

**Applies to**: Access 2024, Access 2019

The Application.SaveAsText method in Microsoft Access allows you to export database objects (like forms, reports, macros, modules, or queries) into a text file. This can be useful for version control, debugging, or transferring objects between databases.

## Syntax

Application.SaveAsText _ObjectType_, _ObjectName_, _FileName_

## Parameters

|Parameter|Description|
|:--------|:-----------|
|_ObjectType_|The type of object you want to export (e.g., acForm, acReport, acQuery, etc.).|
|_ObjectName_|The name of the object you want to export.|
|_FileName_|The full path and name of the text file where the object will be saved.|

## Example
Here’s how you can save a form named "MyForm" to a text file:

```vba
Application.SaveAsText acForm, "MyForm", "C:\Exports\MyForm.txt"
```

## Remarks

The exported text file contains all the properties and definitions of the object. You can later use the Application.LoadFromText method to import the object back into a database. This method is particularly useful for developers who want to integrate Access objects into version control systems or share objects in a readable format.
