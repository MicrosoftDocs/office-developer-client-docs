---
title: "EntityType Deliverable (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: ad49200b-7f3c-4541-a095-7d8768d409d5
description: "Contains the properties that define the reporting data for a deliverable in the ProjectData service."
---

# EntityType: Deliverable (ProjectData service)

Contains the properties that define the reporting data for a deliverable in the **ProjectData** service. 
  
## Example

The following REST query uses the [Deliverables](entityset-deliverables-projectdata-service.md) entity set and the **DeliverableId** and **ProjectId** keys to get the URL path of the specified deliverable. The query is all on one line. 
  
```
http://<pwa_url>/_api/ProjectData/Deliverables
    ?$select=ItemRelativeUrlPath
    &amp;$filter=DeliverableId eq guid'ff5ab774-4dff-4af7-a0d9-f0214c782d86'
    and ProjectId eq guid'c03bfc61-e0e1-e111-8d29-00155d35d32e'
```

## Definition

```XML
<EntityType Name="Deliverable">
  <Key>
    <PropertyRef Name="ProjectId" />
    <PropertyRef Name="DeliverableId" />
  </Key>
  <Property Name="ProjectId" Type="Edm.Guid" Nullable="false" />
  . . .
  <NavigationProperty Name="DependentProjects" Relationship="ReportingData.Project_Dependencies_Deliverable_DependentProjects" ToRole="Project_Dependencies" FromRole="Deliverable_DependentProjects" />
  . . .
</EntityType>
```

## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[ReportingData](schema-microsoft-office-project-server-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

Child elements are properties of a deliverable and navigation properties of that deliverable. Attributes of the **Property** elements specify the property name and type, and whether the property can be a null value. The **NavigationProperty** elements specify collections of entities, such as parent projects and dependent tasks, that are associated with a deliverable. A navigation property uses an **Association** element in a query for a related entity or collection 
  
The **Key** elements specify the properties that are the primary keys for a deliverable query. **ProjectId** is the project GUID and **DeliverableId** is the GUID of the deliverable. 
  
### Property elements

The following table lists the values of the **Property** elements for the **Deliverable** entity. The **Name**, **Type**, and **Nullable** columns contain attribute values for each property. 
  
**Attribute values for the Property elements of Deliverables**

|**Name**|**Type**|**Nullable**|**Description**|
|:-----|:-----|:-----|:-----|
|**CreateByResource** <br/> |**Edm.String** <br/> |**true** <br/> |The resource that created the deliverable.  <br/> |
|**CreatedDate** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The date and time that the deliverable was created.  <br/> |
|**DeliverableId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID of the deliverable.  <br/> |
|**Description** <br/> |**Edm.String** <br/> |**true** <br/> |The description of the deliverable.  <br/> |
|**FinishDate** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The finish date of the deliverable.  <br/> |
|**IsFolder** <br/> |**Edm.Boolean** <br/> |**false** <br/> |**True** if the deliverable is a folder in the SharePoint list.  <br/> |
|**ItemRelativeUrlPath** <br/> |**Edm.String** <br/> |**true** <br/> |The relative URL of the deliverable.  <br/> |
|**ModifiedByResource** <br/> |**Edm.String** <br/> |**true** <br/> |The resource that last changed the deliverable.  <br/> |
|**ModifiedDate** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The date and time that the deliverable was modified.  <br/> |
|**ProjectId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID of the project for the deliverable.  <br/> |
|**ProjectName** <br/> |Edm.String  <br/> |**true** <br/> |The name of the project.  <br/> |
|**StartDate** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The start date and time of the deliverable.  <br/> |
|**Title** <br/> |**Edm.String** <br/> |**true** <br/> |The title of the deliverable.  <br/> |
   
### NavigationProperty elements

The following table lists attribute values for the **NavigationProperty** elements of the **Deliverable** entity. The **Name** and **Relationship** columns contain attribute values for each navigation property.There are two types of **Relationship** attributes. One type contains two pairs of names; each pair of names indicates a navigation direction. The first pair starts with the entity type that has the primary, or starting, role in the navigation. The second pair starts with the entity type that has the secondary, or dependent, role in the navigation. For example, for the **Project** navigation property, the primary type is **Project**, and the secondary type is **Deliverable**. For this type of navigation, the **FromRole** is **Project_Deliverables**, and the **ToRole** is **Deliverable_Project**.
  
The other type of **Relationship** attribute contains a single pair of names. The first name in the pair is the primary entity type in the navigation. The second name in the pair is the secondary entity type in the navigation. For example, in the **DependentTasks** navigation property relationship, **Deliverable** is the primary entity type and **DependentTasks** is the secondary entity type. 
  
**Attribute values for the NavigationProperty elements**

|**Name**|**Relationship**|**Description**|
|:-----|:-----|:-----|
|**DependentProjects** <br/> |[Project_Dependencies_Deliverable_DependentProjects](association-project_dependencies_deliverable_dependentprojects-projectdata-servi.md) <br/> |Establishes navigation from a collection of projects to a dependenciy entity and from a deliverable to a collection of dependent projects.  <br/> |
|**DependentTasks** <br/> |[Deliverable_DependentTasks](association-deliverable_dependenttasks-projectdata-service.md) <br/> |Establishes navigation from a collection of deliverables to a dependent task.  <br/> |
|**ParentProjects** <br/> |[Deliverable_ParentProjects](association-element-deliverable_parentprojects-projectserverdata-service.md) <br/> |Establishes navigation from a collection of deliverables to a parent project.  <br/> |
|**ParentTasks** <br/> |[Deliverable_ParentTasks](association-deliverable_parenttasks-projectdata-service.md) <br/> |Establishes navigation from a collection of deliverables to a task.  <br/> |
|**Project** <br/> |[Project_Deliverables_Deliverable_Project](association-element-project_deliverables-projectserverdata-service.md) <br/> |Establishes navigation from a project to a collection of deliverables and from deliverable to a project.  <br/> |
   
## See also

#### Reference

[Deliverables](entityset-deliverables-projectdata-service.md)
  
[ReportingData](schema-microsoft-office-project-server-projectdata-service.md)
#### Concepts

[Querying OData feeds for Project reporting data](querying-odata-feeds-for-project-reporting-data.md)

