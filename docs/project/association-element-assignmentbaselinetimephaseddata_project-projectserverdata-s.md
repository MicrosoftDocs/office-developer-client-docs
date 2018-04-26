---
title: "Association element AssignmentBaselineTimephasedData_Project (ProjectServerData service)"

 
manager: luken
ms.date: 3/9/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: b61e7a7e-be40-436f-95a6-1d4b0f2d2a3d
description: "The AssignmentBaselineTimephasedData_Project association relates assignment baseline timephased data to a project."
---

# Association element: AssignmentBaselineTimephasedData_Project (ProjectServerData service)

The **AssignmentBaselineTimephasedData_Project** association relates assignment baseline timephased data to a project. 
  
## Definition

```XML
<Association Name="AssignmentBaselineTimephasedData_Project">
  <End Type="ReportingData.Project" Role="Project" Multiplicity="0..1" />
  <End Type="ReportingData.AssignmentBaselineTimephasedData" Role="AssignmentBaselineTimephasedData" Multiplicity="*" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**AssignmentBaselineTimephasedData_Project** <br/> |Identifies the two entity types that form the **AssignmentBaselineTimephasedData_Project** association.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **AssignmentBaselineTimephasedData_Project** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the AssignmentBaselineTimephasedData_Project association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**AssignmentBaselineTimephasedData** <br/> |[EntityType element: AssignmentBaselineTimephasedData](entitytype-assignmentbaselinetimephaseddata-projectdata-service.md) <br/> |**\*** <br/> |The collection of timephased data for assignment baselines, in the reporting tables.  <br/> |
|**Project** <br/> |[EntityType element: Project](entitytype-project-projectdata-service.md) <br/> |**0..1** <br/> |The project object that is being referenced in in the **AssignmentBaselineTimephasedData_Project** association.  <br/> |
   
## Remarks

The **Project** navigation property in the **AssignmentBaselineTimephasedData** entity uses the **AssignmentBaselineTimephasedData_Project** association to query for a project that is associated with a collection of timephased data for assignment baselines. 
  
## See also

#### Reference

[EntityType element: AssignmentBaselineTimephasedData](entitytype-assignmentbaselinetimephaseddata-projectdata-service.md)
  
[EntityType element: Project](entitytype-project-projectdata-service.md)

