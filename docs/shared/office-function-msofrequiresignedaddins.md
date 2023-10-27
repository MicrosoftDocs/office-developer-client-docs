---
title: "MsoFRequireSignedAddins function"
manager: lijia
ms.date: 10/11/2023
ms.audience: Developer
APIPlatform: Office 
ms.localizationpriority: low
ms.assetid: 
description: "Find information about the MsoFRequireSignedAddins function."
---

# MsoFRequireSignedAddins function

## Description

This function will check if Office Trust Center requires Application Add-ins to be signed by Trusted Publishers. The function with underscore prefix is used in a 32-bit Windows cdecl calling convention.

```CPP
BOOL MsoFRequireSignedAddins()

```

```CPP
BOOL _MsoFRequireSignedAddins()

```

## Return value

Boolean, which represents if Office Trust Center requires Application Add-ins to be signed by Trusted Publishers.

## Requirements

|  |  |
|---------------------------------|--------------------------------|
|DLL                              |MSO.DLL                         |
|Minimum supported application    |Microsoft Office 2010 system    |
