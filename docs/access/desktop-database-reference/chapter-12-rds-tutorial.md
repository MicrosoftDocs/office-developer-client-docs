---
title: 'Chapter 12: RDS tutorial'
TOCTitle: 'Chapter 12: RDS tutorial'
ms:assetid: fa44a5e8-e4df-dfdd-d7a1-a870ec3cabdd
ms:mtpsurl: https://msdn.microsoft.com/library/JJ250277(v=office.15)
ms:contentKeyID: 48548837
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Chapter 12: RDS Tutorial


**Applies to**: Access 2013, Office 2013

This tutorial illustrates using the RDS programming model to query and update a data source. First, it describes the steps necessary to accomplish this task. Then the tutorial is repeated in Microsoft Visual Basic Scripting Edition and Microsoft Visual J++, featuring ADO for Windows Foundation Classes (ADO/WFC).

This tutorial is coded in different languages for two reasons:

- The documentation for RDS assumes the reader codes in Visual Basic. This makes the documentation convenient for Visual Basic programmers, but less useful for programmers who use other languages.

- If you are uncertain about a particular RDS feature and you know a little of another language, you might be able to resolve your question by looking for the same feature expressed in another language.

## How the tutorial is presented

This tutorial is based on the RDS programming model. It discusses each step of the programming model individually. In addition, it illustrates each step with a fragment of Visual Basic code.

The code example is repeated in other languages with minimal discussion. Each step in a given programming language tutorial is marked with the corresponding step in the programming model and descriptive tutorial. Use the number of the step to refer to the discussion in the descriptive tutorial.

The RDS programming model is stated below. Use it as a roadmap as you proceed through the tutorial.

## RDS programming model with objects

- Specify the program to be invoked on the server, and obtain a way (proxy) to refer to it from the client.

- Invoke the server program. Pass parameters to the server program that identifies the data source and the command to issue.

- The server program obtains a [Recordset](recordset-object-ado.md) object from the data source, typically by using ADO. Optionally, the **Recordset** object is processed on the server.

- The server program returns the final **Recordset** object to the client application.

- On the client, the **Recordset** object is optionally put into a form that can be easily used by visual controls.

- Changes to the **Recordset** object are sent back to the server and used to update the data source.

Following are the steps in this tutorial:

- [Step 1: Specify a server program](step-1-specify-a-server-program-rds-tutorial.md)
- [Step 2: Invoke the server program](step-2-invoke-the-server-program-rds-tutorial.md)
- [Step 3: Server obtains a Recordset](step-3-server-obtains-a-recordset-rds-tutorial.md)
- [Step 4: Server returns the Recordset](step-4-server-returns-the-recordset-rds-tutorial.md)
- [Step 5: DataControl is made usable](step-5-datacontrol-is-made-usable-rds-tutorial.md)
- [Step 6: Changes are sent to the server](step-6-changes-are-sent-to-the-server-rds-tutorial.md)
- [RDS tutorial (VBScript)](rds-tutorial-vbscript.md)
- [RDS tutorial (Visual J++)](rds-tutorial-visual-j.md)