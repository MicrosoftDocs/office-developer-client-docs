---
title: 'Chapter 2: Getting Data'
TOCTitle: 'Chapter 2: Getting Data'
ms:assetid: 72d097e1-9284-cc27-fd48-e6bbb6a2a543
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ249465(v=office.15)
ms:contentKeyID: 48545619
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Chapter 2: Getting Data


_**Applies to:** Access 2013 | Office 2013_

The preceding chapter introduced four primary operations involved in creating an ADO application: getting data, examining data, editing data, and updating data. This chapter will focus on the details of the concepts relevant to the first operation: getting data.

Several ADO objects can play a role in this operation. First you connect to the data source using an ADO **Connection** object (which at times will be created implicitly). Then you pass instructions to the data source about what you want to do using an ADO **Command** object (which also can be created implicitly). The result of passing a command to a data source and receiving its response usually will be represented in an ADO **Recordset** object.

To get data, your application must be in communication with a data source, such as a DBMS, a file store, or a comma-delimited text file. This communication represents a *connection* — the environment necessary for exchanging data.

The ADO object model represents the concept of a connection with the **Connection** object — the foundation upon which much ADO functionality is built. The purpose of a **Connection** object is to:

  - Define the information ADO needs to communicate with data sources and create sessions.

  - Define the transactional capabilities of the session.

  - Allow you to create and execute commands against the data source.

  - Provide information about the design of the underlying data source in the form of schema rowsets. For more information about schema rowsets, see [OpenSchema Method](openschema-method-ado.md).

