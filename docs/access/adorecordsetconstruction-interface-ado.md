---
title: "ADORecordsetConstruction Interface (ADO)"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 2b53aa6e-3b6f-a996-3967-534215fd586c
---

# ADORecordsetConstruction Interface (ADO)

The **ADORecordsetConstruction** interface is used to construct an ADO **Recordset** object from an OLE DB **Rowset** object in a C/C++ application. 
  
This interface supports the following properties:
  
## Properties

|||
|:-----|:-----|
|[Chapter](chapter-property-ado.md) <br/> |Read/Write.           Gets/sets an OLE DB **Chapter** object from/on this ADO **Recordset** object.  <br/> |
|[RowPosition](rowposition-property-ado.md) <br/> |Read/Write.           Gets/sets an OLE DB **RowPosition** object from/on this ADO **Recordset** object.  <br/> |
|[Rowset](rowset-property-ado.md) <br/> |Read/Write.           Gets/sets an OLE DB **Rowset** object from/on this ADO **Recordset** object.  <br/> |
   
## Methods

None.
  
## Events

None.
  
## Remarks

Given an OLE DB **Rowset** object (  `pRowset`), the construction of an ADO **Recordset** object (), the construction of an ADO **Recordset** object (  `adoRs`) amounts to the following three basic operations:
  
1. Create an ADO **Recordset** object: 
    
  ```
  Recordset20Ptr adoRs;
  adoRs.CreateInstance(__uuidof(Recordset));
  
  ```

2. Query the **IADORecordsetConstruction** interface on the **Recordset** object: 
    
  ```
  adoRecordsetConstructionPtr adoRsConstruct=NULL;
  adoRs->QueryInterface(__uuidof(ADORecordsetConstruction),
                       (void**)&amp;adoRsConstruct);
  
  ```

3. Call the  `IADORecordsetConstruction::put_Rowset` property method to set the OLE DB  `Rowset` object on the ADO  `Recordset` object: 
    
  ```
  IUnknown *pUnk=NULL;
  pRowset->QueryInterface(IID_IUnknown, (void**)&amp;pUnk);
  adoRsConstruct->put_Rowset(pUnk);
  
  ```

The resultant object now represents the ADO **Recordset** object constructed from the OLE DB **Rowset** object. 
  
You can also construct an ADO **Recordset** object from an OLE DB **Chapter** or **RowPosition** object. 
  
## Requirements

 **Version:** ADO 2.0 and later 
  
 **Library:** msado15.dll 
  
 **UUID:** 00000283-0000-0010-8000-00AA006D2EA4 
  

