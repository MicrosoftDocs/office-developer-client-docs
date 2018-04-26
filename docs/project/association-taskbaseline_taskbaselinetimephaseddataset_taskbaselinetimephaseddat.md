---
title: "Association TaskBaseline_TaskBaselineTimephasedDataSet_TaskBaselineTimephasedData_TaskBaselines (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: dfa49e7a-57d6-413d-9a07-a765332e9c2b
description: "The TaskBaseline_TaskBaselineTimephasedDataSet_TaskBaselineTimephasedData_TaskBaselines association relates a task baseline to task baseline timephased data and relates task baseline timephased data to task baselines."
---

# Association: TaskBaseline_TaskBaselineTimephasedDataSet_TaskBaselineTimephasedData_TaskBaselines (ProjectData service)

The **TaskBaseline_TaskBaselineTimephasedDataSet_TaskBaselineTimephasedData_TaskBaselines** association relates a task baseline to task baseline timephased data and relates task baseline timephased data to task baselines. 
  
## Definition

```XML
<Association Name="TaskBaseline_TaskBaselineTimephasedDataSet_TaskBaselineTimephasedData_TaskBaselines">
  <End Type="ReportingData.TaskBaselineTimephasedData" Role="TaskBaselineTimephasedData_TaskBaselines" Multiplicity="*" />
  <End Type="ReportingData.TaskBaseline" Role="TaskBaseline_TaskBaselineTimephasedDataSet" Multiplicity="*" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**TaskBaseline_TaskBaselineTimephasedDataSet_TaskBaselineTimephasedData_TaskBaselines** <br/> |Identifies the entity types and the navigation properties that form the two-way association task baselines and task baseline timephased data. In the first half of the name, **TaskBaseline** is the entity type and **TaskBaselineTimephasedDataSet** is the navigation property. In the second half of the name, **TaskBaselineTimephasedData** is the entity type and **TaskBaselines** is the navigation property.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **TaskBaseline_TaskBaselineTimephasedDataSet_TaskBaselineTimephasedData_TaskBaselines** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the TaskBaseline_TaskBaselineTimephasedDataSet_TaskBaselineTimephasedData_TaskBaselines association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**TaskBaseline_TaskBaselineTimephasedDataSet** <br/> |[EntityType element: TaskBaseline](entitytype-taskbaseline-projectdata-service.md) <br/> |**\*** <br/> |There can be many task baseline entities that correspond with task baseline timephased dataset entities.  <br/> |
|**TaskBaselineTimephasedData_TaskBaselines** <br/> |[EntityType element: TaskBaselineTimephasedData](entitytype-taskbaselinetimephaseddata-projectdata-service.md) <br/> |**\*** <br/> |There can be many task baseline timephased data entities that correspond to task baselines.  <br/> |
   
## Remarks

One end of the association is the **TaskBaseline** entity, and the other end is the **TaskBaselineTimephasedData** entity. The **TaskBaseline** entity type contains the **TaskBaselineTimephasedDataSet** navigation property, where the **FromRole** defines **TaskBaseline_TaskBaselineTimephasedDataSet** as the start of the association to get the collection of task baselines that is associated with task baseline timephased data. Similarly, the **TaskBaselineTimephasedData** entity type contains the **TaskBaselines** navigation property, where the **FromRole** defines **TaskBaselineTimephasedData_TaskBaselines** as the start of the association to get the collection of task baselines that are associated with task baseline timephased data. 
  
## See also

#### Reference

[EntityType element: TaskBaseline](entitytype-taskbaseline-projectdata-service.md)
  
[EntityType element: TaskBaselineTimephasedData](entitytype-taskbaselinetimephaseddata-projectdata-service.md)

