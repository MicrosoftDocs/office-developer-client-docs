---
title: "Association Project_Assignments_Assignment_Project (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: d2efaa4d-adaa-4b20-bb8f-7ced043661b2
description: "The Project_Assignments_Assignment_Project association relates a project to the assignments that it contains and relates assignments to a project."
---

# Association: Project_Assignments_Assignment_Project (ProjectData service)

The **Project_Assignments_Assignment_Project** association relates a project to the assignments that it contains and relates assignments to a project. 
  
## Definition

```XML
<Association Name="Project_Assignments_Assignment_Project">
  <End Type="ReportingData.Assignment" Role="Assignment_Project" Multiplicity="*" />
  <End Type="ReportingData.Project" Role="Project_Assignments" Multiplicity="0..1" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**Project_Assignments_Assignment_Project** <br/> |Identifies the entity types and the navigation properties that form the two-way association for projects and assignments. In the first half of the name, **Project** is the entity type and **Assignments** is the navigation property. In the second half of the name, **Assignment** is the entity type and **Project** is the navigation property.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **Project_Assignments_Assignment_Project** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the Project_Assignments association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**Project_Assignments** <br/> |[EntityType element: Project](entitytype-project-projectdata-service.md) <br/> |**0..1** <br/> |There is one project entity that corresponds to a collection of assignments.  <br/> |
|**Assignment_Project** <br/> |[EntityType element: Assignment](entitytype-assignment-projectdata-service.md) <br/> |**\*** <br/> |There can be many assignment entities that correspond with a project.  <br/> |
   
## Remarks

One end of the association is the **Project** entity, and the other end is the **Assignment** entity. The **Project** entity type contains the **Assignments** navigation property, where the **FromRole** defines **Project_Assignments** as the start of the association to get the collection of assignments in a project. Similarly, the **Assignment** entity type contains the **Project** navigation property, where the **FromRole** defines **Assignment_Project** as the start of the association to get the project that that is associated with a collection of assignments. 
  
## See also

#### Reference

[EntityType element: Assignment](entitytype-assignment-projectdata-service.md)
  
[EntityType element: Project](entitytype-project-projectdata-service.md)

