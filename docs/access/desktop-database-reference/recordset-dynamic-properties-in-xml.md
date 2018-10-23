---
title: Recordset Dynamic Properties in XML
TOCTitle: Recordset Dynamic Properties in XML
ms:assetid: 6ee1f176-9986-4ade-fc97-e3dad8e6bc6b
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249439(v=office.15)
ms:contentKeyID: 48545522
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Recordset Dynamic Properties in XML


**Applies to**: Access 2013 | Office 2013

## Recordset Dynamic Properties in XML

The following **Recordset** provider-specific properties (from the Client Cursor Engine) are currently persisted into the XML format:

  - **Update Resync**

  - **Unique Table**

  - **Unique Schema**

  - **Unique Catalog**

  - **Resync Command**

  - **IRowsetChange**

  - **IRowsetUpdate**

  - **CommandTimeout**

  - **BatchSize**

  - **UpdateCriteria**

  - **Reshape Name**

  - **AutoRecalc**

These properties are saved in the schema section as attributes of the element definition for the **Recordset** being persisted. These attributes are defined in the rowset schema namespace and must have the prefix "rs:".

