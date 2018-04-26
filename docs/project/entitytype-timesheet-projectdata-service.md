---
title: "EntityType Timesheet (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: 828948ef-f9fa-4d67-baa7-8bae7446525e
description: "Contains the properties that define the reporting data for a timesheet in the ProjectData service."
---

# EntityType: Timesheet (ProjectData service)

Contains the properties that define the reporting data for a timesheet in the **ProjectData** service. 
  
## Example

The following REST query uses the [Timesheets](entityset-timesheets-projectdata-service.md) entity set and the **StatusDescription** property to get the specified properties for in-progress timesheets in **ProjectData**. The query is all on one line.
  
```
https://<pwa_url>/_api/ProjectData/Timesheets
    ?$filter=StatusDescription eq 'In Progress'
    &amp;$select=StartDate,TimesheetOwner
```

## Definition

```XML
<EntityType Name="Timesheet">
  <Key>
    <PropertyRef Name="TimesheetId" />
  </Key>
  <Property Name="TimesheetId" Type="Edm.Guid" Nullable="false" />
  . . .
  <NavigationProperty Name="Lines" Relationship="ReportingData.TimesheetLine_Timesheet_Timesheet_Lines" ToRole="TimesheetLine_Timesheet" FromRole="Timesheet_Lines" />
  . . .
</EntityType>
```

## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[ReportingData](schema-microsoft-office-project-server-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

Child elements are properties of a timesheet and navigation properties of that timesheet. Attributes of the **Property** elements specify the property name and type, and whether the property can be a null value. The **NavigationProperty** elements specify collections of entities, such as lines and periods, that are associated with a timesheet. A navigation property uses an **Association** element in a query for a related entity collection 
  
The **Key** element specifies the property that is the primary key for a timesheet query. **TimesheetId** is the GUID of the timesheet. 
  
### Property elements

The following table lists the **Property** elements for the **Timesheet** entity. The **Name**, **Type**, and **Nullable** columns contain attribute values for each property. 
  
**Attribute values for the Property elements of Timesheet**

|**Name**|**Type**|**Nullable**|**Description**|
|:-----|:-----|:-----|:-----|
|**Comment** <br/> |**Edm.String** <br/> |**true** <br/> |The text comment for the timesheet.  <br/> |
|**Description** <br/> |**Edm.String** <br/> |**true** <br/> |The text field for the timesheet description.  <br/> |
|**EndDate** <br/> |**Edm.DateTime** <br/> |**false** <br/> |The end date and time for the timesheet.  <br/> |
|**ModifiedDate** <br/> |**Edm.DateTime** <br/> |**false** <br/> |The date and time that the timesheet was last modified.  <br/> |
|**PeriodId** <br/> |**Edm.Guid** <br/> |**false** <br/> |The GUID for the timesheet period.  <br/> |
|**PeriodName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the timesheet period.  <br/> |
|**PeriodStatusId** <br/> |**Edm.Byte** <br/> |**false** <br/> |The status identifier of the timesheet period (open, closed, or all periods).  <br/> |
|**StartDate** <br/> |**Edm.DateTime** <br/> |**false** <br/> |The start date and time of the timesheet.  <br/> |
|**StatusDescription** <br/> |**Edm.String** <br/> |**true** <br/> |The description of the timesheet status (for example, Approved).  <br/> |
|**TimesheetId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID of the timesheet.  <br/> |
|**TimesheetName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the timesheet.  <br/> |
|**TimesheetOwner** <br/> |**Edm.String** <br/> |**true** <br/> |The owner of the timesheet.  <br/> |
|**TimesheetOwnerId** <br/> |**Edm.Guid** <br/> |**false** <br/> |The GUID of the owner of the timesheet.  <br/> |
|**TimesheetStatusId** <br/> |**Edm.Byte** <br/> |**false** <br/> |The numerical value that represents the status of the timesheet: Not specified = -1, In progress = 0, Submitted = 1, Acceptable = 2, Approved = 3, Rejected = 4, Pending submit = 5 (used when one or more timesheet lines are pending approval after a timesheet is submitted and project manager coordination is required).  <br/> |
   
### NavigationProperty elements

The following table lists attribute values for the **NavigationProperty** elements of the **Timesheet** entity. The **Name** and **Relationship** columns contain attribute values for each navigation property. 
  
There are two types of **Relationship** attributes. One type contains two pairs of names; each pair of names indicates a navigation direction. The first pair starts with the entity type that has the primary, or starting, role in the navigation. The second pair starts with the entity type that has the secondary, or dependent, role in the navigation. For example, for the **Lines** navigation property, the primary type is **TimesheetLine**, and the secondary type is **Timesheet**. For this type of navigation, the **FromRole** is **TimesheetLine_Timesheet**, and the **ToRole** is **Timesheet_Lines**.
  
The other type of **Relationship** attribute contains a single pair of names. The first name in the pair is the primary entity type in the navigation. The second name in the pair is the secondary entity type in the navigation. For example, in the **Periods** navigation property relationship, **Timesheet** is the primary entity type and **Periods** is the secondary entity type. 
  
**Attribute values for the NavigationProperty elements**

|**Name**|**Relationship**|**Description**|
|:-----|:-----|:-----|
|**Lines** <br/> |[TimesheetLine_Timesheet_Timesheet_Lines](http://msdn.microsoft.com/library/09f40b49-4c0d-4aee-9d5f-8c97bfd93ccb%28Office.15%29.aspx) <br/> |Establishes navigation from a collection of timesheet lines to a timesheet and from a timesheet to a timesheet line.  <br/> |
|**Periods** <br/> |[Timesheet_Periods](association-element-timesheet_periods-projectserverdata-service.md) <br/> |Establishes navigation from a collection of timesheets to a timesheet time period.  <br/> |
   
## See also

#### Reference

[Timesheets](entityset-timesheets-projectdata-service.md)
  
[ReportingData](schema-microsoft-office-project-server-projectdata-service.md)
#### Concepts

[Querying OData feeds for Project reporting data](querying-odata-feeds-for-project-reporting-data.md)

