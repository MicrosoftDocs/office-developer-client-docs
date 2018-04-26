---
title: "EntityType element TimesheetPeriod (ProjectServerData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: 7e3c9b7e-0d8d-483d-92ea-9355badbb8eb
description: "Contains the properties that define the reporting data for a timesheet period in the ProjectData service."
---

# EntityType element: TimesheetPeriod (ProjectServerData service)

Contains the properties that define the reporting data for a timesheet period in the **ProjectData** service. 
  
## Example

The following REST query uses the [TimesheetPeriods](entityset-timesheetperiods-projectdata-service.md) entity set and the **PeriodId** key to get the specified timesheet period. The query is all on one line. 
  
```
https://<pwa-url>/_api/ProjectData/TimesheetPeriods
    ?$filter=PeriodId eq guid'e536e2e2-6eaa-e111-99fe-00155d4a4104'
```

## Definition

```XML
<EntityType Name="TimesheetPeriod">
  <Key>
    <PropertyRef Name="PeriodId" />
  </Key>
  <Property Name="PeriodId" Type="Edm.Guid" Nullable="false" />
  . . .
</EntityType>
```

## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[ReportingData](schema-microsoft-office-project-server-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

Child elements are properties of a timesheet period. Attributes of the **Property** elements specify the property name and type, and whether the property can be a null value. Unlike most entity types, there are no **NavigationProperty** child elements for the **TimesheetPeriod** entity type. 
  
The **Key** element specifies the property that is the primary key for a timesheet period query. **PeriodId** is the timesheet period GUID. 
  
### Property elements

The following table lists the **Property** elements for the **TimesheetPeriod** entity. The **Name**, **Type**, and **Nullable** columns contain attribute values for each property. 
  
**Attribute values for the Property elements**

|**Name**|**Type**|**Nullable**|**Description**|
|:-----|:-----|:-----|:-----|
|**Description** <br/> |**Edm.String** <br/> |**true** <br/> |The text field for the timesheet period description.  <br/> |
|**EndDate** <br/> |**Edm.DateTime** <br/> |**false** <br/> |The end date and time of the timesheet period.  <br/> |
|**LCID** <br/> |**Edm.Int32** <br/> |**true** <br/> |The locale identifier.  <br/> |
|**PeriodId** <br/> |**Edm.Guid** <br/> |**false** <br/> |**Key**         The GUID for the timesheet period.  <br/> |
|**PeriodName** <br/> |**Edm.String** <br/> |**true** <br/> |The name of the timesheet period.  <br/> |
|**PeriodStatusId** <br/> |**Edm.Byte** <br/> |**false** <br/> |The status identifier of the timesheet period (open, closed, or all periods).  <br/> |
|**StartDate** <br/> |**Edm.DateTime** <br/> |**false** <br/> |The start date and time of the timesheet period.  <br/> |
   
### NavigationProperty elements

There are no **NavigationProperty** child elements for the **TimesheetPeriod** entity type. 
  
## See also

#### Reference

[TimesheetPeriods](entityset-timesheetperiods-projectdata-service.md)
  
[ReportingData](schema-microsoft-office-project-server-projectdata-service.md)
#### Concepts

[Querying OData feeds for Project reporting data](querying-odata-feeds-for-project-reporting-data.md)

