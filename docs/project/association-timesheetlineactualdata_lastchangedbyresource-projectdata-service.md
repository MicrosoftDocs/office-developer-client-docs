---
title: "Association TimesheetLineActualData_LastChangedByResource (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: 68c1bdf0-4f5c-483c-a8e0-cc109e6a4dbb
description: "The TimesheetLineActualData_LastChangedByResource association relates timesheet line actual data to a resource."
---

# Association: TimesheetLineActualData_LastChangedByResource (ProjectData service)

The **TimesheetLineActualData_LastChangedByResource** association relates timesheet line actual data to a resource. 
  
## Definition

```XML
<Association Name="TimesheetLineActualData_LastChangedByResource">
  <End Type="ReportingData.TimesheetLineActualData" Role="TimesheetLineActualData" Multiplicity="*" />
  <End Type="ReportingData.Resource" Role="LastChangedByResource" Multiplicity="0..1" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**TimesheetLineActualData_LastChangedByResource** <br/> |Identifies the two entity types that form the **TimesheetLineActualData_LastChangedByResource** association.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **TimesheetLineActualData_LastChangedByResource** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the TimesheetLineActualData_LastChangedByResource association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**TimesheetLineActualData** <br/> |[EntityType element: TimesheetLineActualData](entitytype-timesheetlineactualdata-projectdata-service.md) <br/> |**\*** <br/> |The collection of actual data for timesheet lines, in the reporting tables.  <br/> |
|**LastChangedByResource** <br/> |[EntityType element: Resource](entitytype-resource-projectdata-service.md) <br/> |**0..1** <br/> |The resource object that is referenced in the **TimesheetLineActualData_LastChangedByResource** association.  <br/> |
   
## Remarks

The **LastChangedByResource** navigation property in the **TimesheetLineActualData** entity uses the **TimesheetLineActualData_LastChangedByResource** association to query for a resource that is associated with a collection of timesheet line actual data. 
  
## See also

#### Reference

[EntityType element: Resource](entitytype-resource-projectdata-service.md)
  
[EntityType element: TimesheetLineActualData](entitytype-timesheetlineactualdata-projectdata-service.md)

