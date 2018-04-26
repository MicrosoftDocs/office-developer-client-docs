---
title: "EntitySet Assignments (ProjectData service)"

 
manager: soliver
ms.date: 5/19/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: bcbb6dbd-1b24-4cd7-a161-ccc563b1306e
description: "Specifies the collection of assignments in the ReportingData schema."
---

# EntitySet: Assignments (ProjectData service)

Specifies the collection of assignments in the **ReportingData** schema. 
  
## Definition

```XML
<EntitySet Name="Assignments" EntityType="ReportingData.Assignment" />

```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**Assignments** <br/> |The name of the entity set.  <br/> |
|**EntityType** <br/> |**ReportingData.Assignment** <br/> |The type of entity.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[EntityContainer element: ReportingData](entitycontainer-reportingdata-projectdata-service.md) <br/> |Contains definitions of entity sets for internal use in queries of the online Reporting database.  <br/> |
   
## Child elements

||
|:-----|
|None |
   
## Example

The following statement uses LINQ query syntax to retrieve **Assignment** entity data from the OData interface of the Project Server reporting tables. To use the statement in an application, set a service reference to the **ProjectDataService**, and initialize the **ReportingData** context. The **Assignments** entity set can then be accessed as  `context.Assignments`. For more information, see [Querying OData feeds for Project reporting data](querying-odata-feeds-for-project-reporting-data.md).
  
```cs
var query =
    from a in Assignments
    orderby a.ProjectName, a.ResourceName
    select new
    {
        Project = a.ProjectName,
        Resource = a.ResourceName,
        AssignmentBookingType = a.AssignmentBookingName,
        AssignmentStartDate = a.AssignmentStartDate,
        Task = a.TaskName,
        AssignmentWork = a.AssignmentWork,
        AssignmentCost = a.AssignmentCost,
        AssisgnmentCostVariance = a.AssignmentCostVariance,
        AssignmentFinishVariance = a.AssignmentFinishVariance
    };
```

The preceding statement can be written by using Lambda expression syntax, as follows:
  
```cs
var query = Assignments
    .OrderBy(a => a.ProjectName)
    .ThenBy(a => a.ResourceName)
    .Select(a => new
    {
        Project = a.ProjectName,
        Resource = a.ResourceName,
        AssignmentBookingType = a.AssignmentBookingName,
        AssignmentStartDate = a.AssignmentStartDate,
        Task = a.TaskName,
        AssignmentWork = a.AssignmentWork,
        AssignmentCost = a.AssignmentCost,
        AssisgnmentCostVariance = a.AssignmentCostVariance,
        AssignmentFinishVariance = a.AssignmentFinishVariance
    });
```

Either statement creates the following REST URL (all on one line).
  
```HTML
http://ServerName/pwa/_vti_bin/client.svc/ProjectServerData/Assignments()?
    $orderby=ProjectName,ResourceName&amp;            
    $select=ProjectName,ResourceName,AssignmentBookingName,AssignmentStartDate,TaskName,
    AssignmentWork,AssignmentCost,AssignmentCostVariance,AssignmentFinishVariance
```

All three of the sample queries get the same data.
  
**Sample results of the Task query**

|**Project**|**Resource**|**AssignmentBookingType**|**AssignmentStartDate**|**Task**|**AssignmentWork**|**AssignmentCost**|**AssignmentCostVariance**|**AssignmentFinishVariance**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|ProjectA  <br/> |Res2  <br/> |Committed  <br/> |3/12/2012 8:00:00 AM  <br/> |T1  <br/> |24.0 hrs  <br/> |$404.00  <br/> |$0.00  <br/> |0.0 hrs  <br/> |
|ProjectA  <br/> |Res7  <br/> |Committed  <br/> |3/12/2012 8:00:00 AM  <br/> |T3  <br/> |32.0 hrs  <br/> |$564.00  <br/> |$136.00  <br/> |8.0 hrs  <br/> |
|ProjectA  <br/> |Res8  <br/> |Committed  <br/> |3/12/2012 8:00:00 AM  <br/> |T2  <br/> |8.0 hrs  <br/> |$156.00  <br/> |-$272.00  <br/> |-16.0 hrs  <br/> |
|ProjectB  <br/> |Res3  <br/> |Committed  <br/> |3/19/2012 8:00:00 AM  <br/> |T3  <br/> |40.0 hrs  <br/> |$740.00  <br/> |$0.00  <br/> |0.0 hrs  <br/> |
|ProjectB  <br/> |Res4  <br/> |Proposed  <br/> |3/19/2012 8:00:00 AM  <br/> |T4  <br/> |8.0 hrs  <br/> |$168.00  <br/> |-$168.00  <br/> |-8.0 hrs  <br/> |
|ProjectB  <br/> |Res7  <br/> |Committed  <br/> |3/19/2012 8:00:00 AM  <br/> |T1  <br/> |48.0 hrs  <br/> |$836.00  <br/> |$272.00  <br/> |16.0 hrs  <br/> |
|ProjectB  <br/> |Res8  <br/> |Committed  <br/> |3/19/2012 8:00:00 AM  <br/> |T2  <br/> |24.0 hrs  <br/> |$428.00  <br/> |$0.00  <br/> |0.00  <br/> |
   
## Remarks

Each entity set has a specific page-size limit. For information about page limits for on-premises and online ProjectData queries and how to set the on-premises page limit, see [ProjectData - OData service reference](projectdataproject-odata-service-reference.md).
  

