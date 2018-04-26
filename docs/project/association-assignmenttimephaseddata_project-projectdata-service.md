---
title: "Association AssignmentTimephasedData_Project (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: edbf51cf-de02-49ce-b577-281845703923
description: "The AssignmentTimephasedData_Project association relates assignment timephased data to a project."
---

# Association: AssignmentTimephasedData_Project (ProjectData service)

The **AssignmentTimephasedData_Project** association relates assignment timephased data to a project. 
  
## Definition

```XML
<Association Name="AssignmentTimephasedData_Project">
  <End Type="ReportingData.Project" Role="Project" Multiplicity="0..1" />
  <End Type="ReportingData.AssignmentTimephasedData" Role="AssignmentTimephasedData" Multiplicity="*" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**AssignmentTimephasedData_Project** <br/> |Identifies the two entity types that form the **AssignmentTimephasedData_Project** association.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **AssignmentTimephasedData_Project** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the AssignmentTimephasedData_Project association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**AssignmentTimephasedData** <br/> |[EntityType element: AssignmentTimephasedData](entitytype-assignmenttimephaseddata-projectdata-service.md) <br/> |**\*** <br/> |The collection of assignment timephased data in the reporting tables.  <br/> |
|**Project** <br/> |[EntityType element: Project](entitytype-project-projectdata-service.md) <br/> |**0..1** <br/> |The project object that is being referenced in the **AssignmentTimephasedData_Project** association.  <br/> |
   
## Remarks

The **Project** navigation property in the **AssignmentTimephasedData** entity uses the **AssignmentTimephasedData_Project** association to query for a project that is associated with a collection of assignment timephased data. 
  
## See also

#### Reference

[EntityType element: AssignmentTimephasedData](entitytype-assignmenttimephaseddata-projectdata-service.md)
  
[EntityType element: Project](entitytype-project-projectdata-service.md)

