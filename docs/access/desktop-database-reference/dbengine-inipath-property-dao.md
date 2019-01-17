---
title: DBEngine.IniPath property (DAO)
TOCTitle: IniPath Property
ms:assetid: b18cace5-4e53-d011-6373-f4ac64556fd4
ms:mtpsurl: https://msdn.microsoft.com/library/Ff822009(v=office.15)
ms:contentKeyID: 48547151
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- dao360.chm1053070
f1_categories:
- Office.Version=v15
localization_priority: Normal
---

# DBEngine.IniPath property (DAO)


**Applies to**: Access 2013, Office 2013

Sets or returns information about the Windows Registry key that contains values for the Microsoft Access database engine (Microsoft Access workspaces only).

## Syntax

*expression* .IniPath

*expression* A variable that represents a **DBEngine** object.

## Remarks

You can configure the Microsoft Access databse engine with the Windows Registry. You can use the Registry to set options, such as installable ISAM DLLs.

For this option to have any effect, you must set the **IniPath** property before your application invokes any other DAO code. The scope of this setting is limited to your application and can't be changed without restarting your application.

You also use the Registry to provide initialization parameters for some installable ISAM database drivers. For example, to use Paradox version 4.0, set the **IniPath** property to a part of the Registry containing the appropriate parameters.

This property recognizes either HKEY\_LOCAL\_MACHINE or HKEY\_LOCAL\_USER. If no root key is supplied, the default is HKEY\_LOCAL\_MACHINE.

