---
title: "ADORecordConstruction Interface (ADO)"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 3f0afbdb-f1c4-e44e-7c0f-a0c4cee554a7
---

# ADORecordConstruction Interface (ADO)

The **ADORecordConstruction** interface is used to construct an ADO **Record** object from an OLE DB **Row** object in a C/C++ application. 
  
This interface supports the following properties:
  
## Properties

|||
|:-----|:-----|
|[ParentRow](parentrow-property-ado.md) <br/> |Write-only.           Sets the container of an OLE DB **Row** object on this ADO **Record** object.  <br/> |
|[Row](row-property-ado.md) <br/> |Read/Write.           Gets/sets an OLE DB **Row** object from/on this ADO **Record** object.  <br/> |
   
## Methods

None.
  
## Events

None.
  
## Remarks

Given an OLE DB **Row** object (  `pRow`), the construction of an ADO **Record** object (), the construction of an ADO **Record** object (  `adoR`), amounts to the following three basic operations:
  
1. Create an ADO **Record** object: 
    
  ```
  _RecordPtr adoR;
  adoRs.CreateInstance(__uuidof(_Record));
  
  ```

2. Query the **IADORecordConstruction** interface on the **Record** object: 
    
  ```
  adoRecordConstructionPtr adoRConstruct=NULL;
  adoR->QueryInterface(__uuidof(ADORecordConstruction),
                      (void**)&amp;adoRConstruct);
  
  ```

3. Call the **IADORecordConstruction::put_Row** property method to set the OLE DB **Row** object on the ADO **Record** object: 
    
  ```
  IUnknown *pUnk=NULL;
  pRow->QueryInterface(IID_IUnknown, (void**)&amp;pUnk);
  adoRConstruct->put_Row(pUnk);
  
  ```

The resultant **adoR** object now represents the ADO **Record** object constructed from the OLE DB **Row** object. 
  
An ADO **Record** object can also be constructed from the container of an OLE DB **Row** object. 
  
## Requirements

 **Version:** ADO 2.0 and later 
  
 **Library:** msado15.dll 
  
 **UUID:** 00000567-0000-0010-8000-00AA006D2EA4 
  

