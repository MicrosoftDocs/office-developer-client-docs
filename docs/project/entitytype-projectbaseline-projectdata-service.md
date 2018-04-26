---
title: "EntityType ProjectBaseline (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: e695800e-042e-4775-a426-2988af279cef
description: "Contains the properties that define the reporting data for a project baseline in the ProjectData service."
---

# EntityType: ProjectBaseline (ProjectData service)

Contains the properties that define the reporting data for a project baseline in the **ProjectData** service. 
  
## Example

The following REST query uses the [ProjectBaselines](entityset-projectbaselines-projectdata-service.md) entity set to get the specified project baseline properties. The query is all on one line. 
  
```
http://<pwa_url>/_api/ProjectData/ProjectBaselines
    ?$select=ProjectName,ProjectBaselineStartDate,ProjectBaselineFinishDate,ProjectBaselineWork,ProjectBaselineCost
```

The next two examples also get the following data results.
  
**Sample data results of the ProjectBaseline query**

|**ProjectName**|**StartDate**|**EndDate**|**ProjectBaselineWork**|**ProjectBaselineCost**|
|:-----|:-----|:-----|:-----|:-----|
|ProjectA  <br/> |3/26/2012 8:00:00 AM  <br/> |3/30/2012 5:00:00 PM  <br/> |144.0 hrs  <br/> |$2380.00  <br/> |
|ProjectB  <br/> |3/12/2012 8:00:00 AM  <br/> |3/16/2012 5:00:00 PM  <br/> |87.5 hrs  <br/> |$1835.90  <br/> |
|ProjectC  <br/> |3/12/2012 8:00:00 AM  <br/> |3/17/2012 5:00:00 PM  <br/> |112.0 hrs  <br/> |$1872.00  <br/> |
   
The following statement uses LINQ query syntax to retrieve **ProjectBaseline** entity data from the OData interface of the Project Server reporting tables. To use the statement in an application, set a service reference to the **ProjectDataService**, and initialize the **ReportingData** context. The **ProjectBaselines** entity set can then be accessed as  `context.ProjectBaselines`. For more information, see [Querying OData feeds for Project reporting data](querying-odata-feeds-for-project-reporting-data.md).
  
```cs
    var query =
    from p in ProjectBaselines
    select new
    {
        ProjectName = p.ProjectName,
        StartDate = p.ProjectBaselineStartDate,
        EndDate = p.ProjectBaselineFinishDate,
        ProjectBaselineWork = p.ProjectBaselineWork,
        ProjectBaselineCost = p.ProjectBaselineCost
    };

```

The preceding statement can be written by using Lambda expression syntax, as follows:
  
```cs
    var query = ProjectBaselines
    .Select( p => new
    {
        ProjectName = p.ProjectName,
        StartDate = p.ProjectBaselineStartDate,
        EndDate = p.ProjectBaselineFinishDate,
        ProjectBaselineWork = p.ProjectBaselineWork,
        ProjectBaselineCost = p.ProjectBaselineCost
    });

```

## Definition

```XML
<EntityType Name="ProjectBaseline">
  <Key>
    <PropertyRef Name="ProjectId" />
    <PropertyRef Name="BaselineNumber" />
  </Key>
  <Property Name="ProjectId" Type="Edm.Guid" Nullable="false" />
  . . .
  <NavigationProperty Name="Project" Relationship="ReportingData.ProjectBaseline_Project" ToRole="Project" FromRole="ProjectBaseline" />
</EntityType>
```

## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[ReportingData](schema-microsoft-office-project-server-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

Child elements are properties of a project baseline and navigation properties of that project baseline. Attributes of the **Property** elements specify the property name and type, and whether the property can be a null value. The **NavigationProperty** element specifies a project entity that is associated with a project baseline. A navigation property uses an **Association** element in a query for a related entity collection 
  
The **Key** elements specify the properties that are the primary keys for a project baseline query. **ProjectId** is the project GUID. **BaselineNumber** is the number of the baseline. 
  
### Property elements

The following table lists the **Property** elements for the **ProjectBaseline** entity. The **Name**, **Type**, and **Nullable** columns contain attribute values for each property. 
  
**Attribute values for the Property elements of ProjectBaseline**

|**Name**|**Type**|**Nullable**|**Description**|
|:-----|:-----|:-----|:-----|
|**BaselineNumber** <br/> |**Edm.Int32** <br/> |**false** <br/> |**Key**         The number that identifies a baseline.  <br/> |
|**ProjectId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID that identifies a project.  <br/> |
|**ProjectName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of a project.  <br/> |
|**ProjectBaselineBudgetCost** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The planned budgeted cost of a project.  <br/> |
|**ProjectBaselineBudgetWork** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The planned budgeted amount of work for a project.  <br/> |
|**ProjectBaselineCost** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The planned cost of a project.  <br/> |
|**ProjectBaselineDeliverableFinishDate** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The planned finish date for a project deliverable.  <br/> |
|**ProjectBaselineDeliverableStartDate** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The planned start date for a project deliverable.  <br/> |
|**ProjectBaselineDuration** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The planned duration of a project.  <br/> |
|**ProjectBaselineDurationString** <br/> |**Edm.String** <br/> |**true** <br/> |A string that contains a planned project duration.  <br/> |
|**ProjectBaselineFinishDate** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The finish date and time for a planned project.  <br/> |
|**ProjectBaselineFinishDateString** <br/> |**Edm.String** <br/> |**true** <br/> |A string that contains a planned project finish date and time.  <br/> |
|**ProjectBaselineFixedCost** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The planned cost for a task that remains constant regardless of its duration or the work performed by a resource.  <br/> |
|**ProjectBaselineStartDate** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The start date and time for a planned project.  <br/> |
|**ProjectBaselineStartDateString** <br/> |**Edm.String** <br/> |**true** <br/> |A string that contains a planned project start date and time.  <br/> |
|**ProjectBaselineWork** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The planned total amount of work for a project.  <br/> |
|**TaskId** <br/> |**Edm.Guid** <br/> |**false** <br/> |The GUID that identifies a task.  <br/> |
   
### NavigationProperty elements

The following table lists attribute values for the **NavigationProperty** element of the **ProjectBaseline** entity. The **Name** and **Relationship** columns contain attribute values for the navigation property. 
  
The **Relationship** attribute contains a pair of names. The first name in the pair is the primary entity type in the navigation. The second name in the pair is the secondary entity type in the navigation. In the **Project** navigation property relationship, **ProjectBaseline** is the primary entity type and **Project** is the secondary entity type. 
  
**Attribute values for the NavigationProperty elements**

|**Name**|**Relationship**|**Description**|
|:-----|:-----|:-----|
|**Project** <br/> |[ProjectBaseline_Project](association-element-projectbaseline_project-projectserverdata-service.md) <br/> |Establishes navigation from a collection of project baselines to a project.  <br/> |
   
## See also

#### Reference

[ProjectBaselines](entityset-projectbaselines-projectdata-service.md)
  
[ReportingData](schema-microsoft-office-project-server-projectdata-service.md)
#### Concepts

[Querying OData feeds for Project reporting data](querying-odata-feeds-for-project-reporting-data.md)

