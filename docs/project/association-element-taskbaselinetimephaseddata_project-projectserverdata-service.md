---
title: "Association element TaskBaselineTimephasedData_Project (ProjectServerData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 1b969ade-7a4d-4c43-9769-1a0f3aa93632
description: "The TaskBaselineTimephasedData_Project association relates a project to the task baseline timephased data that it contains."
---

# Association element: TaskBaselineTimephasedData_Project (ProjectServerData service)

The **TaskBaselineTimephasedData_Project** association relates a project to the task baseline timephased data that it contains. 
  
## Definition

```XML
<Association Name="TaskBaselineTimephasedData_Project">
  <End Type="ReportingData.TaskBaselineTimephasedData" Role="TaskBaselineTimephasedData" Multiplicity="*" />
  <End Type="ReportingData.Project" Role="Project" Multiplicity="0..1" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**TaskBaselineTimephasedData_Project** <br/> |Identifies the two entity types that form the **TaskBaselineTimephasedData_Project** association.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **TaskBaselineTimephasedData_Project** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the TaskBaselineTimephasedData_Project association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**TaskBaselineTimephasedData** <br/> |[EntityType element: TaskBaselineTimephasedData](entitytype-taskbaselinetimephaseddata-projectdata-service.md) <br/> |**\*** <br/> |The collection of timephased data for task baselines, in the reporting tables.  <br/> |
|**Project** <br/> |[EntityType element: Project](entitytype-project-projectdata-service.md) <br/> |**0..1** <br/> |The project object that is referenced in the **TaskBaselineTimephasedData_Project** association.  <br/> |
   
## Remarks

The **Project** navigation property in the **TaskBaselineTimephasedData** entity uses the **TaskBaselineTimephasedData_Project** association to query for a project that is associated with a collection of task baseline timephased data. 
  
## See also

#### Reference

[EntityType element: Project](entitytype-project-projectdata-service.md)
  
[EntityType element: TaskBaselineTimephasedData](entitytype-taskbaselinetimephaseddata-projectdata-service.md)

