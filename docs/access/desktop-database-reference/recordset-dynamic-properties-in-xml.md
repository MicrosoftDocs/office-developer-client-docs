---
title: Recordset dynamic properties in XML
TOCTitle: Recordset dynamic properties in XML
ms:assetid: 6ee1f176-9986-4ade-fc97-e3dad8e6bc6b
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249439(v=office.15)
ms:contentKeyID: 48545522
ms.date: 09/18/2015
mtps_version: v=office.15
localization_priority: Normal
---

# Recordset dynamic properties in XML

**Applies to**: Access 2013, Office 2013

The following **Recordset** provider-specific properties (from the Client Cursor Engine) are currently persisted into the XML format:

- **AutoRecalc**
- **BatchSize**
- **CommandTimeout**
- **IRowsetChange**
- **IRowsetUpdate**
- **Reshape Name**
- **Resync Command**
- **Unique Catalog**
- **Unique Schema**
- **Unique Table**
- **Update Resync**
- **UpdateCriteria**


These properties are saved in the schema section as attributes of the element definition for the **Recordset** being persisted. These attributes are defined in the rowset schema namespace and must have the prefix "rs:".

## See also

- [ADO dynamic properties](ado-dynamic-properties.md)
