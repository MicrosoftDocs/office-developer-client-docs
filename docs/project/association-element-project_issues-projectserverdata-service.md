---
title: "Association element Project_Issues (ProjectServerData service)"

 
manager: luken
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 59a35f88-b862-4e3c-a2af-451f63fe54fe
description: "The Project_Issues_Issue_Project association relates a project to the issues that it contains and relates a collection of issues to its project."
---

# Association element: Project_Issues (ProjectServerData service)

The **Project_Issues_Issue_Project** association relates a project to the issues that it contains and relates a collection of issues to its project. 
  
## Definition

```XML
<Association Name="Project_Issues_Issue_Project">
  <End Type="ReportingData.Issue" Role="Issue_Project" Multiplicity="*" />
  <End Type="ReportingData.Project" Role="Project_Issues" Multiplicity="0..1" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**Project_Issues_Issue_Project** <br/> |Identifies the entity types and the navigation properties that form the two-way association for projects and issues. In the first half of the name, **Project** is the entity type and **Issues** is the navigation property. In the second half of the name, **Issue** is the entity type and **Project** is the navigation property.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **Project_Issues_Issue_Project** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the Project_Issues association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**Project_Issues** <br/> |[EntityType element: Project](entitytype-project-projectdata-service.md) <br/> |**0..1** <br/> |There is one project entity that corresponds to a collection of issues.  <br/> |
|**Issue_Project** <br/> |[EntityType element: Issue](entitytype-issue-projectdata-service.md) <br/> |**\*** <br/> |There can be many issue entities that correspond with a project.  <br/> |
   
## Remarks

One end of the association is the **Project** entity, and the other end is the **Issue** entity. The **Project** entity type contains the **Issues** navigation property, where the **FromRole** defines **Project_Issues** as the start of the association to get the collection of issues in a project. Similarly, the **Issue** entity type contains the **Project** navigation property, where the **FromRole** defines **Issue_Project** as the start of the association to get the project that is associated with a collection of issues. 
  
## See also

#### Reference

[EntityType element: Issue](entitytype-issue-projectdata-service.md)
  
[EntityType element: Project](entitytype-project-projectdata-service.md)

