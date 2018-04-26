---
title: "Association TaskTimephasedData_Project (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: b9c7642b-1496-41a9-988c-fa40fd3a3877
description: "TaskTimephasedData_Project association relates task timephased data to its project."
---

# Association: TaskTimephasedData_Project (ProjectData service)

 **TaskTimephasedData_Project** association relates task timephased data to its project. 
  
## Definition

```XML
<Association Name="TaskTimephasedData_Project">
  <End Type="ReportingData.TaskTimephasedData" Role="TaskTimephasedData" Multiplicity="*" />
  <End Type="ReportingData.Project" Role="Project" Multiplicity="0..1" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**TaskTimephasedData_Project** <br/> |Identifies the two entity types that form the **TaskTimephasedData_Project** association.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **TaskTimephasedData_Project** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the TaskTimephasedData_Project association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**TaskTimephasedData** <br/> |[EntityType element: TaskTimephasedData](entitytype-tasktimephaseddata-projectdata-service.md) <br/> |**\*** <br/> |The collection of task timephased data in the reporting tables.  <br/> |
|**Project** <br/> |[EntityType element: Project](entitytype-project-projectdata-service.md) <br/> |**0..1** <br/> |The project object that is referenced in the **TaskTimephasedData_Project** association.  <br/> |
   
## Remarks

The **Project** navigation property in the **TaskTimephasedData** entity uses the **TaskTimephasedData_Project** association to query for a project that is associated with a collection of timephased data for tasks. 
  
## See also

#### Reference

[EntityType element: Project](entitytype-project-projectdata-service.md)
  
[EntityType element: TaskTimephasedData](entitytype-tasktimephaseddata-projectdata-service.md)

