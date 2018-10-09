---
title: Append Method (ADOX Views)
TOCTitle: Append Method (ADOX Views)
ms:assetid: 202f1d0a-dc5d-84e5-daf3-3212e5bc6088
ms:mtpsurl: https://msdn.microsoft.com/library/JJ248985(v=office.15)
ms:contentKeyID: 48543655
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Append Method (ADOX Views)


**Applies to**: Access 2013 | Office 2013


Creates a new [View](view-object-adox.md) object and appends it to the [Views](views-collection-adox.md) collection.

## Syntax

*Views*.Append*Name*, *Command*

## Parameters

  - *Name*

  - A **String** value that specifies the name of the view to create.

  - *Command*

  - An ADO [Command](command-object-ado.md) object that represents the view to create.

## Remarks

Creates a new view in the data source with the name and attributes specified in the **Command** object.

If the command text that the user specifies represents a procedure rather than a view, the behavior is dependent upon the provider. **Append** will fail if the provider does not support persisting commands.


> [!NOTE]
> <P>When using the OLE DB Provider for Microsoft Jet, the <STRONG>Views</STRONG> collection <STRONG>Append</STRONG> method will allow you to specify a <STRONG>Procedure</STRONG> rather than a <STRONG>View</STRONG> in the <EM>Command</EM> parameter. The <STRONG>Procedure</STRONG> will be added to the data source and will be added to the <STRONG>Views</STRONG> collection. After the <STRONG>Append</STRONG>, if the <STRONG>Procedures</STRONG> and <STRONG>Views</STRONG> collections are refreshed, the <STRONG>Procedure</STRONG> will no longer be in the <STRONG>Views</STRONG> collection and will appear in the <STRONG>Procedures</STRONG> collection.</P>


