---
title: "EntityType ProjectWorkflowStageData (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: a5028be5-d7c4-41cb-8f88-32f2a9bb6d13
description: "Contains the properties that define the reporting data for project workflow stage data in the ProjectData service."
---

# EntityType: ProjectWorkflowStageData (ProjectData service)

Contains the properties that define the reporting data for project workflow stage data in the **ProjectData** service. 
  
## Example

The following REST query uses the [ProjectWorkflowStageDataSet](entityset-projectworkflowstagedataset-projectdata-service.md) entity set and the **ProjectId** key to get the workflow stage data for the specified project. The query is all on one line. 
  
```
https://<pwa_url>/_api/ProjectData/ProjectWorkflowStageDataSet
    ?$filter=ProjectId eq guid'5263ee3e-66e6-e111-9fc9-00155d35d32e'

```

## Definition

```XML
<EntityType Name="ProjectWorkflowStageData">
  <Key>
    <PropertyRef Name="ProjectId" />
    <PropertyRef Name="StageId" />
  </Key>
  <Property Name="ProjectId" Type="Edm.Guid" Nullable="false" />
  . . .
  <NavigationProperty Name="Project" Relationship="ReportingData.Project_StagesInfo_ProjectWorkflowStageData_Project" ToRole="Project_StagesInfo" FromRole="ProjectWorkflowStageData_Project" />
</EntityType>
```

## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[ReportingData](schema-microsoft-office-project-server-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

Child elements are properties of project workflow stage data and navigation properties of that stage data. Attributes of the **Property** elements specify the property name and type, and whether the property can be a null value. The **NavigationProperty** element specifies project entities that are associated with project workflow stage data. A navigation property uses an **Association** element in a query for a related entity collection 
  
The **Key** elements specify the properties that are the primary keys for a query for project workflow stage data. **ProjectId** is the project GUID and **StageId** is the workflow stage GUID. 
  
### Property elements

The following table lists the **Property** elements for the **ProjectWorkflowStageData** entity. The **Name**, **Type**, and **Nullable** columns contain attribute values for each property. 
  
**Attribute values for the Property elements of ProjectWorkflowStageData**

|**Name**|**Type**|**Nullable**|**Description**|
|:-----|:-----|:-----|:-----|
|**LastModifiedDate** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The date and time that a workflow stage data was last updated.  <br/> |
|**LCID** <br/> |**Edm.Int32** <br/> |**false** <br/> |The locale identifier.  <br/> |
|**PhaseDescription** <br/> |**Edm.String** <br/> |**true** <br/> |The description for a workflow phase.  <br/> |
|**PhaseName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of a workflow phase.  <br/> |
|**ProjectId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID that identifies a project for workflow stage data.  <br/> |
|**ProjectName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the project.  <br/> |
|**StageCompletionDate** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The completion date and time of a workflow stage.  <br/> |
|**StageDescription** <br/> |**Edm.String** <br/> |**true** <br/> |The description of a workflow stage.  <br/> |
|**StageEntryDate** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The date and time that a workflow stage begins.  <br/> |
|**StageId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID of a workflow stage.  <br/> |
|**StageInformation** <br/> |**Edm.String** <br/> |**true** <br/> |Information for a workflow stage.  <br/> |
|**StageName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of a workflow stage.  <br/> |
|**StageOrder** <br/> |**Edm.Int32** <br/> |**false** <br/> |The order of a stage in a workflow.  <br/> |
|**StageStateDescription** <br/> |**Edm.String** <br/> |**true** <br/> |The description of the state of a workflow stage.  <br/> |
|**StageStatus** <br/> |**Edm.Int32** <br/> |**false** <br/> |The status of a workflow stage.  <br/> |
   
### NavigationProperty elements

The following table lists attribute values for the **NavigationProperty** element of the **ProjectWorkflowStageData** entity. The **Name** and **Relationship** columns contain attribute values. 
  
The **Relationship** attribute has two pairs of names; each pair of names indicates a navigation direction. The first pair starts with the entity type that has the primary, or starting, role in the navigation. The second pair starts with the entity type that has the secondary, or dependent, role in the navigation. For the **Project** navigation property, the primary type is **Project**, and the secondary type is **ProjectWorkflowStageData**. For this type of navigation, the **FromRole** is **Project_StagesInfo**, and the **ToRole** is **ProjectWorkflowStageData_Project**.
  
**Attribute values for the NavigationProperty elements**

|**Name**|**Relationship**|**Description**|
|:-----|:-----|:-----|
|**Project** <br/> |[Project_StagesInfo_ProjectWorkflowStageData_Project](association-project_stagesinfo_projectworkflowstagedata_project-projectdata-serv.md) <br/> |Establishes navigation from a project to a collection of project workflow stage information and from a collection of project workflow stage data to a project.  <br/> |
   
## See also

#### Reference

[ProjectWorkflowStageDataSet](entityset-projectworkflowstagedataset-projectdata-service.md)
  
[ReportingData](schema-microsoft-office-project-server-projectdata-service.md)
#### Concepts

[Querying OData feeds for Project reporting data](querying-odata-feeds-for-project-reporting-data.md)

