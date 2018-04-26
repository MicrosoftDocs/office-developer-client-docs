---
title: "EntityType Issue (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: 07d76c59-20d7-47db-8126-52cdc29f4e69
description: "Contains the properties that define the reporting data for an issue in the ProjectData service."
---

# EntityType: Issue (ProjectData service)

Contains the properties that define the reporting data for an issue in the **ProjectData** service. 
  
## Example

The following REST query uses the [Issues](entityset-issues-projectdata-service.md) entity set and the **ProjectId** key to get the issues for the specified project. The query is all on one line. 
  
```
http://<pwa_url>/_api/ProjectData/Issues
    ?$filter=ProjectId eq guid'4fbb36d6-97bc-e111-a7e3-00155d4a5608'
```

## Definition

```XML
<EntityType Name="Issue">
  <Key>
    <PropertyRef Name="ProjectId" />
    <PropertyRef Name="IssueId" />
  </Key>
  <Property Name="ProjectId" Type="Edm.Guid" Nullable="false" />
  . . .
  <NavigationProperty Name="AffectedTasks" Relationship="ReportingData.Issue_AffectedTasks" ToRole="AffectedTasks" FromRole="Issue" />
  . . .
</EntityType>
```

## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[ReportingData](schema-microsoft-office-project-server-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

Child elements are properties of an issue and navigation properties of that issue. Attributes of the **Property** elements specify the property name and type, and whether the property can be a null value. The **NavigationProperty** elements specify collections of entities, such as tasks and projects, that are associated with an issue. A navigation property uses an **Association** element in a query for a related entity or collection. 
  
The **Key** elements specify the properties that are the primary keys for an issue query. **ProjectId** is the project GUID and **IssueId** is the GUID of the issue. 
  
### Property elements

The following table lists the values of the **Property** elements for the **Issue** entity. The **Name**, **Type**, and **Nullable** columns contain attribute values for each property. 
  
**Attribute values for the Property elements of Issue**

|**Name**|**Type**|**Nullable**|**Description**|
|:-----|:-----|:-----|:-----|
|**AssignedToResource** <br/> |**Edm.String** <br/> |**true** <br/> |The resource to which the issue is assigned.  <br/> |
|**Category** <br/> |**Edm.String** <br/> |**true** <br/> |The category of the issue.  <br/> |
|**CreateByResource** <br/> |**Edm.String** <br/> |**true** <br/> |The resource that created the issue.  <br/> |
|**CreatedDate** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The date and time of creation of the issue.  <br/> |
|**Discussion** <br/> |**Edm.String** <br/> |**true** <br/> |The text field for the issue discussion.  <br/> |
|**DueDate** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The due date and time of the issue.  <br/> |
|**IsFolder** <br/> |**Edm.Boolean** <br/> |**false** <br/> |**True** if the issue is a folder in the SharePoint list.  <br/> |
|**IssueId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID of the issue.  <br/> |
|**ItemRelativeUrlPath** <br/> |**Edm.String** <br/> |**true** <br/> |The relative URL of the issue.  <br/> |
|**ModifiedByResource** <br/> |**Edm.String** <br/> |**true** <br/> |The user who last modified the issue.  <br/> |
|**ModifiedDate** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The date and time that the issue was last modified.  <br/> |
|**NumberOfAttachments** <br/> |**Edm.Int32** <br/> |**true** <br/> |The number of attachments for the issue.  <br/> |
|**Owner** <br/> |**Edm.String** <br/> |**true** <br/> |The owner of the issue.  <br/> |
|**Priority** <br/> |**Edm.String** <br/> |**true** <br/> |The priority of the issue.  <br/> |
|**ProjectId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID that identifies the project.  <br/> |
|**ProjectName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the project.  <br/> |
|**Resolution** <br/> |**Edm.String** <br/> |**true** <br/> |The resolution of the issue.  <br/> |
|**Status** <br/> |**Edm.String** <br/> |**true** <br/> |The status of the issue.  <br/> |
|**Title** <br/> |**Edm.String** <br/> |**true** <br/> |The title or name of the issue.  <br/> |
   
### NavigationProperty elements

The following table lists attribute values for the **NavigationProperty** elements of the **Issue** entity. The **Name** and **Relationship** columns contain attribute values for each navigation property.There are two types of **Relationship** attributes. One type contains two pairs of names; each pair of names indicates a navigation direction. The first pair starts with the entity type that has the primary, or starting, role in the navigation. The second pair starts with the entity type that has the secondary, or dependent, role in the navigation. For example, for the **Project** navigation property, the primary type is **Project**, and the secondary type is **Issue**. For this type of navigation, the **FromRole** is **Project_Issues**, and the **ToRole** is **Issue_Project**.
  
The other type of **Relationship** attribute contains a single pair of names. The first name in the pair is the primary entity type in the navigation. The second name in the pair is the secondary entity type in the navigation. For example, in the **AffectedTasks** navigation property relationship, **Issue** is the primary entity type and **AffectedTasks** is the secondary entity type. 
  
**Attribute values for the NavigationProperty elements**

|**Name**|**Relationship**|**Description**|
|:-----|:-----|:-----|
|**Project** <br/> |[Project_Issues_Issue_Project](association-element-project_issues-projectserverdata-service.md) <br/> |Establishes navigation from a project to a collection of issues and from an issues to a project.  <br/> |
|**RelatedRisks** <br/> |[Issue_RelatedRisks_Risk_RelatedIssues](association-element-issue_relatedrisks-projectserverdata-service.md) <br/> |Establishes navigation from a collection of issues to a collection of related risks and from a risk to a collection of related issues.  <br/> |
|**Tasks** <br/> |[Issue_Tasks_Task_Issues](http://msdn.microsoft.com/library/c0534c3f-56aa-45ac-b78a-9ddfe02b8b3a%28Office.15%29.aspx) <br/> |Establishes navigation from a collection of issues to a task and from a task to a collection of issues.  <br/> |
|**SubIssues** <br/> |[Issue_SubIssues](association-issue_subissues-projectdata-service.md) <br/> |Establishes navigation from a collection of issues to a subissue.  <br/> |
   
## See also

#### Reference

[Issues](entityset-issues-projectdata-service.md)
  
[ReportingData](schema-microsoft-office-project-server-projectdata-service.md)
#### Concepts

[Querying OData feeds for Project reporting data](querying-odata-feeds-for-project-reporting-data.md)

