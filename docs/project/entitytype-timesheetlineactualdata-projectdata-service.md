---
title: "EntityType TimesheetLineActualData (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: 9b8adcf5-8842-4928-b94b-56db3defbdcc
description: "Contains the properties that define the reporting data for timesheet line actual data in the ProjectData service."
---

# EntityType: TimesheetLineActualData (ProjectData service)

Contains the properties that define the reporting data for timesheet line actual data in the **ProjectData** service. 
  
## Example

The following REST query uses the [TimesheetLineActualDataSet](entityset-timesheetlineactualdataset-projectdata-service.md) entity set and the **TimesheetLineId** and **TimeByDay** keys to get the **LastChangedResourceName** property for the specified timesheet line and time range. The query is all on one line. 
  
```
https://<pwa_url>/_api/ProjectData/TimesheetLineActualDataSet
    ?$filter=TimesheetLineId eq guid'50c173b9-23bb-e111-aa86-00155d4a5608'
    and TimeByDay ge datetime'2012-01-01'
    &amp;$select=LastChangedResourceName
```

## Definition

```XML
<EntityType Name="TimesheetLineActualData">
  <Key>
    <PropertyRef Name="AdjustmentIndex" />
    <PropertyRef Name="TimeByDay" />
    <PropertyRef Name="TimesheetLineId" />
  </Key>
  <Property Name="TimesheetLineId" Type="Edm.Guid" Nullable="false" />
  . . .
  <NavigationProperty Name="LastChangedByResource" Relationship="ReportingData.TimesheetLineActualData_LastChangedByResource" ToRole="LastChangedByResource" FromRole="TimesheetLineActualData" />
  . . .
</EntityType>
```

## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[ReportingData](schema-microsoft-office-project-server-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

Child elements are properties of timesheet line actual data and navigation properties of that data. Attributes of the **Property** elements specify the property name and type, and whether the property can be a null value. The **NavigationProperty** elements specify collections of entities, such as time and timesheet line, that are associated with timesheet line actual data. A navigation property uses an **Association** element in a query for a related entity collection 
  
The **Key** elements specify the properties that are the primary keys for a timesheet line actual data query. **TimesheetLineId** is the GUID of the timesheet line, **AdjustmentIndex** is adjustment number, and **TimeByDay** is a day in the timeline. 
  
### Property elements

The following table lists the **Property** elements for the **TimesheetLineActualData** entity. The **Name**, **Type**, and **Nullable** columns contain attribute values for each property. 
  
**Attribute values for the Property elements of TimesheetLineActualData**

|**Name**|**Type**|**Nullable**|**Description**|
|:-----|:-----|:-----|:-----|
|**ActualOvertimeWorkBillable** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The actual billable overtime work that has already been performed.  <br/> |
|**ActualOvertimeWorkNonBillable** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The actual nonbillable overtime work that has already been performed.  <br/> |
|**ActualWorkBillable** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The actual billable amount of work that has already been performed.  <br/> |
|**ActualWorkNonBillable** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The actual nonbillable amount of work that has already been performed.  <br/> |
|**AdjustmentIndex** <br/> |**Edm.Int32** <br/> |**false** <br/> |**Key**         The timesheet actual adjustment index.  <br/> |
|**Comment** <br/> |**Edm.String** <br/> |**true** <br/> |The text field for a timesheet line comment.  <br/> |
|**CreatedDate** <br/> |**Edm.DateTime** <br/> |**false** <br/> |The date and time that the timesheet line was created.  <br/> |
|**LastChangedResourceName** <br/> |**Edm.String** <br/> |**true** <br/> |The resource that last changed the timesheet line.  <br/> |
|**PlannedWork** <br/> |**Edm.Decimal** <br/> |**false** <br/> |The estimated amount of work.  <br/> |
|**ResourceName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the resource associated with the timesheet line.  <br/> |
|**TimeByDay** <br/> |**Edm.DateTime** <br/> |**false** <br/> |**Key**         A primary key that identifies the day along a timeline. The granularity is in days only.  <br/> |
|**TimeByDay_DayOfMonth** <br/> |**Edm.Byte** <br/> |**false** <br/> |The value that represents the day of the month (1-31) for time by day calculation.  <br/> |
|**TimeByDay_DayOfWeek** <br/> |**Edm.Byte** <br/> |**false** <br/> |The value that represents the day of the week (1-7) for time by day calculation.  <br/> |
|**TimesheetLineId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID of the timesheet line.  <br/> |
   
### NavigationProperty elements

The following table lists attribute values for the **NavigationProperty** elements of the **TimesheetLineActualData** entity. The **Name** and **Relationship** columns contain attribute values for each navigation property. 
  
There are two types of **Relationship** attributes. One type contains two pairs of names; each pair of names indicates a navigation direction. The first pair starts with the entity type that has the primary, or starting, role in the navigation. The second pair starts with the entity type that has the secondary, or dependent, role in the navigation. For example, for the **TimesheetLine_Actuals_TimesheetLineActualData_TimesheetLine** navigation property, the primary type is **TimesheetLine**, and the secondary type is **TimesheetLineActualData**. For this type of navigation, the **FromRole** is **TimesheetLine_Actuals**, and the **ToRole** is **TimesheetLineActualData_TimesheetLine**.
  
The other type of **Relationship** attribute contains a single pair of names. The first name in the pair is the primary entity type in the navigation. The second name in the pair is the secondary entity type in the navigation. For example, in the **LastChangedBy** navigation property relationship, **TimesheetLineActualData** is the primary entity type and **LastChangedByResource** is the secondary entity type. 
  
**Attribute values for the NavigationProperty elements**

|**Name**|**Relationship**|**Description**|
|:-----|:-----|:-----|
|**LastChangedByResource** <br/> |[TimesheetLineActualData_LastChangedByResource](association-timesheetlineactualdata_lastchangedbyresource-projectdata-service.md) <br/> |Establishes navigation from a collection of timesheet line actual data to the resource that last changed the timesheet line.  <br/> |
|**Time** <br/> |[TimesheetLineActualData_Time](association-element-timesheetlineactualdata_time-projectserverdata-service.md) <br/> |Establishes navigation from a collection of timesheet line actual data to time data.  <br/> |
|**TimesheetLine** <br/> |[TimesheetLine_Actuals_TimesheetLineActualData_TimesheetLine](http://msdn.microsoft.com/library/f8749715-b4a9-4b4b-9dce-4c836c5c4233%28Office.15%29.aspx) <br/> |Establishes navigation from a timesheet line to timesheet line actual data and from timesheet line actual data to a timesheet line.  <br/> |
   
## See also

#### Reference

[TimesheetLineActualDataSet](entityset-timesheetlineactualdataset-projectdata-service.md)
  
[ReportingData](schema-microsoft-office-project-server-projectdata-service.md)
#### Concepts

[Querying OData feeds for Project reporting data](querying-odata-feeds-for-project-reporting-data.md)

