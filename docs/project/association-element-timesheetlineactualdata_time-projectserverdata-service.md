---
title: "Association element TimesheetLineActualData_Time (ProjectServerData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: f7ca9b07-2897-4d1e-add6-0cb67c99f6ee
description: "The TimesheetLineActualData_Time association relates timesheet line actual data to a time entity."
---

# Association element: TimesheetLineActualData_Time (ProjectServerData service)

The **TimesheetLineActualData_Time** association relates timesheet line actual data to a time entity. 
  
## Definition

```XML
<Association Name="TimesheetLineActualData_Time">
  <End Type="ReportingData.TimesheetLineActualData" Role="TimesheetLineActualData" Multiplicity="*" />
  <End Type="ReportingData.Time" Role="Time" Multiplicity="0..1" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**TimesheetLineActualData_Time** <br/> |Identifies the two entity types that form the **TimesheetLineActualData_Time** association.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **TimesheetLineActualData_Time** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the TimesheetLineActualData_Time association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**TimesheetLineActualData** <br/> |[EntityType element: TimesheetLineActualData](entitytype-timesheetlineactualdata-projectdata-service.md) <br/> |**\*** <br/> |The collection of actual data for timesheet lines, in the reporting table.  <br/> |
|**Time** <br/> |[EntityType element: Time](entitytype-time-projectdata-service.md) <br/> |**0..1** <br/> |The time object that is referenced in the **TimesheetLineActualData_Time** association.  <br/> |
   
## Remarks

The **Time** navigation property in the **TimesheetLineActualData** entity uses the **TimesheetLineActualData_Time** association to query for a time that is associated with a collection of timesheet line actual data. 
  
## See also

#### Reference

[EntityType element: Time](entitytype-time-projectdata-service.md)
  
[EntityType element: TimesheetLineActualData](entitytype-timesheetlineactualdata-projectdata-service.md)

