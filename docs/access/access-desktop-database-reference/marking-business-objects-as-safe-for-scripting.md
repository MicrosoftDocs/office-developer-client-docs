﻿---
title: Marking Business Objects as Safe for Scripting
TOCTitle: Marking Business Objects as Safe for Scripting
ms:assetid: 8ee49aec-672d-96f7-baa6-9261317a4d90
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249630(v=office.15)
ms:contentKeyID: 48546295
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Marking Business Objects as Safe for Scripting


**Applies to**: Access 2013 | Office 2013

To help ensure a secure Internet environment, you need to mark any business objects instantiated with the [RDS.DataSpace](dataspace-object-rds.md) object's [CreateObject](createobject-method-rds.md) method as "safe for scripting." You need to ensure they are marked as such in the License area of the system registry before they can be used in DCOM.

To manually mark your business object as safe for scripting, create a text file with a .reg extension that contains the following text. The following two numbers enable the safe-for-scripting feature:

``` 
 
[HKEY_CLASSES_ROOT\CLSID\<MyActiveXGUID>\Implemented 
Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}] 
[HKEY_CLASSES_ROOT\CLSID\<MyActiveXGUID>\Implemented 
Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}] 
```

where \<*MyActiveXGUID*\> is the hexadecimal GUID number of your business object. Save it and merge it into your registry by using the Registry Editor or double-clicking the .reg file in Windows Explorer.

Business objects created in Microsoft® Visual Basic can be automatically marked as "safe for scripting" with the Package and Deployment Wizard. When the wizard asks you to specify safety settings, select **Safe for initialization** and **Safe for scripting**.

On the last step, the Application Setup Wizard creates an .htm and a .cab file. You can then copy these two files to the target computer and double-click the .htm file to load the page and correctly register the server.

Because the business object will be installed in the Windows\\System32\\Occache directory by default, move it to the Windows\\System32 directory and change the **HKEY\_CLASSES\_ROOT\\CLSID\\**\<*MyActiveXGUID*\>\\**InprocServer32** registry key to match the correct path.


> [!NOTE]
> <P>Business objects marked as safe for scripting or safe for initialization can be instantiated and initialized by anyone over the network. Any custom business object must not be designed and implemented casually. It is imperative that such objects do not present a security threat that hackers can explore to gain access to the sensitive area of the hosting server and inflict damages.</P>


