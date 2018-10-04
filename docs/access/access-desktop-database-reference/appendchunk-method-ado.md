---
title: AppendChunk Method (ADO)
TOCTitle: AppendChunk Method (ADO)
ms:assetid: 3fa931a3-2cd7-a3b0-a750-40e18bc9937e
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249179(v=office.15)
ms:contentKeyID: 48544405
ms.date: 09/18/2015
mtps_version: v=office.15
---

# AppendChunk Method (ADO)


**Applies to**: Access 2013 | Office 2013

**In this article**  
Syntax  
Parameters  
Remarks  

Appends data to a large text or binary data [Field](field-object-ado.md), or to a [Parameter](parameter-object-ado.md) object.

## Syntax

*object.*AppendChunk *Data*

## Parameters

  - *object*

  - A **Field** or **Parameter** object.

  - *Data*

  - A **Variant** that contains the data to append to the object.

## Remarks

Use the **AppendChunk** method on a **Field** or **Parameter** object to fill it with long binary or character data. In situations where system memory is limited, you can use the **AppendChunk** method to manipulate long values in portions rather than in their entirety.

**Field**

If the **adFldLong** bit in the [Attributes](attributes-property-ado.md) property of a **Field** object is set to true, you can use the **AppendChunk** method for that field.

The first **AppendChunk** call on a **Field** object writes data to the field, overwriting any existing data. Subsequent **AppendChunk** calls add to existing data. If you are appending data to one field and then you set or read the value of another field in the current record, ADO assumes that you are finished appending data to the first field. If you call the **AppendChunk** method on the first field again, ADO interprets the call as a new **AppendChunk** operation and overwrites the existing data. Accessing fields in other [Recordset](recordset-object-ado.md) objects that are not clones of the first **Recordset** object will not disrupt **AppendChunk** operations.

If there is no current record when you call **AppendChunk** on a **Field** object, an error occurs.


> [!NOTE]
> <P>The <STRONG>AppendChunk</STRONG> method does not operate on <STRONG>Field</STRONG> objects of a <A href="record-object-ado.md">Record</A> object. It does not perform any operation and will produce a run-time error.</P>



**Parameter**

If the **adParamLong** bit in the **Attributes** property of a **Parameter** object is set to true, you can use the **AppendChunk** method for that parameter.

The first **AppendChunk** call on a **Parameter** object writes data to the parameter, overwriting any existing data. Subsequent **AppendChunk** calls on a **Parameter** object add to existing parameter data. An **AppendChunk** call that passes a null value discards all of the parameter data.

