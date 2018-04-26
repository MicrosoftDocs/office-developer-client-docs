---
title: "Association Project_StagesInfo_ProjectWorkflowStageData_Project (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 34485d06-c5bd-4df2-ba68-c0cfb4ac2919
description: "The Project_StagesInfo_ProjectWorkflowStageData_Project association relates a project to workflow stage information and relates workflow stage data to a project."
---

# Association: Project_StagesInfo_ProjectWorkflowStageData_Project (ProjectData service)

The **Project_StagesInfo_ProjectWorkflowStageData_Project** association relates a project to workflow stage information and relates workflow stage data to a project. 
  
## Definition

```XML
<Association Name="Project_StagesInfo_ProjectWorkflowStageData_Project">
  <End Type="ReportingData.ProjectWorkflowStageData" Role="ProjectWorkflowStageData_Project" Multiplicity="*" />
  <End Type="ReportingData.Project" Role="Project_StagesInfo" Multiplicity="0..1" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**Project_StagesInfo_ProjectWorkflowStageData_Project** <br/> |Identifies the entity types and the navigation properties that form the two-way association for projects and workflow stages. In the first half of the name, **Project** is the entity type and **StagesInfo** is the navigation property. In the second half of the name, **ProjectWorkflowStageData** is the entity type and **Project** is the navigation property.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **Project_StagesInfo_ProjectWorkflowStageData_Project** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the Project_StagesInfo association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**Project_StagesInfo** <br/> |[EntityType element: Project](entitytype-project-projectdata-service.md) <br/> |**0..1** <br/> |There is one project entity that corresponds to a collection of workflow stage information entities.  <br/> |
|**ProjectWorkflowStageData_Project** <br/> |[EntityType element: ProjectWorkflowStageData](entitytype-projectworkflowstagedata-projectdata-service.md) <br/> |**\*** <br/> |There can be many workflow stage data entities in a project.  <br/> |
   
## Remarks

One end of the association is the **Project** entity, and the other end is the **ProjectWorkflowStageData** entity. The **Project** entity type contains the **StagesInfo** navigation property, where the **FromRole** defines **Project_StagesInfo** as the start of the association to get the collection of workflow stage information entities that are associated with a project. Similarly, the **ProjectWorkflowStageData** entity type contains the **Project** navigation property, where the **FromRole** defines **ProjectWorkflowStageData_Project** as the start of the association to get the project that is associated with workflow stage data entities. 
  
## See also

#### Reference

[EntityType element: Project](entitytype-project-projectdata-service.md)
  
[EntityType element: ProjectWorkflowStageData](entitytype-projectworkflowstagedata-projectdata-service.md)

