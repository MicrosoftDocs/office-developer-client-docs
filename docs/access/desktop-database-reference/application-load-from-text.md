---
title: Application.LoadFromText
TOCTitle: Application.LoadFromText
ms:assetid: 6cd9963e-7edc-4834-b4c2-0983fe47e72b
ms.date: 08/06/2024
ms.localizationpriority: medium
---

# Application.LoadFromText

**Applies to**: Access 2024, Access 2019

The Application.LoadFromText is a method used to import database objects (like forms, reports, queries, etc.) from a text file into an Access database. This is often paired with [Application.SaveAsText](application-save-as-text.md), which exports database objects to text files. These methods are particularly useful for version control, backups, or transferring objects between databases.

## Syntax

Application.LoadFromText _ObjectType_, _ObjectName_, _FileName_

## Parameters

|Parameter|Description|
|:--------|:-----------|
|_ObjectType_|The type of object (e.g., acForm, acReport, acQuery, etc.).|
|_ObjectName_|The name of the object to be imported.|
|_FileName_|The full path to the text file containing the object definition.|

## Example

Here’s how you can import a form that was saved as a text file.

```vba
Application.LoadFromText acForm, "MyForm", "C:\Backup\MyForm.txt"
```

## Remarks

Be cautious when using LoadFromText with complex queries involving subqueries, as it may occasionally result in corrupted queries. This method is unsupported but widely used by developers for advanced tasks like version control or automated deployments.
