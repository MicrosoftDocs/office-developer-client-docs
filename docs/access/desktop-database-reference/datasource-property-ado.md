---
<<<<<<< HEAD
title: DataSource Property (ADO)
TOCTitle: DataSource Property (ADO)
=======
title: DataSource property (ADO)
TOCTitle: DataSource property (ADO)
>>>>>>> master
ms:assetid: 5c5d6c9b-b7d4-45a5-0f6a-a5580a74361e
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249325(v=office.15)
ms:contentKeyID: 48545087
ms.date: 09/18/2015
mtps_version: v=office.15
---

<<<<<<< HEAD
# DataSource Property (ADO)
=======
# DataSource property (ADO)
>>>>>>> master


**Applies to**: Access 2013 | Office 2013

Indicates an object that contains data to be represented as a [Recordset](recordset-object-ado.md) object.

## Remarks

This property is used to create data-bound controls with the Data Environment. The Data Environment maintains collections of data (data sources) containing named objects (*data members*) that will be represented as a **Recordset** object*.*

The [DataMember](datamember-property-ado.md) and **DataSource** properties must be used in conjunction.

The object referenced must implement the **IDataSource** interface and must contain an **IRowset** interface.

**Usage**

```vb
    Dim rs as New ADODB.Recordset
    rs.DataMember = "Command"     'Name of the rowset to bind to
    Set rs.DataSource = myDE      'Name of the object containing an IRowset
```
