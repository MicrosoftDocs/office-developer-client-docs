---
title: "EntityType Resource (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: 2a5318d3-0eb5-4570-aa3f-56198d3d18aa
description: "Contains the properties that define the reporting data for a resource in the ProjectData service."
---

# EntityType: Resource (ProjectData service)

Contains the properties that define the reporting data for a resource in the **ProjectData** service. 
  
## Example

The following REST query uses the [Resources](entityset-resources-projectdata-service.md) entity set and the **ResourceId** key to get the specified resource and properties. The query is all on one line. 
  
```
https://<pwa_url>/_api/ProjectData/Resources
    ?$filter=ResourceId eq guid'7589986b-c623-e211-b517-00155d34681f'
    &amp;$select=ResourceBaseCalendar,ResourceIsActive,ResourceName
```

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

Both preceding statements create the following REST URL (all on one line).
  
```
http://<pwa_url>/_api/ProjectData/Resources
    ?$orderby=ResourceName
    &amp;$filter=ResourceCount gt 0
    &amp;$select=ResourceName,ResourceEarliestAvailableFrom,ResourceStandardRate,ResourceMaxUnits

```

All three of the sample queries get the same data shown in the table below.
  
**Sample results of the Resources query**

|**ResourceName**|**ResourceEarliestAvailableFrom**|**ResourceStandardRate**|**ResourceMaxUnits**|
|:-----|:-----|:-----|:-----|
|Resource1  <br/> |3/4/2012 8:00:00 AM  <br/> |$19.00  <br/> |100%  <br/> |
|Resource2  <br/> |3/2/2012 8:00:00 AM  <br/> |$18.00  <br/> |100%  <br/> |
|Resource3  <br/> |3/3/2012 8:00:00 AM  <br/> |$15.50  <br/> |100%  <br/> |
   
## Definition

```XML
<EntityType Name="Resource">
  <Key>
    <PropertyRef Name="ResourceId" />
  </Key>
  <Property Name="ResourceId" Type="Edm.Guid" Nullable="false" />
  . . .
  <NavigationProperty Name="Assignments" Relationship="ReportingData.Assignment_Resource_Resource_Assignments" ToRole="Assignment_Resource" FromRole="Resource_Assignments" />
  . . .
</EntityType>
```

## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[ReportingData](schema-microsoft-office-project-server-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

Child elements are properties of a resource and navigation properties of that resource. Attributes of the **Property** elements specify the property name and type, and whether the property can be a null value. The **NavigationProperty** elements specify collections of entities, such as assignments, that are associated with a resource. A navigation property uses an **Association** element in a query for a related entity collection 
  
The **Key** element specifies the property that is the primary key for a resource query. **ResourceId** is the resource GUID. 
  
### Property elements

The following table lists the **Property** elements for the **Resource** entity. The **Name**, **Type**, and **Nullable** columns contain attribute values for each property. 
  
**Attribute values for the Property elements of Resource**

|**Name**|**Type**|**Nullable**|**Description**|
|:-----|:-----|:-----|:-----|
|**CostType** <br/> |**Edm.String** <br/> |**true** <br/> |A type of cost, for instance cumulative cost or cost-per-use.  <br/> |
|**RBS** <br/> |**Edm.String** <br/> |**true** <br/> |A custom field that helps to determine the resources and the assignments that a user can view in the Resource Center when they are using Microsoft Project Web Access.  <br/> |
|**ResourceBaseCalendar** <br/> |**Edm.String** <br/> |**true** <br/> |The base calendar for a resource.  <br/> |
|**ResourceBookingType** <br/> |**Edm.Byte** <br/> |**true** <br/> |The resource booking type, proposed or committed.  <br/> |
|**ResourceCanLevel** <br/> |**Edm.Boolean** <br/> |**false** <br/> |**True** if resource leveling can be done.  <br/> |
|**ResourceCode** <br/> |**Edm.String** <br/> |**true** <br/> |A user-defined code for filtering or sorting resources.  <br/> |
|**ResourceCostCenter** <br/> |**Edm.String** <br/> |**true** <br/> |A user-defined code for resource cost accounting.  <br/> |
|**ResourceCostPerUse** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The cost that accrues each time a work resource is used.  <br/> |
|**ResourceCreatedDate** <br/> |**Edm.DateTime** <br/> |**false** <br/> |The date and time that a resource was created in the project.  <br/> |
|**ResourceDepartments** <br/> |**Edm.String** <br/> |**true** <br/> |The department that is associated with a resource.  <br/> |
|**ResourceEarliestAvailableFrom** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The earliest date that a resource is available for work on a particular task.  <br/> |
|**ResourceEmailAddress** <br/> |**Edm.String** <br/> |**true** <br/> |The email address of a resource.  <br/> |
|**ResourceGroup** <br/> |**Edm.String** <br/> |**true** <br/> |The group to which a resource belongs.  <br/> |
|**ResourceHyperlink** <br/> |**Edm.String** <br/> |**true** <br/> |The URL that is specified for a resource in the Edit User page of Project Web Access.  <br/> |
|**ResourceHyperlinkHref** <br/> |**Edm.String** <br/> |**true** <br/> |The text that is displayed for a resource hyperlink, as specified in the Edit User page of Project Web Access.  <br/> |
|**ResourceId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID that identifies a resource.  <br/> |
|**ResourceInitials** <br/> |**Edm.String** <br/> |**true** <br/> |The initials of a resource.  <br/> |
|**ResourceIsActive** <br/> |**Edm.Boolean** <br/> |**false** <br/> |**True** if a resource is active.  <br/> |
|**ResourceIsGeneric** <br/> |**Edm.Boolean** <br/> |**false** <br/> |**True** if a resource is generic.  <br/> |
|**ResourceIsTeam** <br/> |**Edm.Boolean** <br/> |**false** <br/> |**True** if a resource is a team resource.  <br/> |
|**ResourceLatestAvailableTo** <br/> |**Edm.DateTime** <br/> |**true** <br/> |The last date that a resource is available.  <br/> |
|**ResourceMaterialLabel** <br/> |**Edm.String** <br/> |**true** <br/> |A unit of measurement for a material resource.  <br/> |
|**ResourceMaxUnits** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The maximum capacity (percentage or units) that a resource is available to accomplish tasks during the current time period.  <br/> |
|**ResourceModifiedDate** <br/> |**Edm.DateTime** <br/> |**false** <br/> |The date that information about a resource was last modified.  <br/> |
|**ResourceName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of a resource.  <br/> |
|**ResourceNTAccount** <br/> |**Edm.String** <br/> |**true** <br/> |The Windows account name for a resource.  <br/> |
|**ResourceOvertimeRate** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The rate of overtime pay for a resource.  <br/> |
|**ResourceStandardRate** <br/> |**Edm. Decimal** <br/> |**false** <br/> |The standard rate of pay for a resource.  <br/> |
|**ResourceStatusId** <br/> |**Edm.Guid** <br/> |**false** <br/> |The GUID of a resource status.  <br/> |
|**ResourceStatusName** <br/> |**Edm.String** <br/> |**true** <br/> |The localized name of a resource status (for example, Unassigned Resource, Local Resource, Unknown Resource, and Enterprise Resource).  <br/> |
|**ResourceTimesheetManageId** <br/> |**Edm.Guid** <br/> |**true** <br/> |The GUID of a timesheet manager.  <br/> |
|**ResourceType** <br/> |**Edm.Int16** <br/> |**false** <br/> |The type of a resource (for example, Enterprise, Local, Project Server, Material, or Generic). See **ResourceType** for valid values.  <br/> |
|**ResourceWorkGroup** <br/> |**Edm.Int16** <br/> |**true** <br/> |A number value that represents a team collaboration method for a resource.  <br/> |
|**TypeDescription** <br/> |**Edm.String** <br/> |**true** <br/> |The description of the resource type.  <br/> |
|**TypeName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the resource type (for example, Pure User or Work Resource).  <br/> |
   
### NavigationProperty elements

The following table lists attribute values for the **NavigationProperty** elements of the **Resource** entity. The **Name** and **Relationship** columns contain attribute values for each navigation property. 
  
Each **Relationship** attribute has two pairs of names; each pair of names indicates a navigation direction. The first pair starts with the entity type that has the primary, or starting, role in the navigation. The second pair starts with the entity type that has the secondary, or dependent, role in the navigation. For example, for the **Assignments** navigation property, the primary type is **Assignment**, and the secondary type is **Resource**. For this type of navigation, the **FromRole** is **Assignment_Resource**, and the **ToRole** is **Resource_Assignments**.
  
**Attribute values for the NavigationProperty elements**

|**Name**|**Relationship**|**Description**|
|:-----|:-----|:-----|
|**Assignments** <br/> |[Assignment_Resource_Resource_Assignments](association-element-assignment_resource-projectserverdata-service.md) <br/> |Establishes navigation from a collection of assignments to a resource and from a resource to a collection of assignments.  <br/> |
|**TimephasedInfoDataSet** <br/> |[ResourceTimephasedData_Resource_Resource_TimephasedInfoDataSet](association-resourcetimephaseddata_resource_resource_timephasedinfodataset-proje.md) <br/> |Establishes navigation from resource timephased data to a resource and from a resource to a timephased information data set.  <br/> |
   
## See also

#### Reference

[Resources](entityset-resources-projectdata-service.md)
  
[ReportingData](schema-microsoft-office-project-server-projectdata-service.md)
#### Concepts

[Querying OData feeds for Project reporting data](querying-odata-feeds-for-project-reporting-data.md)

