---
title: "Association AssignmentBaseline_AssignmentBaselineTimephasedDataSet_AssignmentBaselineTimephasedData_Baseline (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 0412c222-fbee-4d0d-9fac-e8fee5c7b6cc
description: "The AssignmentBaseline_AssignmentBaselineTimephasedDataSet_AssignmentBaselineTimephasedData_Baseline association relates an assignment baseline to assignment baseline timephased data and relates assignment baseline timephased data to its baseline."
---

# Association: AssignmentBaseline_AssignmentBaselineTimephasedDataSet_AssignmentBaselineTimephasedData_Baseline (ProjectData service)

The **AssignmentBaseline_AssignmentBaselineTimephasedDataSet_AssignmentBaselineTimephasedData_Baseline** association relates an assignment baseline to assignment baseline timephased data and relates assignment baseline timephased data to its baseline. 
  
## Definition

```XML
<Association Name="AssignmentBaseline_AssignmentBaselineTimephasedDataSet_AssignmentBaselineTimephasedData_Baseline">
  <End Type="ReportingData.AssignmentBaselineTimephasedData" Role="AssignmentBaselineTimephasedData_Baseline" Multiplicity="*" />
  <End Type="ReportingData.AssignmentBaseline" Role="AssignmentBaseline_AssignmentBaselineTimephasedDataSet" Multiplicity="0..1" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**AssignmentBaseline_AssignmentBaselineTimephasedDataSet_AssignmentBaselineTimephasedData_Baseline** <br/> |Identifies the entity types and the navigation properties that form the two-way association for assignment baselines and assignment baseline timephased data. In the first half of the name, **AssignmentBaseline** is the entity type and **AssignmentBaselineTimephasedDataSet** is the navigation property. In the second half of the name, **AssignmentBaselineTimephasedData** is the entity type and **Baseline** is the navigation property.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **AssignmentBaseline_AssignmentBaselineTimephasedDataSet_AssignmentBaselineTimephasedData_Baseline** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the AssignmentBaseline_AssignmentBaselineTimephasedDataSet association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**AssignmentBaseline_AssignmentBaselineTimephasedDataSet** <br/> |[EntityType element: AssignmentBaseline](entitytype-assignmentbaseline-projectdata-service.md) <br/> |**0..1** <br/> |There is one assignment baseline entity that corresponds to an assignment baseline timephased dataset.  <br/> |
|**AssignmentBaselineTimephasedData_Baseline** <br/> |[EntityType element: AssignmentBaselineTimephasedData](entitytype-assignmentbaselinetimephaseddata-projectdata-service.md) <br/> |**\*** <br/> |There can be multiple assignment baseline timephased data entities for a baseline.  <br/> |
   
## Remarks

One end of the association is the **AssignmentBaseline** entity, and the other end is the **AssignmentBaselineTimephasedData** entity. The **AssignmentBaseline** entity type contains the **AssignmentBaselineTimephasedDataSet** navigation property, where the **FromRole** defines **AssignmentBaseline_AssignmentBaselineTimephasedDataSet** as the start of the association to get the assignment timephased data that is associated with an assignment baseline. Similarly, the **AssignmentBaselineTimephasedData** entity type contains the **Baseline** navigation property, where the **FromRole** defines **AssignmentBaselineTimephasedData_Baseline** as the start of the association to get the baseline that corresponds to a set of assignment timephased baseline data. 
  
## See also

#### Reference

[EntityType element: AssignmentBaseline](entitytype-assignmentbaseline-projectdata-service.md)
  
[EntityType element: AssignmentBaselineTimephasedData](entitytype-assignmentbaselinetimephaseddata-projectdata-service.md)

