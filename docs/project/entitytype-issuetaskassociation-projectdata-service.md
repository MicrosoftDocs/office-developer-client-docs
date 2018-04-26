---
title: "EntityType IssueTaskAssociation (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 78b13b57-e8b6-4f34-96a8-148970cfcce9
description: "Contains the properties that define the reporting data for an issue task association in the ProjectData service."
---

# EntityType: IssueTaskAssociation (ProjectData service)

Contains the properties that define the reporting data for an issue task association in the **ProjectData** service. 
  
## Example

The following REST query uses the [IssueTaskAssociations](entityset-issuetaskassociations-projectdata-service.md) entity set and the **TaskId** and **RelationshipType** keys to get the issue task associations for the specified task and relationship type. The query is all on one line. 
  
```
http://<pwa_url>/_api/ProjectData/IssueTaskAssociations
    ?$filter=TaskId eq guid'91325620-ccbb-e111-82d9-00155d4a4108'
    and RelationshipType eq 2
```

## Definition

```XML
<EntityType Name="IssueTaskAssociation">
  <Key>
    <PropertyRef Name="ProjectId" />
    <PropertyRef Name="IssueId" />
    <PropertyRef Name="TaskId" />
    <PropertyRef Name="RelationshipType" />
  </Key>
  <Property Name="ProjectId" Type="Edm.Guid" Nullable="false" />
 . . .
  <NavigationProperty Name="Issue" Relationship="ReportingData.IssueTaskAssociation_Issue" ToRole="Issue" FromRole="IssueTaskAssociation" />
 . . .
</EntityType>

```

## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[ReportingData](schema-microsoft-office-project-server-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

Child elements are properties of an issue task association and navigation properties of that issue task association. Attributes of the **Property** elements specify the property name and type, and whether the property can be a null value. The **NavigationProperty** elements specify collections of entities, such as tasks and projects, that are associated with an issue task association. A navigation property uses an **Association** element in a query for a related entity or collection 
  
The **Key** elements specify the properties that are the primary keys for an issue task association query. **ProjectId** is the project GUID, **IssueId** is the GUID of the issue, **TaskId** is the GUID of the task, and **RelationshipType** is the enumerated type of the association. 
  
### Property elements

The following table lists the values of the **Property** elements for the **IssueTaskAssociation** entity. The **Name**, **Type**, and **Nullable** columns contain attribute values for each property. 
  
> [!NOTE]
> In the **ProjectData** schema, if the **Nullable** attribute is missing, the default value is **true**. 
  
**Attribute values for the Property elements of IssueTaskAssociation**

|**Name**|**Type**|**Nullable**|**Description**|
|:-----|:-----|:-----|:-----|
|**IssueId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID that identifies an issue.  <br/> |
|**ProjectId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID that identifies a project.  <br/> |
|**ProjectName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of a project.  <br/> |
|**RelatedProjectId** <br/> |**Edm.Guid** <br/> |**false** <br/> |The GUID that identifies a related project.  <br/> |
|**RelatedProjectName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of a related project.  <br/> |
|**RelationshipType** <br/> |**Edm.Int32** <br/> |**false** <br/> |**Key**         An enumeration that indicates a type of entity relationship.  <br/> |
|**TaskId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID of a task.  <br/> |
|**TaskName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of a task.  <br/> |
|**Title** <br/> |**Edm.String** <br/> |**true** <br/> |The title of the issue.  <br/> |
   
### NavigationProperty elements

The following table lists attribute values for the **NavigationProperty** elements of the **IssueTaskAssocation** entity. The **Name** and **Relationship** columns contain attribute values for each navigation property. 
  
Each **Relationship** attribute contains a pair of names. The first name in the pair is the primary entity type in the navigation. The second name in the pair is the secondary entity type in the navigation. For example, in the **Issue** navigation property relationship, **IssueTaskAssociation** is the primary entity type and **Issue** is the secondary entity type. 
  
**Attribute values for the NavigationProperty elements**

|**Name**|**Relationship**|**Description**|
|:-----|:-----|:-----|
|**Issue** <br/> |[IssueTaskAssociation_Issue](association-issuetaskassociation_issue-projectdata-service.md) <br/> |Establishes navigation from an issue task association to an issue.  <br/> |
|**Project** <br/> |[IssueTaskAssociation_Project](association-issuetaskassociation_project-projectdata-service.md) <br/> |Establishes navigation from an issue task assocation to a project.  <br/> |
|**RelatedProject** <br/> |[IssueTaskAssociation_RelatedProject](association-issuetaskassociation_relatedproject-projectdata-service.md) <br/> |Establishes navigation from an issue task association to a related project.  <br/> |
|**Task** <br/> |[IssueTaskAssociation_Task](association-issuetaskassociation_task-projectdata-service.md) <br/> |Establishes navigation from an issue task assocation to a task.  <br/> |
   
## See also

#### Reference

[IssueTaskAssociations](entityset-issuetaskassociations-projectdata-service.md)
  
[ReportingData](schema-microsoft-office-project-server-projectdata-service.md)
#### Concepts

[Querying OData feeds for Project reporting data](querying-odata-feeds-for-project-reporting-data.md)

