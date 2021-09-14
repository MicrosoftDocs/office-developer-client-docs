---
title: DBEngine.DefaultPassword property (DAO)
TOCTitle: DefaultPassword Property
ms:assetid: 189e34f3-d573-c75f-8be2-d98c50df8a52
ms:mtpsurl: https://msdn.microsoft.com/library/Ff845616(v=office.15)
ms:contentKeyID: 48543478
ms.date: 09/18/2015
mtps_version: v=office.15
ms.localizationpriority: medium
---

# DBEngine.DefaultPassword property (DAO)


**Applies to**: Access 2013, Office 2013

Sets the password used to create the default **Workspace** when it is initialized. Read/write **String**.

## Syntax

*expression* .DefaultPassword

*expression* A variable that represents a **DBEngine** object.

## Remarks

The setting for **DefaultPassword** is a String data type that can be up to 20 characters long. It can contain any character except ASCII 0.


> [!NOTE]
> Use strong passwords that combine upper- and lowercase letters, numbers, and symbols. Weak passwords don't mix these elements. Strong password: Y6dh!et5. Weak password: House27. Use a strong password that you can remember so that you don't have to write it down.

By default, the **DefaultUser** property is set to "admin" and the **DefaultPassword** property is set to a zero-length string ("").

Typically, you use the **CreateWorkspace** method to create a **Workspace** object with a given user name and password. However, for backward compatibility with earlier versions and for convenience when you don't implement a secured database, the Microsoft Access database engine automatically creates a default **Workspace** object when needed if one isn't already open. In this case, the **DefaultUser** and **DefaultPassword** property values define the user and password for the default **Workspace** object.

For this property to take effect, you should set it before calling any DAO methods.

