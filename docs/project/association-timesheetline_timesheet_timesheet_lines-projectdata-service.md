---
title: "Association TimesheetLine_Timesheet_Timesheet_Lines (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 47dcd56b-2a27-42cb-86c1-df70786c6d59
description: "The TimesheetLine_Timesheet_Timesheet_Lines association relates timesheet lines to a timesheet and relates a timesheet to timesheet lines."
---

# Association: TimesheetLine_Timesheet_Timesheet_Lines (ProjectData service)

The **TimesheetLine_Timesheet_Timesheet_Lines** association relates timesheet lines to a timesheet and relates a timesheet to timesheet lines. 
  
## Definition

```XML
<Association Name="TimesheetLine_Timesheet_Timesheet_Lines">
  <End Type="ReportingData.Timesheet" Role="Timesheet_Lines" Multiplicity="0..1" />
  <End Type="ReportingData.TimesheetLine" Role="TimesheetLine_Timesheet" Multiplicity="*" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**TimesheetLine_Timesheet_Timesheet_Lines** <br/> |Identifies the entity types and the navigation properties that form the two-way association for projects and tasks. In the first half of the name, **TimesheetLine** is the entity type and **Timesheet** is the navigation property. In the second half of the name, **Timesheet** is the entity type and **Lines** is the navigation property.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **TimesheetLine_Timesheet_Timesheet_Lines** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the TimesheetLine_Timesheet_Timesheet_Lines association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**TimesheetLine_Timesheet** <br/> |[EntityType element: TimesheetLine](entitytype-timesheetline-projectdata-service.md) <br/> |**\*** <br/> |There can be many timesheet line entities that correspond to a timesheet.  <br/> |
|**Timesheet_Lines** <br/> |[EntityType element: Timesheet](entitytype-timesheet-projectdata-service.md) <br/> |**0..1** <br/> |There is one timesheet entity that corresponds to a collection of timesheet lines.  <br/> |
   
## Remarks

One end of the association is the **TimesheetLine** entity, and the other end is the **Timesheet** entity. The **TimesheetLine** entity type contains the **Timesheet** navigation property, where the **FromRole** defines **TimesheetLine_Timesheet** as the start of the association to get the timesheet that is associated with a collection of timesheet lines. Similarly, the **Timesheet** entity type contains the **Timesheet_Lines** navigation property, where the **FromRole** defines **Timesheet_Lines** as the start of the association to get the timesheet lines that belong to a timesheet. 
  
## See also

#### Reference

[EntityType element: Timesheet](entitytype-timesheet-projectdata-service.md)
  
[EntityType element: TimesheetLine](entitytype-timesheetline-projectdata-service.md)

