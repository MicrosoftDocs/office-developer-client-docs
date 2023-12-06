---
title: "MsoFIsFileFromTrustedLocation function" 
manager: lijia
ms.date: 10/11/2023
ms.audience: Developer
api_name:
- MsoFIsFileFromTrustedLocation
- _MsoFIsFileFromTrustedLocation
api_type:
- DLLExport
api_location:
- mso.dll
topic_type:
- APIRef
- kbSyntax
APIPlatform: Office
ms.localizationpriority: low
ms.assetid: 
description: "Find information about the MsoFIsFileFromTrustedLocation function."
---

# MsoFIsFileFromTrustedLocation function

## Description

This function will check if the given file is from some trusted location or not. The function with underscore prefix is used in a 32-bit Windows cdecl calling convention.

```CPP
BOOL MsoFIsFileFromTrustedLocation(const WCHAR* wzPath) 

```

```CPP
BOOL _MsoFIsFileFromTrustedLocation(const WCHAR* wzPath) 

```

## Return value

Boolean, which represents if the given file is from some trusted location.

## Remarks

A trusted location is where to store a file when you don’t want that file to be checked by the Office Trust Center.

## Requirements

|  |  |
|---------------------------------|--------------------------------|
|DLL                              |MSO.DLL                         |
|Minimum supported application    |Microsoft Office 2007 system    |
