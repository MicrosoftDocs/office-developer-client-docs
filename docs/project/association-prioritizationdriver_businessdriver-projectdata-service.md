---
title: "Association PrioritizationDriver_BusinessDriver (ProjectData service)"

 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
ms.prod: null
localization_priority: Normal
ms.assetid: 34ef04e3-0ee8-48ce-9308-c3e5319447a1
description: "The PrioritizationDriver_BusinessDriver association relates prioritization drivers to a business driver."
---

# Association: PrioritizationDriver_BusinessDriver (ProjectData service)

The **PrioritizationDriver_BusinessDriver** association relates prioritization drivers to a business driver. 
  
## Definition

```XML
<Association Name="PrioritizationDriver_BusinessDriver">
  <End Type="ReportingData.PrioritizationDriver" Role="PrioritizationDriver" Multiplicity="*" />
  <End Type="ReportingData.BusinessDriver" Role="BusinessDriver" Multiplicity="0..1" />
</Association>
```

## Attributes

|**Attribute**|**Value**|**Description**|
|:-----|:-----|:-----|
|**Name** <br/> |**PrioritizationDriver_BusinessDriver** <br/> |Identifies the two entity types that form the **PrioritizationDriver_BusinessDriver** association.  <br/> |
   
## Parent element

|**Element**|**Description**|
|:-----|:-----|
|[Schema element: ReportingData](schema-reportingdata-projectdata-service.md) <br/> |The schema for the reporting data in the **ProjectData** service.  <br/> |
   
## Child elements

The **PrioritizationDriver_BusinessDriver** association element contains two **End** elements that represent opposite ends of the association. The **Role** attribute is a lookup key that enables a navigational property to specify the direction in the association. The **Multiplicity** attribute refers to the entity type. Multiplicity indicates the number of entities that can be related at each end of the association: zero or one ( **0..1**), or many ( **\***). The Microsoft .NET implementation of OData uses **0..1** when the navigational property points to a single entity, rather than to an entity set. 
  
**Attributes of the End elements for the PrioritizationDriver_BusinessDriver association**

|**Role**|**Type**|**Multiplicity**|**Description**|
|:-----|:-----|:-----|:-----|
|**PrioritizationDriver** <br/> |[EntityType element: PrioritizationDriver](entitytype-prioritizationdriver-projectdata-service.md) <br/> |**\*** <br/> |The collection of prioritization drivers in the reporting tables.  <br/> |
|**BusinessDriver** <br/> |[EntityType element: BusinessDriver](entitytype-businessdriver-projectdata-service.md) <br/> |**0..1** <br/> |The business driver object that is referenced in the **PrioritizationDriver_BusinessDriver** association.  <br/> |
   
## Remarks

The **BusinessDriver** navigation property in the **PrioritizationDriver** entity uses the **PrioritizationDriver_BusinessDriver** association to query for a business driver that is associated with a collection of prioritization drivers. 
  
## See also

#### Reference

[EntityType element: PrioritizationDriver](entitytype-prioritizationdriver-projectdata-service.md)
  
[EntityType element: BusinessDriver](entitytype-businessdriver-projectdata-service.md)

