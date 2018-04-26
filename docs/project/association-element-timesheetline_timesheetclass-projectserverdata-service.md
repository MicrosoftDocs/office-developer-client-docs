---
title: "Association element TimesheetLine_TimesheetClass (ProjectServerData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: e8d11cc8-ab75-42e6-b898-1c7ea54272cd
description: "The TimesheetLine_TimesheetClass association relates a timesheet line to a timesheet class."
---

# Association element: TimesheetLine_TimesheetClass (ProjectServerData service)

The **TimesheetLine_TimesheetClass** association relates a timesheet line to a timesheet class. 
  
## Definition

```XML
<Association Name="TimesheetLine_TimesheetClass">
  <End Type="ReportingData.TimesheetLine" Role="TimesheetLine" Multiplicity="*" />
  <End Type="ReportingData.TimesheetClass" Role="TimesheetClass" Multiplicity="0..1" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**TimesheetLine_TimesheetClass** <br/> |Identifies the two entity types that form the **TimesheetLine_TimesheetClass** association.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **TimesheetLine_TimesheetClass** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the TimesheetLine_TimesheetClass association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**TimesheetLine** <br/> |[EntityType element: TimesheetLine](entitytype-timesheetline-projectdata-service.md) <br/> |**\*** <br/> |The collection of timesheet lines in the reporting tables.  <br/> |
|**TimesheetClass** <br/> |[EntityType element: TimesheetClass](entitytype-timesheetclass-projectdata-service.md) <br/> |**0..1** <br/> |The timesheet class object that is referenced in the **TimesheetLine_TimesheetClass** association.  <br/> |
   
## Remarks

The **TimesheetClass** navigation property in the **TimesheetLine** entity uses the **TimesheetLine_TimesheetClass** association to query for a timesheet class that is associated with a collection of timesheet lines. 
  
## See also

#### Reference

[EntityType element: TimesheetClass](entitytype-timesheetclass-projectdata-service.md)
  
[EntityType element: TimesheetLine](entitytype-timesheetline-projectdata-service.md)

