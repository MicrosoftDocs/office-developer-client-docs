---
title: Using ADO with Scripting Languages
TOCTitle: Using ADO with Scripting Languages
ms:assetid: 2e163ffb-22fe-36f5-9960-8f6bcb148183
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ249074(v=office.15)
ms:contentKeyID: 48543985
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Using ADO with Scripting Languages


_**Applies to:** Access 2013 | Office 2013_

**In this article**  
ODBC Data Sources  
Referencing the ADO Library  
Handling events  

Within a scripting environment, ADO allows you to expose data by way of server-side scripting. In this scenario, ADO, the underlying OLE DB provider that it utilizes, and any other components needed to reference a given data store are installed on a server running Internet Information Services (IIS). Using Active Server Pages (ASP), ADO is a component referenced in a script that can generate HTML, for example. This HTML content can be passed via HTTP to a client Web browser. Through the use of scripting, the Web page can send actions back to the server-side script, allowing you to update, traverse, or view specific data.

## ODBC Data Sources

One notable difference between scripting and non-scripting ADO code is the ODBC Data Source, if used. For non-scripting applications, you can create a User DSN in the ODBC Data Source Administrator. For scripts that are running under IIS, you must create a System DSN; otherwise your scripts won't recognize the data source you created. This applies to any ADO scripting application using the Microsoft OLE DB Provider for ODBC through Microsoft IIS.

## Referencing the ADO Library

N/A with scripting languages.

## Handling events

N/A with scripting languages.

The following topics contain more specific information about using ADO with scripting languages:

  - [ADO in VBScript](vbscript-ado-programming.md)

  - [ADO in JScript](jscript-ado-programming.md)

