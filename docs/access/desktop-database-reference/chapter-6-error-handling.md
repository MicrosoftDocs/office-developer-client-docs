---
title: 'Chapter 6: Error handling'
TOCTitle: 'Chapter 6: Error handling'
ms:assetid: 6ae7343b-b9e0-c4c3-f65c-110f903e573e
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249420(v=office.15)
ms:contentKeyID: 48545440
ms.date: 09/18/2015
mtps_version: v=office.15
localization_priority: Normal
---

# Chapter 6: Error handling

**Applies to**: Access 2013, Office 2013

ADO uses several different methods to notify an application of errors that occur. This chapter discusses the types of errors that can occur when you are using ADO and how your application is notified. It concludes by making suggestions about how to handle those errors.

## How does ADO report errors?

ADO notifies you about errors in several ways:

- ADO errors generate a run-time error. Handle an ADO error the same way you would any other run-time error, such as using an **On Error** statement in Visual Basic.

- Your program can receive errors from OLE DB. An OLE DB error generates a run-time error as well.

- If the error is specific to your data provider, one or more **Error** objects are placed in the **Errors** collection of the **Connection** object that was used to access the data store when the error occurred.

- If the process that raised an event also produced an error, error information is placed in an **Error** object and passed as a parameter to the event. See [Chapter 7: Handling ADO Events](chapter-7-handling-ado-events.md) for more information about events.

- Problems that occur when processing batch updates or other bulk operations involving a **Recordset** can be indicated by the **Status** property of the **Recordset**. For example, schema constraint violations or insufficient permissions can be specified by **RecordStatusEnum** values.

- Problems that occur involving a particular **Field** in the current record are also indicated by the **Status** property of each **Field** in the **Fields** collection of the **Record** or **Recordset**. For example, updates that could not be completed or incompatible data types can be specified by **FieldStatusEnum** values.

The following sections describe each of these notification methods in more detail.

- [ADO errors](ado-errors.md)
- [ADO error reference](ado-error-reference.md)
- [Provider errors](provider-errors.md)
- [Field-related error information](field-related-error-information.md)
- [Recordset-related error information](recordset-related-error-information.md)
- [Anticipating errors](anticipating-errors.md)
- [Handling errors in other languages (ADO)](handling-errors-in-other-languages.md)
