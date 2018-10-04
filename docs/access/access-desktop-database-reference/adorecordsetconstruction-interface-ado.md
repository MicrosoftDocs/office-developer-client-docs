---
title: ADORecordsetConstruction Interface (ADO)
TOCTitle: ADORecordsetConstruction Interface (ADO)
ms:assetid: 2b53aa6e-3b6f-a996-3967-534215fd586c
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249060(v=office.15)
ms:contentKeyID: 48543926
ms.date: 09/18/2015
mtps_version: v=office.15
---

# ADORecordsetConstruction Interface (ADO)


**Applies to**: Access 2013 | Office 2013

**In this article**  
Properties  
Methods  
Events  
Remarks  
Requirements  

The **ADORecordsetConstruction** interface is used to construct an ADO **Recordset** object from an OLE DB **Rowset** object in a C/C++ application.

This interface supports the following properties:

## Properties

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><a href="chapter-property-ado.md">Chapter</a></p></td>
<td><p>Read/Write.<br />
Gets/sets an OLE DB <strong>Chapter</strong> object from/on this ADO <strong>Recordset</strong> object.</p></td>
</tr>
<tr class="even">
<td><p><a href="rowposition-property-ado.md">RowPosition</a></p></td>
<td><p>Read/Write.<br />
Gets/sets an OLE DB <strong>RowPosition</strong> object from/on this ADO <strong>Recordset</strong> object.</p></td>
</tr>
<tr class="odd">
<td><p><a href="rowset-property-ado.md">Rowset</a></p></td>
<td><p>Read/Write.<br />
Gets/sets an OLE DB <strong>Rowset</strong> object from/on this ADO <strong>Recordset</strong> object.</p></td>
</tr>
</tbody>
</table>


## Methods

None.

## Events

None.

## Remarks

Given an OLE DB **Rowset** object (pRowset ), the construction of an ADO **Recordset** object (), the construction of an ADO **Recordset** object (adoRs ) amounts to the following three basic operations:

1.  Create an ADO **Recordset** object:
    
        Recordset20Ptr adoRs;
        adoRs.CreateInstance(__uuidof(Recordset));

2.  Query the **IADORecordsetConstruction** interface on the **Recordset** object:
    
        adoRecordsetConstructionPtr adoRsConstruct=NULL;
        adoRs->QueryInterface(__uuidof(ADORecordsetConstruction),
                             (void**)&adoRsConstruct);

3.  Call the IADORecordsetConstruction::put\_Rowset property method to set the OLE DB Rowset object on the ADO Recordset object:
    
        IUnknown *pUnk=NULL;
        pRowset->QueryInterface(IID_IUnknown, (void**)&pUnk);
        adoRsConstruct->put_Rowset(pUnk);

The resultant object now represents the ADO **Recordset** object constructed from the OLE DB **Rowset** object.

You can also construct an ADO **Recordset** object from an OLE DB **Chapter** or **RowPosition** object.

## Requirements

**Version:** ADO 2.0 and later

**Library:** msado15.dll

**UUID:** 00000283-0000-0010-8000-00AA006D2EA4

