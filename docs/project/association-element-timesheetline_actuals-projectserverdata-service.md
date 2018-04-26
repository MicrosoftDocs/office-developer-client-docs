---
title: "Association element TimesheetLine_Actuals (ProjectServerData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: c3339e2a-88ce-4b1d-a842-842b9d44b739
description: "The TimesheetLine_Actuals_TimesheetLineActualData_TimesheetLine association relates a timesheet line to actual data and relates timesheet line actual data to a timesheet line."
---

# Association element: TimesheetLine_Actuals (ProjectServerData service)

The **TimesheetLine_Actuals_TimesheetLineActualData_TimesheetLine** association relates a timesheet line to actual data and relates timesheet line actual data to a timesheet line. 
  
## Definition

```XML
<Association Name="TimesheetLine_Actuals_TimesheetLineActualData_TimesheetLine">
  <End Type="ReportingData.TimesheetLineActualData" Role="TimesheetLineActualData_TimesheetLine" Multiplicity="*" />
  <End Type="ReportingData.TimesheetLine" Role="TimesheetLine_Actuals" Multiplicity="0..1" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**TimesheetLine_Actuals_TimesheetLineActualData_TimesheetLine** <br/> |Identifies the entity types and the navigation properties that form the two-way association for timesheet lines and timesheet line actual data. In the first half of the name, **TimesheetLine** is the entity type and **Actuals** is the navigation property. In the second half of the name, **TimesheetLineActualData** is the entity type and **TimesheetLine** is the navigation property.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **TimesheetLine_Actuals_TimesheetLineActualData_TimesheetLine** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the TimesheetLine_Actuals_TimesheetLineActualData_TimesheetLine association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**TimesheetLine_Actuals** <br/> |[EntityType element: TimesheetLine](entitytype-timesheetline-projectdata-service.md) <br/> |**0..1** <br/> |There is one timesheet line entity that corresponds to a collection of actuals.  <br/> |
|**TimesheetLineActualData_TimesheetLine** <br/> |[EntityType element: TimesheetLineActualData](entitytype-timesheetlineactualdata-projectdata-service.md) <br/> |**\*** <br/> |There can be many timesheet line actual data entities that correspond with a timesheet line.  <br/> |
   
## Remarks

One end of the association is the **TimesheetLine** entity, and the other end is the **TimesheetLineActualData** entity. The **TimesheetLine** entity type contains the **Actuals** navigation property, where the **FromRole** defines **TimesheetLine_Actuals** as the start of the association to get the collection of actual data that is associated with a timesheet line. Similarly, the **TimesheetLineActualData** entity type contains the **TimesheetLine** navigation property, where the **FromRole** defines **TimesheetLineActualData_TimesheetLine** as the start of the association to get the timesheet line that is associated with a collection of timesheet line actual data. 
  
## See also

#### Reference

[EntityType element: TimesheetLine](entitytype-timesheetline-projectdata-service.md)
  
[EntityType element: TimesheetLineActualData](entitytype-timesheetlineactualdata-projectdata-service.md)

