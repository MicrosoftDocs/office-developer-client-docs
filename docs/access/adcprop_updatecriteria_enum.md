---
title: "ADCPROP_UPDATECRITERIA_ENUM"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 70da63fa-fa75-9bb4-683d-0fcb4c4a2934
---

# ADCPROP_UPDATECRITERIA_ENUM

Specifies which fields can be used to detect conflicts during an optimistic update of a row of the data source with a [Recordset](recordset-object-ado.md) object. 
  
Use these constants with the **Recordset** " **Update Criteria** " dynamic property, which is referenced in the [ADO Dynamic Property Index](ado-dynamic-property-index.md) and documented in the [Microsoft Cursor Service for OLE DB](microsoft-cursor-service-for-ole-db-ado-service-component.md) documentation. 
  
|**Constant**|**Value**|**Description**|
|:-----|:-----|:-----|
|**adCriteriaAllCols** <br/> |1  <br/> |Detects conflicts if any column of the data source row has been changed.  <br/> |
|**adCriteriaKey** <br/> |0  <br/> |Detects conflicts if the key column of the data source row has been changed, which means that the row has been deleted.  <br/> |
|**adCriteriaTimeStamp** <br/> |3  <br/> |Detects conflicts if the timestamp of the data source row has been changed, which means the row has been accessed after the **Recordset** was obtained.  <br/> |
|**adCriteriaUpdCols** <br/> |2  <br/> |Detects conflicts if any of the columns of the data source row that correspond to updated fields of the **Recordset** have been changed.  <br/> |
   
 **ADO/WFC Equivalent**
  
Package: **com.ms.wfc.data**
  
|**Constant**|
|:-----|
|AdoEnums.AdcPropUpdateCriteria.ALLCOLS  <br/> |
|AdoEnums.AdcPropUpdateCriteria.KEY  <br/> |
|AdoEnums.AdcPropUpdateCriteria.TIMESTAMP  <br/> |
|AdoEnums.AdcPropUpdateCriteria.UPDCOLS  <br/> |
   

