---
title: 'Chapter 15: ADOX fundamentals'
TOCTitle: 'Chapter 15: ADOX fundamentals'
ms:assetid: 973d7579-4f34-3b31-a761-a951ab29e850
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249673(v=office.15)
ms:contentKeyID: 48546464
ms.date: 09/18/2015
mtps_version: v=office.15
ms.localizationpriority: medium
---

# Chapter 15: ADOX fundamentals

**Applies to**: Access 2013, Office 2013

Microsoft ActiveX Data Objects Extensions for Data Definition Language and Security (ADOX) is an extension to the ADO objects and programming model. ADOX includes objects for schema creation and modification, as well as security. Because it is an object-based approach to schema manipulation, you can write code that will work against various data sources regardless of differences in their native syntaxes.

ADOX is a companion library to the core ADO objects. It exposes additional objects for creating, modifying, and deleting schema objects, such as tables and procedures. It also includes security objects to maintain users and groups and to grant and revoke permissions on objects.

To use ADOX with your development tool, you should establish a reference to the ADOX type library. The description of the ADOX library is "Microsoft ADO Ext. for DDL and Security." The ADOX library file name is Msadox.dll, and the program ID (ProgID) is "ADOX". For more information about establishing references to libraries, see the documentation of your development tool.

The Microsoft OLE DB Provider for the Microsoft Jet Database Engine fully supports ADOX. Certain features of ADOX may not be supported, depending on your data provider. For more information about supported features with the Microsoft OLE DB Provider for ODBC, the Microsoft OLE DB Provider for Oracle, or the Microsoft SQL Server OLE DB Provider, see the MDAC readme file.

This document assumes a working knowledge of the Microsoft Visual Basic programming language and a general knowledge of ADO. For more information about ADO, see the [ADO programmer's guide](ado-programmer-s-guide.md).

This chapter covers the following topic:

- [Provider support for ADOX](provider-support-for-adox.md)

For more overview information about ADOX, see the following topics:

- [ADOX objects](adox-objects.md)
- [ADOX collections](adox-collections.md)
- [ADOX properties](adox-properties.md)
- [ADOX methods](adox-methods.md)
- [ADOX examples](adox-code-examples.md)

