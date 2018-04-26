---
title: "EntityType RiskTaskAssociation (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: be513f90-4808-4a5c-a200-168ce3d8e545
description: "Contains the properties that define the reporting data for a risk task association in the ProjectData service."
---

# EntityType: RiskTaskAssociation (ProjectData service)

Contains the properties that define the reporting data for a risk task association in the **ProjectData** service. 
  
## Example

The following REST query uses the [RiskTaskAssociations](entityset-risktaskassociations-projectdata-service.md) entity set and the **ProjectId** key to get the risk task associations that correspond to a specified project. The query is all on one line. 
  
```
http://<pwa_url>/_api/ProjectData/RiskTaskAssociations
    ?$filter=ProjectId eq guid'cb7f4bfa-e3bb-e111-8b9e-00155d34c815'
```

## Definition

```XML
<EntityType Name="RiskTaskAssociation">
  <Key>
    <PropertyRef Name="ProjectId" />
    <PropertyRef Name="RiskId" />
    <PropertyRef Name="TaskId" />
    <PropertyRef Name="RelationshipType" />
  </Key>
  <Property Name="ProjectId" Type="Edm.Guid" Nullable="false" />
. . .
  <NavigationProperty Name="Risk" Relationship="ReportingData.RiskTaskAssociation_Risk" ToRole="Risk" FromRole="RiskTaskAssociation" />
 . . .
</EntityType>
```

## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[ReportingData](schema-microsoft-office-project-server-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

Child elements are properties of a risk task association and navigation properties of that risk task association. Attributes of the **Property** elements specify the property name and type, and whether the property can be a null value. The **NavigationProperty** elements specify collections of entities, such as projects and related projects, that are associated with a risk task association. A navigation property uses an **Association** element in a query for a related entity or collection 
  
The **Key** elements specify the properties that are the primary keys for a risk task association query. **ProjectId** is the GUID of the project, **RiskId** is the GUID of the risk, **TaskId** is the GUID of the task, and **RelationshipType** is the enumerated type of the association. 
  
### Property elements

The following table lists the values of the **Property** elements for the **RiskTaskAssociation** entity. The **Name**, **Type**, and **Nullable** columns contain attribute values for each property. 
  
**Attribute values for the Property elements of RiskTaskAssociation**

|**Name**|**Type**|**Nullable**|**Description**|
|:-----|:-----|:-----|:-----|
|**ProjectId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The project GUID.  <br/> |
|**ProjectName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of a project.  <br/> |
|**RelatedProjectId** <br/> |**Edm.Guid** <br/> |**false** <br/> |The GUID of a related project.  <br/> |
|**RelatedProjectName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of a related project.  <br/> |
|**RelationshipType** <br/> |**Edm.Int32** <br/> |**false** <br/> |**Key**         The enumerated type of a relationship.  <br/> |
|**RiskId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID of a risk.  <br/> |
|**TaskId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID of a task.  <br/> |
|**TaskName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of a task.  <br/> |
|**Title** <br/> |**Edm.String** <br/> |**true** <br/> |The title of a risk.  <br/> |
   
### NavigationProperty elements

The following table lists attribute values for the **NavigationProperty** elements of the **RiskTaskAssociation** entity. The **Name** and **Relationship** columns contain attribute values for each navigation property. 
  
Each **Relationship** attribute contains a pair of names. The first name in the pair is the primary entity type in the navigation. The second name in the pair is the secondary entity type in the navigation. For example, in the **Project** navigation property relationship, **RiskTaskAssociation** is the primary entity type and **Project** is the secondary entity type. 
  
**Attribute values for the NavigationProperty elements**

|**Name**|**Relationship**|**Description**|
|:-----|:-----|:-----|
|**Project** <br/> |[RiskTaskAssociation_Project](association-risktaskassociation_project-projectdata-service.md) <br/> |Establishes navigation from a risk task association to a project.  <br/> |
|**RelatedProject** <br/> |[RiskTaskAssociation_RelatedProject](association-risktaskassociation_relatedproject-projectdata-service.md) <br/> |Establishes navigation from a risk task association to a related project.  <br/> |
|**Risk** <br/> |[RiskTaskAssociation_Risk](association-risktaskassociation_risk-projectdata-service.md) <br/> |Establishes navigation from a risk task association to a risk.  <br/> |
|**Task** <br/> |[RiskTaskAssociation_Task](association-risktaskassociation_task-projectdata-service.md) <br/> |Establishes navigation from a risk task association to a task.  <br/> |
   
## See also

#### Reference

[RiskTaskAssociations](entityset-risktaskassociations-projectdata-service.md)
  
[ReportingData](schema-microsoft-office-project-server-projectdata-service.md)
#### Concepts

[Querying OData feeds for Project reporting data](querying-odata-feeds-for-project-reporting-data.md)

