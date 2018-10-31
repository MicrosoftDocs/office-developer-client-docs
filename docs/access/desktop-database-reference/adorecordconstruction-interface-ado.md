---
title: ADORecordConstruction Interface (ADO)
TOCTitle: ADORecordConstruction Interface (ADO)
ms:assetid: 3f0afbdb-f1c4-e44e-7c0f-a0c4cee554a7
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249175(v=office.15)
ms:contentKeyID: 48544387
ms.date: 09/18/2015
mtps_version: v=office.15
---

# ADORecordConstruction Interface (ADO)


**Applies to**: Access 2013, Office 2013

The **ADORecordConstruction** interface is used to construct an ADO **Record** object from an OLE DB **Row** object in a C/C++ application.

This interface supports the following properties:

## Properties

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><a href="parentrow-property-ado.md">ParentRow</a></p></td>
<td><p>Write-only.<br />
Sets the container of an OLE DB <strong>Row</strong> object on this ADO <strong>Record</strong> object.</p></td>
</tr>
<tr class="even">
<td><p><a href="row-property-ado.md">Row</a></p></td>
<td><p>Read/Write.<br />
Gets/sets an OLE DB <strong>Row</strong> object from/on this ADO <strong>Record</strong> object.</p></td>
</tr>
</tbody>
</table>


## Methods

None.

## Events

None.

## Remarks

Given an OLE DB **Row** object (pRow), the construction of an ADO **Record** object (), the construction of an ADO **Record** object (adoR), amounts to the following three basic operations:

1.  Create an ADO **Record** object:
    
    ```vb
        _RecordPtr adoR;
        adoRs.CreateInstance(__uuidof(_Record));
    ```

2.  Query the **IADORecordConstruction** interface on the **Record** object:
    
    ```vb
        adoRecordConstructionPtr adoRConstruct=NULL;
        adoR->QueryInterface(__uuidof(ADORecordConstruction),
                            (void**)&adoRConstruct);
    ```

3.  Call the **IADORecordConstruction::put\_Row** property method to set the OLE DB **Row** object on the ADO **Record** object:
    
    ```vb
        IUnknown *pUnk=NULL;
        pRow->QueryInterface(IID_IUnknown, (void**)&pUnk);
        adoRConstruct->put_Row(pUnk);
    ```
    
The resultant **adoR** object now represents the ADO **Record** object constructed from the OLE DB **Row** object.

An ADO **Record** object can also be constructed from the container of an OLE DB **Row** object.

## Requirements

**Version:** ADO 2.0 and later

**Library:** msado15.dll

**UUID:** 00000567-0000-0010-8000-00AA006D2EA4

