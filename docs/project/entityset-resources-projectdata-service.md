---
title: "EntitySet Resources (ProjectData service)"

 
manager: soliver
ms.date: 5/19/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: b027af4d-3c32-42e3-8f53-0f2345b776df
description: "Specifies the collection of resources in the ReportingData schema."
---

# EntitySet: Resources (ProjectData service)

Specifies the collection of resources in the **ReportingData** schema. 
  
## Definition

```XML
<EntitySet Name="Resources" EntityType="ReportingData.Resource" />

```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**Resources** <br/> |The name of the entity set.  <br/> |
|**EntityType** <br/> |**ReportingData.Resource** <br/> |The type of entity.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[EntityContainer element: ReportingData](entitycontainer-reportingdata-projectdata-service.md) <br/> |Contains definitions of entity sets for internal use in queries of the online Reporting database.  <br/> |
   
## Child elements

||
|:-----|
|None |
   
## Example

The following statement uses LINQ query syntax to retrieve **Resource** entity data from the OData interface of the Project Server reporting tables. To use the statement in an application, set a service reference to the **ProjectDataService**, and initialize the **ReportingData** context. The **Resources** entity set can then be accessed as  `context.Resources`. For more information, see [Querying OData feeds for Project reporting data](querying-odata-feeds-for-project-reporting-data.md).
  
```cs
var query =
    from r in Resources
    orderby r.ResourceName
    where (r.ResourceCount > (Int32)0)
    select new
    {
        ResourceName = r.ResourceName,
        ResourceEarliestAvailableFrom = r.ResourceEarliestAvailableFrom,
        ResourceStandardRate = r.ResourceStandardRate,
        ResourceMaxUnits = r.ResourceMaxUnits
    };

```

The preceding statement can be written by using Lambda expression syntax, as follows:
  
```cs
var query = Resources
    .OrderBy(r => r.ResourceName)
    .Where(r => (r.ResourceCount > (Int32)0))
    .Select(r => new
    {
        ResourceName = r.ResourceName,
        ResourceEarliestAvailableFrom = r.ResourceEarliestAvailableFrom,
        ResourceStandardRate = r.ResourceStandardRate,
        ResourceMaxUnits = r.ResourceMaxUnits
    });

```

Either statement creates the following REST URL (all on one line).
  
```HTML
http://ServerName/pwa/_vti_bin/client.svc/ProjectServerData/Resources()?
    $orderby=ResourceName&amp;
    $filter=ResourceCount gt 0&amp;
    $select=ResourceName,ResourceEarliestAvailableFrom,ResourceStandardRate,ResourceMaxUnits

```

All three of the sample queries get the same data.
  
**Sample results of the Resources query**

|**ResourceName**|**ResourceEarliestAvailableFrom**|**ResourceStandardRate**|**ResourceMaxUnits**|
|:-----|:-----|:-----|:-----|
|Resource1  <br/> |3/4/2012 8:00:00 AM  <br/> |$19.00  <br/> |100%  <br/> |
|Resource2  <br/> |3/2/2012 8:00:00 AM  <br/> |$18.00  <br/> |100%  <br/> |
|Resource3  <br/> |3/3/2012 8:00:00 AM  <br/> |$15.50  <br/> |100%  <br/> |
   
## Remarks

Each entity set has a specific page-size limit. For information about page limits for on-premises and online ProjectData queries and how to set the on-premises page limit, see [ProjectData - OData service reference](projectdataproject-odata-service-reference.md).
  

