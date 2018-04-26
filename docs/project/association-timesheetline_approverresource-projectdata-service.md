---
title: "Association TimesheetLine_ApproverResource (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 2f542dfe-53b4-478c-8d91-73281b8bc59c
description: "The TimesheetLine_ApproverResource association relates an approver resource to its timesheet line."
---

# Association: TimesheetLine_ApproverResource (ProjectData service)

The **TimesheetLine_ApproverResource** association relates an approver resource to its timesheet line. 
  
## Definition

```XML
<Association Name="TimesheetLine_ApproverResource">
  <End Type="ReportingData.TimesheetLine" Role="TimesheetLine" Multiplicity="*" />
  <End Type="ReportingData.Resource" Role="ApproverResource" Multiplicity="0..1" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**TimesheetLine_ApproverResource** <br/> |Identifies the two entity types that form the **TimesheetLine_ApproverResource** association.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **TimesheetLine_ApproverResource** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the TimesheetLine_ApproverResource association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**TimesheetLine** <br/> |[EntityType element: TimesheetLine](entitytype-timesheetline-projectdata-service.md) <br/> |**\*** <br/> |The collection of timesheet lines in the reporting tables.  <br/> |
|**ApproverResource** <br/> |[EntityType element: Resource](entitytype-resource-projectdata-service.md) <br/> |**0..1** <br/> |The approver resource object that is referenced in the **TimesheetLine_ApproverResource** association.  <br/> |
   
## Remarks

The **ApproverResource** navigation property in the **TimesheetLine** entity uses the **TimesheetLine_ApproverResource** association to query for an approver resource that is associated with a collection of timesheet lines. 
  
## See also

#### Reference

[EntityType element: TimesheetLine](entitytype-timesheetline-projectdata-service.md)
  
[EntityType element: Resource](entitytype-resource-projectdata-service.md)

