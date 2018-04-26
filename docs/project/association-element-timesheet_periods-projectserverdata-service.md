---
title: "Association element Timesheet_Periods (ProjectServerData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: d698f8b8-882c-48d1-9c35-0580008ae67b
description: "The Timesheet_Periods association relates a timesheet period to its timesheet."
---

# Association element: Timesheet_Periods (ProjectServerData service)

The **Timesheet_Periods** association relates a timesheet period to its timesheet. 
  
## Definition

```XML
<Association Name="Timesheet_Periods">
  <End Type="ReportingData.Timesheet" Role="Timesheet" Multiplicity="*" />
  <End Type="ReportingData.TimesheetPeriod" Role="Periods" Multiplicity="0..1" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**Timesheet_Periods** <br/> |Identifies the two entity types that form the **Timesheet_Periods** association.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **Timesheet_Periods** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the Timesheet_Periods association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**Timesheet** <br/> |[EntityType element: Timesheet](entitytype-timesheet-projectdata-service.md) <br/> |**\*** <br/> |The collection of timesheets in the reporting tables.  <br/> |
|**Periods** <br/> |[EntityType element: TimesheetPeriod](entitytype-element-timesheetperiod-projectserverdata-service.md) <br/> |**0..1** <br/> |The timesheet period object that is referenced in the **Timesheet_Periods** association.  <br/> |
   
## Remarks

The **Periods** navigation property in the **Timesheet** entity uses the **Timesheet_Periods** association to query for a time period that is associated with a collection of timesheets. 
  
## See also

#### Reference

[EntityType element: Timesheet](entitytype-timesheet-projectdata-service.md)
  
[EntityType element: TimesheetPeriod](entitytype-element-timesheetperiod-projectserverdata-service.md)

