---
title: Append Method (ADOX Procedures)
TOCTitle: Append Method (ADOX Procedures)
ms:assetid: a93b31bb-e41a-5152-abe7-dd7c2b2fcd0a
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249783(v=office.15)
ms:contentKeyID: 48546919
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Append Method (ADOX Procedures)


**Applies to**: Access 2013 | Office 2013

**In this article**  
Syntax  
Parameters  
Remarks  

Adds a new [Procedure](procedure-object-adox.md) object to the [Procedures](procedures-collection-adox.md) collection.

## Syntax

*Procedures*.Append*Name*, *Command*

## Parameters

  - *Name*

  - A **String** value that specifies the name of the procedure to create and append.

  - *Command*

  - An ADO [Command](command-object-ado.md) object that represents the procedure to create and append.

## Remarks

Creates a new procedure in the data source with the name and attributes specified in the **Command** object.

If the command text that the user specifies represents a view rather than a procedure, the behavior is dependent upon the provider being used. **Append** will fail if the provider does not support persisting commands.


> [!NOTE]
> <P>When using the OLE DB Provider for Microsoft Jet, the <STRONG>Procedures</STRONG> collection <STRONG>Append</STRONG> method will allow you to specify a <STRONG>View</STRONG> rather than a <STRONG>Procedure</STRONG> in the <EM>Command</EM> parameter. The <STRONG>View</STRONG> will be added to the data source and will be added to the <STRONG>Procedures</STRONG> collection. After the <STRONG>Append</STRONG>, if the <STRONG>Procedures</STRONG> and <STRONG>Views</STRONG> collections are refreshed, the <STRONG>View</STRONG> will no longer be in the <STRONG>Procedures</STRONG> collection and will appear in the <STRONG>Views</STRONG> collection.</P>


